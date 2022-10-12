## How Denis grabs the momentum to calculate the K1 for the quadrupoles

For East he read the momentum of the ps at extraction ej2 which is the slow extraction

1) Open LSA App suite click on Applications -> Settings Management

![](https://codimd.web.cern.ch/uploads/upload_f84a47b94236eb2c9b609cb96f5bd987.png)


-> All working set, Parameter type: type "momentum", Parameter is **PSBEAM/MOMENTUM**

2) Select MD beams

![](https://codimd.web.cern.ch/uploads/upload_8ec442c6463814c818fa6672eaf9611d.png)


The whole momentum curve is **PSBEAM/MOMENTUM**
![](https://codimd.web.cern.ch/uploads/upload_623c5a1647f766d96f7e804381681b76.png)


For East, timings are **PSBEAM/MOMENTUMej2** for slow extraction which gives you a single momentum value around 24 GeV

![](https://codimd.web.cern.ch/uploads/upload_bb7d404fc587ba3fe771ede151cac25c.png)


For the Booster the parameter is called **BEBEAM/MOMENTUM** and is around 2.8

![](https://codimd.web.cern.ch/uploads/upload_489c219c27ba0d9791297e10eb2e3cf9.png)


When you calculated K1 with Brho, the B value is the momentum so for example at injection 2.8

To see the change in current in the quadrupoles, open the working set and click on the graph on the bottom to create a **log viewer**

**PA.EXTFREQPSB/Frequency#frequency** 7237936 Hz basically changes the momentum in the PSB working set
