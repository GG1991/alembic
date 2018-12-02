---
title: Products
feature_text: 
feature_image: "https://picsum.photos/2560/600?image=873"
excerpt: "Prototypes used here"
aside: true
---

Using the [BITalino](http://bitalino.com/en/) device:

<img src="{{site.baseurl}}/images/prototype.jpeg">

We could measure electrocardiograms 

<img src="{{site.baseurl}}/images/block.png">

Also processing signals with [qrs_detector](https://github.com/kosachevds/qrs_detector) to get the heart rate measure.

<img src="{{site.baseurl}}/images/heart_rate.png">

The code to do this was written in Python.

```python
import detection
from bitalino import BITalino

macAddress = "20:16:12:22:50:10"

running_time = 120

batteryThreshold = 30
acqChannels = [0, 1, 2, 3, 4, 5]
samplingRate = 100 # with 100 works better than 1000
nSamples = 10
nBlocks=50
digitalOutput = [0,0]

device = BITalino(macAddress)

device.battery(batteryThreshold)

device.start(samplingRate, acqChannels)

start = time.time()
end = time.time()

while (end - start) < running_time:

      bit_out = device.read(nSamples)
      print(bit_out)
```
