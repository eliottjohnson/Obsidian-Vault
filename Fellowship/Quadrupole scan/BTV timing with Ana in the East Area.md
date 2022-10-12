# BTV timing with Ana in the East Area

Ana changed the **start timing** of the BTVs in EAST. **Before** it started at PE2X-**W**20 which is a **W**arning 20 ms before slow extraction (PE2X at 1030ms). Now it starts at **PE2X.F900-CT** which is a **F**orwarning 900 ms before extraction.

You can see which is the start event in LTIM cfv-157-btv2.LTIM and PE2X.SACQ-EMTV2/**LoadEvent**

![](https://codimd.web.cern.ch/uploads/upload_3c506987826dcb89bd6871c7d9f22b9b.png)


**Two crates** of BTV:
* cfv-157-btv1 that has PR57, F62, F61, F61D
* cfv-157-btv2 that has all T8

![](https://codimd.web.cern.ch/uploads/upload_14b23e2c591356b1c1297c53d69b7f4e.png)


### **Three parameters** you can play with:

![](https://codimd.web.cern.ch/uploads/upload_48d73ceded3a6f1ee75503202304b1bb.png)


* PE2X.SACQ-EMTV2: **S**tart **ACQ**uisition

You can change the **delay** of the start knowing that the first event is lost. Here we start at -900ms from 1030ms + **720 ms** delay = 850 ms.
![](https://codimd.web.cern.ch/uploads/upload_256e4978cb4b8ccc1be1486ecb1e7ef7.png)

First acquisition is at 850 + 100 ms = **950 ms** because first event is lost. Then every 100 ms

![](https://codimd.web.cern.ch/uploads/upload_24a66e49a19f541a591d17a1632d7b02.png)

* PE2X.ACQ-EMTV2
**Delay between acquisition**. Is the time between each software acquisition. If you set this to zero and look at the acqTimeInCycle you can compute the time it took to make the acquisition.

![](https://codimd.web.cern.ch/uploads/upload_781f6d42baa8add239b606356e355959.png)

* PE2X.EACQ-EMTV2 - **E**nd of **ACQ**uisition
The end of acquisition starts at PX.ELFT-CT which is the end (**E**) of flat top (**FT**) + 200 ms
![](https://codimd.web.cern.ch/uploads/upload_c861ea51b7c59898351d9e5f208fdc2f.png)

![](https://codimd.web.cern.ch/uploads/upload_7ba1b8c70b554ad8fd83687549630b9f.png)

I think it's set so that we are never limited by the end of acquisition and we always have our 7 acquisitions. This is mainly to make sure that you stop in any case before the start of the next cycle (as this one is 2400 ms).


### BTV jitter

The BTV are asynchronous leading to a **20 ms jitter**. This is the time between each acquired frame. With the delay we put, we should always have an empty frame at the beginning (good for removing background noise). To test with beam.

![](https://codimd.web.cern.ch/uploads/upload_5bcb6ed69571992d1b65df4a06c88a4b.png)

Remarks:
* There is a **20 ms jitter** between each frame from the BTVs and then an additional ~70-100 ms computation time from software.

* The computation time can be **reduced** by changing the window size which leads to less data needed to be digitalized and transfered.

* The acquisition is based on **PE2X** meaning that it is **NOT** linked to the **fast** extraction, only to the **slow** one. You could changed the delay of acquisition if you are doing fast or slow extraction.

* Possibility to install a hardware trigger to remove the jitter, as it's done in other lines, but currently not installed in East.

* Software trigger stack, so if you put 0 delay, it will acquire as fast as possible once is has completed the first acquisition.

### BTV acquisition time

Full spill should be less than 400 ms but depends on settings

Looking at **acqTimeInCycle**:

* delay to 100 ms -> 951.0, 1051.0, 1151.0, 1251.0, 1351.0, 1451.0, 1551.0
* delay to 90 ms -> 941.0, 1031.0, 1121.0, 1211.0, 1301.0, 1391.0, 1481.0

941.0, 1031.0, 1121.0, 1211.0, 1301.0, 1391.0, 1481.0
941.0, 1031.0, 1121.0, 1211.0, 1301.0, 1391.0, 1481.0
941.0, 1031.0, 1121.0, 1211.0, 1301.0, 1391.0, 1481.0
941.0, 1031.0, 1121.0, 1211.0, 1301.0, 1391.0, 1481.0
941.0, 1031.0, 1121.0, 1211.0, 1301.0, 1391.0, 1481.0
941.0, 1031.0, 1121.0, 1211.0, 1301.0, 1391.0, 1481.0
941.0, 1031.0, 1121.0, 1211.0, 1301.0, 1391.0, 1481.0

**90 ms** seems to be the fastest acquisition at full resolution.

* delay to 80 ms -> 931.0, 1011.0, 1091.0, 1171.0, 1251.0, 1331.0, 1491.0

931.0, 1011.0, 1091.0, 1171.0, 1251.0, 1331.0, **1491.0**
931.0, 1011.0, 1091.0, 1171.0, 1251.0, 1331.0, **1491.0**
931.0, 1011.0, 1091.0, 1171.0, 1251.0, 1331.0, **1491.0**
931.0, 1011.0, 1091.0, 1171.0, 1251.0, 1331.0, **1491.0**
931.0, 1011.0, 1091.0, 1171.0, 1251.0, 1331.0, 1411.0
931.0, 1011.0, 1091.0, 1171.0, 1251.0, 1331.0, 1411.0
931.0, 1011.0, 1091.0, 1171.0, 1251.0, 1331.0, **1491.0**

* delay to 70 ms -> 921.0, 991.0, 1061.0, 1131.0, 1201.0, 1341.0, 1481.0

921.0, 991.0, 1061.0, 1131.0, 1201.0, 1271.0, **1481.0**
921.0, 991.0, 1061.0, 1131.0, 1201.0, 1271.0, **1341.0**
921.0, 991.0, 1061.0, 1131.0, 1201.0, **1341.0, 1481.0**
921.0, 991.0, 1061.0, 1131.0, 1201.0, 1271.0, **1411.0**
921.0, 991.0, 1061.0, 1131.0, 1201.0, 1271.0, **1411.0**
921.0, 991.0, 1061.0, 1131.0, 1201.0, **1341.0, 1481.0**
921.0, 991.0, 1061.0, 1131.0, 1201.0, **1341.0, 1481.0**

* delay to 60 ms

First 4 shots are ok but then skips a 2*60ms 

911.0, 971.0, 1031.0, 1091.0, **1211.0, 1331.0, 1511.0**
911.0, 971.0, 1031.0, 1091.0, **1211.0, 1331.0, 1511.0**
911.0, 971.0, 1031.0, 1091.0, **1211.0, 1331.0, 1511.0**
911.0, 971.0, 1031.0, 1091.0, **1211.0, 1331.0, 1451.0**
911.0, 971.0, 1031.0, 1091.0, **1211.0**, 1271.0, **1391.0**
911.0, 971.0, 1031.0, 1091.0, **1211.0, 1331.0, 1511.0**
911.0, 971.0, 1031.0, 1091.0, **1211.0, 1331.0, 1511.0**

Value under 50 ms don't update but if you GET you still get data.

* delay to 50 ms -> 901.0, 951.0, 1001.0, 1151.0, 1251.0, 1351.0, 1451.0
* delay to 40 ms -> 891.0, 931.0, 1051.0, 1131.0, 1251.0, 1371.0, 1571.0
* delay to 30 ms -> 881.0, 911.0, 1031.0, 1151.0, 1241.0, 1361.0, 1481.0
* delay to 0 ms -> 850.0
![](https://codimd.web.cern.ch/uploads/upload_842094a364c06297753dc56b292d3b13.png)

#### Increasing the acquisition speed

Reducing the Size Y to half (40 mm instead of 90) of the data flow allows the acquisition to be set to 20 ms (time between each BTV frame) but there is still a **bottleneck**.

|||
:-:|:-:
![](https://codimd.web.cern.ch/uploads/upload_7a7d3eb7f12f27f7f76e3fbb6a127bce.png)  |  ![](https://codimd.web.cern.ch/uploads/upload_48e94d178abd11c15dfde7b27fced5de.png)

871.0, 891.0, **951.0, 1011.0, 1071.0, 1131.0, 1211.0**
871.0, 891.0, **951.0, 1011.0, 1091.0, 1151.0, 1211.0**
871.0, 891.0, **951.0, 1011.0, 1071.0, 1131.0, 1211.0**
871.0, 891.0, **951.0, 1011.0, 1071.0, 1131.0, 1191.0**

![](https://codimd.web.cern.ch/uploads/upload_5620bfb7853d00a2f49e5b94dca0bb4f.png)

Setting the Window Size Y to the minimum value: 5.49 mm:
871.0, 891.0, 911.0, **951.0, 991.0, 1031.0, 1071.0**
871.0, 891.0, 911.0, **951.0**, 971.0, **1031.0, 1071.0**
871.0, 891.0, 911.0, **951.0, 991.0, 1031.0, 1071.0**
871.0, 891.0, 911.0, **951.0**, 971.0, **1031.0**, 1051.0


**Conclusion**: you can get faster acquisition by lowering the resolution but you still get inconsistant timing. Might still be useful if you save the acquisition time in cycle.