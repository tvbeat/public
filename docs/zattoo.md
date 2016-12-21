# TVbeat Lexicon

## Basics

+ **Universe**: is defined as all subscribers of a given platform and in practice represent a household in which one or more devices are present. 
By default a subscriber is considered to be inactive after there hasn't been activity on any of the subscribers' devices for 25 consecutive days.
+ **BTU** - Base Time Unit: 1 minute, all calculations are minute based
+ **HUT** - Households using TV is the number of television homes using one or more television sets during the specified time period. If more than one device in the same HUT is consuming content at the same time, viewing of each device is divided by the number of active devices in order to get viewing of the entire HUT.
+ **Devices (DEV)** - are defined as all devices capable of receiving content from providers and are further subdivided in STBs and other (mobile phones, tablets, smart TVs, etc...)
+ **Channel persistence (Zap interval)** - is a minimum time interval that a unit has to be tuned to a given channel in order for that viewing to be attributed to said channel. Channel persistence is 5 seconds, and these seconds are counted into total viewing if the threshold is reached (ie. if viewing is longer than 5 seconds). 

## Metrics

### **Reach # - Number of subscribers**
Reach (#) is defined as a number of unique subscribers that have viewed a specified time period (5 sec) of a given content over another, broader specified time period. 

### **Reach %**
Reach (%) is number of subscribers expressed as a percentage of all subscribers. 

### **Rating (RTG)**
Rating is calculated as a proportion of active households within their
relevant universe. As base time unit is one minute, base unit of rating is average minute
rating, a number of HHs tuned to a given minute. 

It is calculated as:
``` Total duration / duration or emission / universe ```

### **Share (SHR)**
Share is audience of a particular timeslot/show/content expressed as a percent over total population (universe).

### **Average duration**
Is defined as the average times that those that have watched the content in question spent viewing it. Average duration (value in the table) is adjusted for the interval selected in the dashboard (minute, hour, day, total). To illustrate, if selected interval is one minute, than average duration value in the table represents average MINUTE duration for the selected period, same goes for all intervals. For total interval, average duration represents number of minutes viewed per device for the entire selected period.

It is calculated as:
``` Total duration / Reach ```

All minute values are presented in decimal number format and calculated like this: 72 seconds are presented as 1.2 min (72/60).

