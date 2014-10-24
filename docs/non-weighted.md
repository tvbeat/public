# TVbeat Lexicon

## Basics

+ **All subscribers***: All active subscribers of a given platform, by default a subscriber is considered to be inactive after there has been activity on any of his devices
+ **BTU** - Base Time Unit: 1 minute, all calculations are minute based
+ **SUT** - Subscribers using TV: is defined as a sum of all viewing for a given time period

## Zap interval
Is a minimum time interval that a HH has to be tuned to a given channel in
order for that viewing to be attributed to said channel. Channel
persistence is 5 seconds, and these seconds are counted into total viewing
if the threshold is reached (ie. if viewing is longer than 5 seconds).

## Metrics

### **Rating (RTG)**
Subscriber Rating is calculated as a proportion of active subscribers within their
relevant universe. As base time unit is one minute, base unit of rating is average minute
rating, a number of HHs tuned to a given minute. All intervals, contetnt and ads that are shorter than one minute will inherit the rating of the minute they start in.

### **Share (SHR)**
Is defined as a fraction of rating over HUT rating.

### **Subscibers (#) and Subscribers (%)**
Is defined as a number of unique Subscribers that have viewed a specified time
period (X) of a given channel over a another, broader specified time period
(Y). X can be consecutive, but does not have to be. At the moment X cannot
be modified and is set to ONE non consecutive minute. If a subscriber is present for a duration that is longer than Zap interval but shorter than one minute only a fraction of that subscriber is counted towards Subscribers (#/%), meaning that a Subscriber has to accumulate a full minute of viewing during Y in order for it to be counted fully.

### **Total duration**
Is defined as the sum of durations of all subscribers that have watched
given content or interval.

### **Average duration**
Is defined as the average time that those that have watched the content or interval in
question spent viewing it. 

It is calculated as:
``` Total duration / Subscribers (#) ```

## Filters

some description

List of available filters: 
+ Channel
+ Content
+ Device Types
+ Modes
+ Packages
+ Regions
