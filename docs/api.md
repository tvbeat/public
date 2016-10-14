# TVBeat API Documentation

The TVBeat API differentiates between three types of queries:

- the "dimensions" query, which is used to fetch a list of currently available
  dimensions for other types of queries;
- the "dimensions search" query, which is used to fetch a list of possible
  values for a specific dimension; and
- the "breakdown" query, which is used to fetch metrics for a specific time span
  broken down by a certain dimension.

Each request needs to be properly signed using the algorithm defined in the
"Authenticating Your Request" section below.

## Terminology

A "dataset" determines a source of data for the query. You will be assigned one
or multiple datasets you're able to access when opening an account.

A "dimension" is a data attribute.

A "metric" is a parameter or measure of quantitative assessment used for
measurement, comparison or to track performance.

## Authenticating Your Request

TVBeat uses HMAC-SHA256 to ensure the integrity and authenticity of incoming API
queries. Each user is assigned two pieces of information: an "access key ID",
and a "secret" which are used to generate a key used to sign the HTTP request
transporting the query.

TVBeat's API uses a signing scheme very similar to the one used by Amazon Web
Services, and much of
[their documentation](https://docs.aws.amazon.com/general/latest/gr/signature-version-4.html)
on request signing is applicable here as well. You can refer to AWS's
documentation for more in-depth information on the signing process if needed.

The following chapters describe the specific steps required to sign the request,
followed by a complete example written in Python.

### TVBeat-specific Headers

With each request to the API, you'll need to send a single additional HTTP
header called `x-tvbeat-date`.

The value of this header should be set to the integer UNIX timestamp of the time
when the request was performed.

### Creating a Canonical Request

A "canonical request" is a string containing normalized concatenated information
about the request. It is defined as follows:

    canonical_request = HTTP_verb + "\n"
                      + canonical_uri + "\n"
                      + canonical_headers + "\n"
                      + signed_headers + "\n"
                      + payload_hash

The *HTTP\_verb* is either "GET" or "POST", depending on the type of request.

The *canonical\_uri* is the resource identifier without the protocol, hostname,
and query string information. E.g. if the destination of the request is
`http://api.tvbeat.com/dataset/breakdown?1`, the *canonical_uri* would be
`/dataset/breakdown`.

The *canonical\_querystring* property is equivalent to the (optional) query
string from the URI. It should be left blank if there are no query string
parameters passed to the query.

The *canonical\_headers* is a concatenated string of header names and values,
trimmed so there are no preceding or trailing spaces, lowercased, and listed in
ASCII order, *with a trailing newline at the end of the string*. TVBeat's API
requires the following headers in this list:

- host; and
- x-tvbeat-date.

If you are including any other HTTP headers with the request, list them here as
well, making sure to respect the sorting requirements.

The *signed\_headers* property is a colon-separated list of names of headers
included in the *canonical\_headers* list. E.g. if you've included the `host`
and `x-tvbeat-date` headers, the *signed\_headers* string would look like
`host;x-tvbeat-date`.

The *payload\_hash* is simply the SHA256-hashed body of the HTTP request. If the
HTTP request's body is empty, the SHA256 hash of an empty string should be used.

### Creating the String to Sign

This string contains the meta-information about the request, as well as the
canonical request generated in the previous step. It is defined as follows:

    string_to_sign = algorithm + "\n"
                   + service + "\n"
                   + canonical_request_hash

Where:

- *algorithm* should always be set to the string `TVBEAT-HMAC-SHA256`;
- *service* should always be the string `ae`;
- *canonical\_request\_hash* should be the SHA256 hash of the canonical
  request string generated in the previous step.

### Calculating the Signature

To calculate the signature, the so-called "signing key" needs to be derived
first. It is calculated as follows:

    key_date = HMAC("TVBEAT" + secret, timestamp)
    key = HMAC(key_date, service)

Where:

- *secret* is the secret key you've received along with your access key ID;
- *timestamp* is an integer UNIX timestamp equivalent to the one in the
  `x-tvbeat-date` header;
- *service* should always be the string `ae`;
- *HMAC* is a function that calculates a hash-based message authentication
  code using the SHA256 hashing algorithm given a key (the first argument) and
  some data (the second argument). The exact implementation of this function is
  outside of the scope of this guide, and you're strongly encouraged to use an
  implementation from a trusted and tested source like your programming
  language's standard library.

Once the key is derived, the signature is defined as follows:

    signature = hex(HMAC(derived_key, string_to_sign))

Where:

- *hex* calculates a hexadecimal digest of the binary result of the *HMAC*
  function;
- *derived\_key* is the result of the key derivation procedure outlined above;
- *string\_to\_sign* is the result of the process outlined in the previous
  chapter.

### Signing the Request

The final step is to add the signature to the HTTP request. This is done by
setting the "Authorization" HTTP header of the request to the following:

    authorization_header = "Algorithm=" + algorithm
                         + ", Credential=" + access_key
                         + ", Service=" + service
                         + ", SignedHeaders=" + signed_headers
                         + ", Signature=" + signature

Where:

- *algorithm* is the string `TVBEAT-HMAC-SHA256`;
- *access\_key* is the access key ID assigned to you along with your secret;
- *service* is the string `ae`;
- *signed\_headers* is the list of header names generated in one of the previous
  chapters;
- *signature* is the result of the process outlined in the previous chapter.

### Example - Building a Request in Python

    #!/sbin/env python2
    import sys, os, base64, datetime, hashlib, hmac, time
    # this is the 3rd party "requests" library
    # (`pip install requests`)
    import requests

    access_key = '1234'
    secret_key = '03d49bbeff5b836dca09a63e9dd07b1c351682ee72ba30f375c597d6e6217289'

    uts = str(int(time.time()))

    method = 'POST'
    service = 'ae'
    host = 'api.tvbeat.com'
    dataset = 'sample'
    uri = '/' + dataset + '/dimension_search'
    endpoint = 'http://' + host + uri

    request_parameters = '''
        {
          "dimension_name": "content.id",
          "search_string": "test",
          "start": 1467334800,
          "stop": 1471914000
        }
    '''

    # Key derivation functions. See:
    # http://docs.aws.amazon.com/general/latest/gr/signature-v4-examples.html#signature-v4-examples-python
    def sign(key, msg):
        return hmac.new(key, msg.encode("utf-8"), hashlib.sha256).digest()

    def getSignatureKey(key, date_stamp, service):
        key_date = sign(('TVBEAT' + key).encode('utf-8'), date_stamp)
        key_service = sign(key_date, service)
        return key_service

    # Canonical Request
    canonical_uri = uri
    canonical_querystring = ''
    canonical_headers = 'host:' + host + '\n' \
                      + 'x-tvbeat-date:' + uts + '\n'
    signed_headers = 'host;x-tvbeat-date'
    payload_hash = hashlib.sha256(request_parameters).hexdigest()
    canonical_request = method + '\n' \
                      + canonical_uri + '\n' \
                      + canonical_querystring + '\n' \
                      + canonical_headers + '\n' \
                      + signed_headers + '\n' \
                      + payload_hash

    # String to Sign
    algorithm = 'TVBEAT-HMAC-SHA256'
    string_to_sign = algorithm + '\n' \
                   + service + '\n' \
                   + hashlib.sha256(canonical_request).hexdigest()

    # Signing Key
    signing_key = getSignatureKey(secret_key, uts, service)

    # Signature
    signature = hmac.new(
        signing_key, (string_to_sign).encode('utf-8'), hashlib.sha256
    ).hexdigest()

    # Adding the Authorization Header to the Request
    authorization_header = 'Algorithm=' + algorithm \
                         + ', Credential=' + access_key \
                         + ', Service=' + service \
                         + ', SignedHeaders=' + signed_headers \
                         + ', Signature=' + signature

    headers = {
        'x-tvbeat-date': uts,
        'Authorization': authorization_header
    }

    # Use Python's requests library to make the request
    r = requests.post(endpoint, data=request_parameters, headers=headers)

    print 'Response code: %d\n' % r.status_code
    print r.text

### Errors

In case you fail to properly sign your request, an HTTP 401 ("Unauthorized")
status code will be returned with an appropriate error message.

If you try to access a resource (either a dataset or a dimension) not allowed
by your access permissions, an HTTP 403 ("Forbidden") status code will be
returned with an appropriate error message.

## Rate Limiting

At the moment, every key/secret combination is limited to a single concurrent
API query.

### Errors

In case you exceed the rate limit, an HTTP 429 ("Too Many Requests") status code
will be returned with an appropriate error message.

## Endpoints

The TVBeat API root is located at [https://api.tvbeat.com](https://api.tvbeat.com).

In addition to parameters defined for each respective endpoint described in the
following chapters, each endpoint is parametrized within its URL by the dataset
it's querying. The final API URL is built by replacing the placeholder
"{dataset}" in the endpoints with the desired dataset name.

### GET /{dataset}/dimensions

#### Parameters

This endpoint accepts no parameters.

#### Example Response

    {
      "breakdown": [
        {"key": "subscriber.regions", "description": "Region", "type": "Set"},
        {"key": "content.episode", "description": "Episode", "type": "Set"},
        {"key": "content.genre", "description": "Genre", "type": "Set"},
        {"key": "device.ua", "description": "Device Type", "type": "Set"},
        {"key": "content.id", "description": "Content", "type": "HugeSet"}
      ],
      "target_audience": [],
      "filter": [
        {"key": "subscriber.regions", "description": "Region", "type": "Set"},
        {"key": "content.episode", "description": "Episode", "type": "Set"},
        {"key": "content.genre", "description": "Genre", "type": "Set"},
        {"key": "device.ua", "description": "Device Type", "type": "Set"},
        {"key": "content.id", "description": "Content", "type": "HugeSet"},
        {"key": "device.oss", "description": "Operating systems", "type": "Set"},
        {"key": "content.subgenre", "description": "Subgenre", "type": "Set"},
        {"key": "video.resolution", "description": "Video resolution", "type": "Set"},
        {"key": "content.season", "description": "Season", "type": "Set"},
        {"key": "channel.id", "description": "Channel", "type": "Set"}
      ]
    }

#### Response Description

A call to this endpoint will result in a response listing available dimensions
broken down into three categories:

- `breakdown`, which lists all dimensions you are able to use as the
  `dimension_name` parameter of the breakdown query described below;
- `filter`, which lists all dimensions you are able to use within the `filters`
  parameter of the breakdown query described below;
- `target_audience`, which lists all dimensions you are able to use within the
  `target_audience` parameter of the breakdown query. This parameter is
  currently unsupported.

Each category contains a list of objects describing each of the dimensions,
listing its `key` (the identifier of the dimension), its `description` (a
human-readable name of the dimension), and its `type`.

There are three possible types of dimensions:

- `Scalar`, a continuous numerical value;
- `Set`, a pre-defined list of a small number (< 100) of values;
- `HugeSet`, a pre-defined list of a larger number of values.

For `Set` and `HugeSet` dimensions, the available values can be fetched by
issuing a "dimensions search" query described in the next chapter.

### POST /{dataset}/dimensions\_search

#### Parameters

This endpoint expects its parameters sent within the body of the HTTP request.
The parameters are sent as a JSON document which should conform to the following
JSON Schema:

    {
      "required": ["dimension_name"],
      "$schema": "http://json-schema.org/draft-04/schema#",
      "id": "DataTypes.Query",
      "title": "DataTypes.Query",
      "type": "object",
      "definitions": {},
      "properties": {
        "limit": {
          "type": "integer"
        },
        "start": {
          "type": "integer"
        },
        "search_string": {
          "type": "string"
        },
        "stop": {
          "type": "integer"
        },
        "dimension_name": {
          "type": "string"
        }
      }
    }

Where:

- *dimension\_name* is the identifier of the dimension (the `key` within the
  structure returned by the "dimensions" query);
- *search\_string* constrains the query to results containing only this string;
- *start* and *stop* are integer UNIX timestamps which an be used to optionally
  constrain the results to only include values within a certain time span;
- *limit* is an optional parameter limiting the number of results returned.

For dimensions with the type `Set`, you are only expected to send the
`dimension_name` parameter; any other parameters sent will be ignored.

For dimensions with the type `HugeSet`, you *must* send at least the
`search_string` parameter alongside the `dimension_name` parameter, otherwise
your query will be ignored. The `search_string` parameter must be at least 2
characters long.

#### Example Response

    [
      {
        "label": "100 Greatest Love Songs",
        "value": 9860,
        "image": "",
        "channel.id": -3
      },
      {
        "label": "50 Greatest Love Songs",
        "value": 7325,
        "image": "",
        "channel.id": -3
      },
      {
        "label": "Arnie's Greatest Ever Stunts",
        "value": 44654,
        "image": "",
        "channel.id": -3
      },
      {
        "label": "Biggest! Hottest! Loudest!",
        "value": 1653,
        "image": "",
        "channel.id": -3
      },
      {
        "label": "Fantastic Four: World's Greatest Heroes",
        "value": 1376,
        "image": "",
        "channel.id": -3
      },
      {
        "label": "Geografski testament",
        "value": 2860,
        "image": "",
        "channel.id": -3
      },
      {
        "label": "Greatest Club Teams: Ajax",
        "value": 11256,
        "image": "",
        "channel.id": -3
      }
    ]

#### Response Description

The response contains a list of objects, each of which has the following
properties:

- *label*, which is the title of the item;
- *value*, which is the unique identifier of the item;
- (optional) *image*, which is the image visually describing the item;
- (optional) *channel.id*, which can be used to determine the channel to which
  the item belongs.

At the moment, the *image* and *channel.id* properties should not be used, and
may be absent from certain responses.

### POST /{dataset}/breakdown

#### Parameters

This endpoint expects its parameters sent within the body of the HTTP request.
The parameters are sent as a JSON document which should conform to the following
JSON Schema:

    {
      "required": ["dimension_name", "filters", "time_span"],
      "$schema": "http://json-schema.org/draft-04/schema#",
      "id": "DataTypes.Query",
      "title": "DataTypes.Query",
      "type": "object",
      "definitions": {
        "DataTypes.TimeSpan": {
          "required": ["from", "to"],
          "$schema": "http://json-schema.org/draft-04/schema#",
          "title": "DataTypes.TimeSpan",
          "type": "object",
          "properties": {
            "to": {
              "type": "integer"
            },
            "from": {
              "type": "integer"
            }
          }
        },
        "DataTypes.QueryOptions": {
          "required": [],
          "$schema": "http://json-schema.org/draft-04/schema#",
          "title": "DataTypes.QueryOptions",
          "type": "object",
          "properties": {
            "limit": {
              "type": "integer"
            },
            "sort_order": {
              "$ref": "#/definitions/DataTypes.SortOrder"
            },
            "sort_metric": {
              "$ref": "#/definitions/DataTypes.SortMetric"
            }
          }
        },
        "DataTypes.SortMetric": {
          "$schema": "http://json-schema.org/draft-04/schema#",
          "title": "DataTypes.SortMetric",
          "enum": [
            "UniqueReach",
            "AverageDuration",
            "ShareOnContent",
            "ReachPercent"
          ]
        },
        "DataTypes.SortOrder": {
          "$schema": "http://json-schema.org/draft-04/schema#",
          "title": "DataTypes.SortOrder",
          "enum": [
            "ASC",
            "DESC"
          ]
        },
        "DataTypes.Interval": {
          "$schema": "http://json-schema.org/draft-04/schema#",
          "title": "DataTypes.Interval",
          "enum": ["Total"]
        },
        "DataTypes.Filter": {
          "required": [
            "filter_dimension_name",
            "filter_ids"
          ],
          "$schema": "http://json-schema.org/draft-04/schema#",
          "title": "DataTypes.Filter",
          "type": "object",
          "properties": {
            "filter_dimension_name": {
              "type": "string"
            },
            "filter_ids": {
              "items": [
                {
                  "type": "integer"
                }
              ],
              "type": "array"
            }
          }
        }
      },
      "properties": {
        "query_options": {
          "$ref": "#/definitions/DataTypes.QueryOptions"
        },
        "dimension_name": {
          "type": "string"
        },
        "filters": {
          "items": [
            {
              "$ref": "#/definitions/DataTypes.Filter"
            }
          ],
          "type": "array"
        },
        "interval": {
          "$ref": "#/definitions/DataTypes.Interval"
        },
        "time_span": {
          "$ref": "#/definitions/DataTypes.TimeSpan"
        }
      }
    }

Where:

- *dimension\_name* is a unique identifier of the dimension by which the results
  will be broken down;
- *filters* is a list of objects representing the filters which can be used to
  constrain the query, in the following form:
  - *filter\_dimension\_name* is a unique identifier of the dimension by which
    the query will be filtered;
  - *filter\_ids* is a list of IDs of items from the dimension in question; these
    IDs can be fetched by issuing a "dimension search" query for the dimension
    in question;
- *time\_span* is an object representing a time constraint on the query, with
  the properties *from* and *to* representing an interval
  `[from, to>` (i.e. a semi-open interval including "from", and excluding "to");
- (optional) *interval* defines the time span within the query will be further
  broken down. Currently, only "Total" is supported, and will be assumed if you
  don't send the parameter with your query;
- (optional) *query\_options* is an object containing the following keys, all
  optional:
  - *limit*, an integer defining the number of results returned (default: 500);
  - *sort\_metric*, a string indicating the metric by which the sorting will
    take place (for a list of supported metrics, please consult the JSON Schema
    above);
  - *sort\_order*, a string of either "ASC" or "DESC", indicating ascending or
    descending sorting order, respectively.

#### Example Response

    {
      "audience": {
        "size": 291025.7074889999,
        "percent": 1,
        "universum": 291025.7074889999
      },
      "intervals": {
        "total": [
          {
            "rating": 13244.249413466,
            "ratingPercent": 0.0455088642,
            "reach": 41291,
            "share": 1,
            "averageDuration": 1468796.2731380616,
            "label": "All",
            "reachPercent": 0.1418809368,
            "avgDurAll": 208394.19114353,
            "channel.id": -2,
            "totalDuration": 60648066914.1437
          },
          {
            "rating": 678.2168712761,
            "ratingPercent": 0.0023304363,
            "share": 0.0512084037,
            "reach": 38151,
            "averageDuration": 81405.2238983885,
            "label": "Channel #1",
            "reachPercent": 0.1310915119,
            "avgDurAll": 10671.5338783767,
            "channel.id": 799,
            "totalDuration": 3105690696.9474187
          },
          {
            "rating": 619.2480491045,
            "ratingPercent": 0.0021278122,
            "share": 0.0467559942,
            "reach": 36137,
            "averageDuration": 78469.7309256262,
            "label": "Channel #2",
            "reachPercent": 0.1241711611,
            "avgDurAll": 9743.6775978512,
            "channel.id": 629,
            "totalDuration": 2835660666.4593554
          },
          {
            "rating": 368.8792483459,
            "ratingPercent": 0.0012675143,
            "share": 0.0278520312,
            "reach": 35527,
            "averageDuration": 47546.143891287,
            "label": "Channel #3",
            "reachPercent": 0.1220751263,
            "avgDurAll": 5804.20152089,
            "channel.id": 46,
            "totalDuration": 1689171854.0257516
          }
        ]
      }
    }

#### Response Description

The response has two components:

- *audience*, which lists information about the size and share of the audience
  encompassed by the results:
  - *universum*, total size of the audience,
  - *size*, the size of the audience encompassed by the filters,
  - *percent*, the ratio between the two;
- *intervals*, which lists the breakdown for every one of the intervals
  requested. Since we currently support only "Total", there will always be one
  member in this object with the key `total`.

The *intervals* key contains a list of objects, each of which represents a
single item from the dimension requested with the `dimension_name` parameter to
the query. The object contains a number of metrics which can differ from query
to query; it will always contain a key with a name equivalent to the unique
identifier of the breakdown dimension, and a `value` key which contains a
human-readable name of that item.

E.g.: if you request a `channel.id` breakdown, this object will always contain a
key called `channel.id`, and a `label` key containing the name of the channel.

In addition to containing an object per dimension item, the *intervals* key will
always contain an extra object representing a "total of totals" for the query,
i.e. a sum of all metrics from all other items. This object will always have the
`label` set to `All`, and the key equivalent to the `dimension_name` parameter
set to the value `-2`.
