# TVbeat Lexicon

## Basics

+ **All subscribers**: All active subscribers of a given platform. By default a subscriber is considered to be inactive after there hasn't been activity on any of the subscribers' devices for 35 consecutive days.
+ **BTU** - Base Time Unit: 1 minute, all calculations are minute based
+ **SUT** - Subscribers using TV: is defined as a sum of all viewing for a given time period

## Zap interval
Is a minimum time interval that a Subscriber has to be tuned in to a given channel in
order for that viewing to be attributed to the said channel. Zap
interval is 5 seconds, and these seconds are counted into total viewing
if the threshold is reached (ie. if viewing is longer than 5 seconds).

## Metrics

### **Subscribers Rating (RTG)**
Subscribers Rating is calculated as a proportion of active subscribers within All subscribers. As base time unit is one minute, base unit of Subscribers rating is average minute rating, a number of Subscribers tuned in to a given minute. 

It is calculated as:
``` Total duration / duration or emission / universe ```

### **Subscibers (#) - Number of subscribers**
Is defined as a number of unique Subscribers that have viewed a specified time period (5 sec) of a given channel over another, broader specified time period.

### **Subscribers Share**
Is Number of subscribers expressed as a percentage of **All Subscribers**

### **Total duration (min.)**
Is defined as the sum of durations of all subscribers that have watched
given content or interval.

### **Average duration (min.)**
Is defined as the average time that those that have watched the content or interval in
question spent viewing it. 

It is calculated as:
``` Total duration / Subscribers (#) ```

## Filters
The user can slice and dice the entire viewership with specific filters such as Channel, Region, Mode etc. Filtering is possible in Segmentation as well as in all Overviews. In Live we also have channel filters. 

List of available filters: 
+ Channel
+ Content
+ Device Types
+ Modes
+ Packages
+ Regions

## Compare (Segmentation)
The Compare feature enables the user to define by which filter they want to compare/display the data in the chart and table. For example, if the user chose they want to compare their data by device, they will get the results broken down by all available devices.
