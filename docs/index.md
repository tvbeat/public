# TVbeat Lexicon

### BASICS

+ Universe: 300.000 households
+ Base Time Unit (BTU): 1 minute, all calculations are minute based
+ Total TV: is defined as a sum of all viewing for a given time period

##### Weighting and weight distribution

Household data is weighted (RIM weighting) and expanded Subscriber data.
Weights are applied at subscriber level. Each device is asigned an internal
weight within a household, this weight is based on the amount of viewing
on the specific device. Household weight is than distributed among devices
based on this internal weight. RIM weighting is currently done on two
characteristics: region and number of devices

##### Channel persistence
Is a minimum time interval that a HH has to be tuned to a given channel in
order for that viewing to be attributed to said channel. Channel
persistence is 5 seconds, and these seconds are counted into total viewing
if the threshold is reached (ie. if viewing is longer than 5 seconds).

### Metrics

##### Rating (RTG)
Rating is calculated as a proportion of active households within their
relevant universe. As base time unit is one minute, base unit of rating is average minute
rating, a number of HHs tuned to a given minute. For spots each spot will
inherit a rating of the break it is part of, and breaks will have their on
ratings inherited from the minutes they are part of. Since our BTU is a
minute this means that breaks will get the rating of the minute (full
minute) that they are most in, and spots will inherit this rating.

##### Share (SHR)
Is defined as a fraction of rating over Total TV rating.

##### Reach (RCH)
Is defined as a number of unique HHs that have viewed a specified time
period (X) of a given channel over a another, broader specified time period
(Y). X can be consecutive, but does not have to be. At the moment X cannot
be modified and is set to ONE non consecutive minute.

##### Total duration
Is defined as the sum of durations of all households that have watched
given content

##### Average duration
Is defined as the average times that those that have watched the content in
question spent viewing it. It is calculated as `[Active Households Total
Duration / Households]`
