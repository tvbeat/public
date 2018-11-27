# TVbeat Lexicon

## Basics

+ **Subscribers (SUB)**: All Subscribers of a given platform. In practice that represents all households in which one or more devices are present. By default a subscriber is considered to be inactive after there hasn't been activity on any of the subscribers' devices for 28 consecutive days.

+ **Devices (DEV)**: All devices capable of receiving content from Providers and are further subdivided in STBs (currently not available) and Other (mobile phones, tablets, smart TVs etc...)

+ **Channel persistence (Zap interval)**: Minimum time interval that a unit has to be tuned to a given channel in order for that viewing to be attributed to said channel. Channel persistence is 0 seconds.

+ **BTU** - Base Time Unit: 1 minute, all calculations are minute based

+ **SUT** - Subscribers using TV: is defined as a sum of all viewing for a given time period


## Metrics

### **Rating% (RTG%)**
Rating is calculated as a proportion of active subscribers within All subscribers. As base time unit is one minute, base unit of Subscribers rating is average minute rating, a number of Subscribers tuned in to a given minute. 

It is calculated as: 
 ```Total duration / duration of period or emission / Universe ```

### **Reach (#) - Number of users**
Is defined as a number of unique subscribers that have viewed a specified time period (0 sec) of a given channel over another, broader specified time period.

### **Reach %**
Number of users expressed as a percentage of the total universe or the target audience.

### **Share (SHR)**
Is defined as a fraction of rating of a specified timeslot/show/channel over total rating.

### **Rating (RTG)**
Rating is calculated as a proportion of active users within their relevant universe. As base time unit is one minute, base unit of rating is average minute rating, a number of users tuned to a given minute.

It is calculated as: 
 ```Total duration / duration or emission ```

### **Total duration (min.)**
Is defined as the sum of durations of all users that have watched
given content or interval.

### **Average duration (min.)**
Is defined as the average time that those that have watched the content or interval in
question spent viewing it. 
It is calculated as:
``` Total duration / Reach (#)  ```

### **Average Duration ALL**
Is defined as the average time that all subscribers have spent watching the content or interval in question.
It is calculated as:
``` Total duration / Universe (#) ```

