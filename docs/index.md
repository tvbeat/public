# TVbeat Lexicon

### BASICS

+ Universe: A population of multichannel households per country to which sample is weighted and balanced to.
  + Croatia: 750k
  + Slovenia: 691k
+ Base Time Unit (BTU): 1 minute, all calculations are minute based
+ Households using TV (HUT): is defined as a sum of all viewing for a given time period

##### Weighting and weight distribution

Household data is weighted (RIM weighting) and expanded platforms subscriber data.
Weights are applied at subscriber level. Each device is asigned an internal
weight within a household, this weight is based on the amount of viewing
on the specific device. Household weight is than distributed among devices
based on this internal weight. RIM weighting is currently done on two
characteristics: region and number of devices

##### Zap interval
Is a minimum time interval that a HH has to be tuned to a given channel in
order for that viewing to be attributed to said channel. Channel
persistence is 5 seconds, and these seconds are counted into total viewing
if the threshold is reached (ie. if viewing is longer than 5 seconds).

### Metrics

##### Rating (RTG)
Rating is calculated as a proportion of active households within their
relevant universe. As base time unit is one minute, base unit of rating is average minute
rating, a number of HHs tuned to a given minute. All intervals that are lower than one minute will inherit the rating of the minute they start in.

##### Share (SHR)
Is defined as a fraction of rating over HUT rating.

##### Reach (RCH)
Is defined as a number of unique HHs that have viewed a specified time
period (X) of a given channel over a another, broader specified time period
(Y). X can be consecutive, but does not have to be. At the moment X cannot
be modified and is set to ONE non consecutive minute. If a household is present for a duration that is longer than Zap interval but shorter than one minute only a fraction of that household si counted towards RCH, meaning that a household has to accumulate a full minute of viewing during Y in order for it to be counted fully.

##### Total duration
Is defined as the sum of durations of all households that have watched
given content

##### Average duration
Is defined as the average times that those that have watched the content in
question spent viewing it. It is calculated as `[Active Households Total
Duration / Households]`
