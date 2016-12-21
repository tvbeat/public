# TVbeat Lexicon

## Basics

+ **Subscribers (SUB)**: Are defined as all Subscribers of a given platform and in practice represent a household in which one or more devices are present. If more than one device in the same SUB is consuming content at the same time, viewing of each device is divided by the number of active devices in order to get viewing of the entire SUB. SUB can watch a total of one minute of content in the span of one minute.By default a subscriber is considered to be inactive after there hasn't been activity on any of the subscribers' devices for 25 consecutive days.
+ **Devices (DEV)**: Are defined as all devices capable of receiving content from Providers and are further subdivided in STBs and Other (mobile phones, tablets, smart TVs etc...)
+ **Channel persistence (Zap interval)**:Is a minimum time interval that a unit has to be tuned to a given channel in order for that viewing to be attributed to said channel. Channel persistence is 15 seconds, and these seconds are counted into total viewing if the threshold is reached (ie. if viewing is longer than 15 seconds). 
+ **BTU** - Base Time Unit: 1 minute, all calculations are minute based
+ **SUT** - Subscribers using TV: is defined as a sum of all viewing for a given time period


## Metrics

### **Subscribers Rating (RTG)**
Subscribers Rating is calculated as a proportion of active subscribers within All subscribers. As base time unit is one minute, base unit of Subscribers rating is average minute rating, a number of Subscribers tuned in to a given minute. 

It is calculated as:
``` Total duration / duration or emission / universe ```

### **Subscibers (#) - Number of subscribers**
Is defined as a number of unique Subscribers that have viewed a specified time period (15 sec) of a given channel over another, broader specified time period.

### **Subscribers %**
Is Number of subscribers expressed as a percentage of **All Subscribers**

### **Share (SHR)**
is defined as a fraction of rating of a specified timeslot/show/channel over total rating.

### **Rating (RTG)**
Rating is calculated as a proportion of active subscribers within their relevant universe. As base time unit is one minute, base unit of rating is average minute rating, a number of subscribers tuned to a given minute.

It is calculated as: Total duration / duration or emission / universe

### **Total duration (min.)**
Is defined as the sum of durations of all subscribers that have watched
given content or interval.

### **Average duration (min.)**
Is defined as the average time that those that have watched the content or interval in
question spent viewing it. 
It is calculated as:
``` Total duration / Subscribers (#) `

### **Average Duration ALL**
Is defined as the average time that all subscribers have spent watching the content or interval in question.
It is calculated as:
``` Total duration / Universe (#) ```

