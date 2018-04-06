# TVbeat Dashboard Release notes

## Cycle 2
5 - 30 March, 2018

### Features / Improvements
* Audience builder
  * New UI flow of creating and selecting audience segments
  * AND/OR structure of querying audience data
* Indexing update
  * Better indexing column display
  * Metric selector
  * PDF and Excel export support
  * New Visualization page with two new charts to display indexing of different audience segments
* Import subcribers optimization - Increased the amount of subscribers users can upload
* Update query limit to 5000 - Queries now return up to max 5000 results (this will be adjusted based in the future according to performance)
* Various UI design improvements
* Old Stack option - marks a dataset that uses old stack
  * Old stack datasets revert to GET method queries for Import subscribers to be compatible
  * Old stack datasets dont support AND/OR multiple sets which will only become available after we migrate those datasets to new stack


### Bug fixes
* Fixed" Add new client account" error where the input was disabled.
* Fixed bug when Importing subscribers would not upload the exact amount of subscribers from the uploaded file
* Removed condition that didnt allow the package sub-overview picker to display
