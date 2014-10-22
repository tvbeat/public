# TVbeat Lexicon

## Basics

+ **Universe**: A population of multichannel households to which sample is weighted and balanced to.
   * Croatia: 750k
   * Slovenia: 691k
+ **BTU** - Base Time Unit: 1 minute, all calculations are minute based
+ **SUT** - Subscribers using TV: is defined as a sum of all viewing for a given time period

## Metrics

### **Subscribers (#)**
Rating is calculated as a proportion of active households within their
relevant universe. As base time unit is one minute, base unit of rating is average minute
rating, a number of HHs tuned to a given minute. All intervals, contetnt and ads that are shorter than one minute will inherit the rating of the minute they start in.

### **Subscribers Share (SHR)**
Is defined as a fraction of rating over HUT rating.

### **Subscribers Rating (RTG)**
Is defined as a number of unique HHs that have viewed a specified time
period (X) of a given channel over a another, broader specified time period
(Y). X can be consecutive, but does not have to be. At the moment X cannot
be modified and is set to ONE non consecutive minute. If a household is present for a duration that is longer than Zap interval but shorter than one minute only a fraction of that household si counted towards RCH, meaning that a household has to accumulate a full minute of viewing during Y in order for it to be counted fully.

### **Total duration (min.)**
Is defined as the sum of durations of all households that have watched
given content

### **Average duration**
Is defined as the average times that those that have watched the content in
question spent viewing it. 

It is calculated as:
```ruby
 Active Households Total Duration / Active Households
```

## Filters

some description

List of available filters: 
+ Channel
+ Content
+ Device Types
+ Modes
+ Packages
+ Regions

