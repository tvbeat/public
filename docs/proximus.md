# TVbeat Lexicon

## Basics

+ **Devices (DEV)**: Are defined as all devices capable of receiving content from Providers and are further subdivided in STBs and OTT devices (mobile phones, tablets, smart TVs, etc...). By default a device is considered to be inactive after there hasn't been activity on any of the subscribers' devices for 25 consecutive days.

+ **Channel persistence (Zap interval)**: Is a minimum time interval that a unit has to be tuned to a given channel in order for that viewing to be attributed to said channel. Channel persistence is currently set on Proximus side to 60 seconds, and these seconds are counted into total viewing if the threshold is reached (ie. if viewing is longer than 60 seconds).

+ **BTU** - Base Time Unit: 1 minute, all calculations are minute based

+ **SUT** - Subscribers using TV: is defined as a sum of all viewing on all devices for a given time period

## Metrics

### **Device Reach #**
Is defined as a number of unique devices that have viewed a specified time period (1 minute) of a given channel over another, broader specified time period.

### **Device Reach %**
Is number of Devices expressed as a percentage of All Devices

### **Share (SHR)**
Is defined as a fraction of rating of a specified timeslot/show/channel over total rating.

### **Rating (RTG)**
Rating is calculated as a proportion of active devices within their relevant universe. As base time unit is one minute, base unit of rating is average minute rating, a number of devices tuned to a given minute.
It is calculated as: "Total duration / Duration of period or emission"

### **Rating% (RTG%)**
Rating is calculated as a proportion of active devices within All devices. As base time unit is one minute, base unit of  rating is average minute rating, a number of devices tuned in to a given minute.
It is calculated as: Total duration / Duration of period or emission / Universe

### **Total Duration (MIN.)**
Is defined as the sum of durations of all Devices that have watched given content or interval.

### **Average Duration (MIN.)**
Is defined as the average time that those devices that have watched the content or interval in question spent viewing it. 
It is calculated as:  "Total duration / Device Reach (#)"

### **Average Duration All**
Is defined as the average time that all devices have spent watching the content or interval in question. 
It is calculated as: "Total duration / Universe (#)"
