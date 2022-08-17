# Injection BTP

As the beam is injected via the BTP transfer line to the PS ring, it passes through PR.BHT41 main unit magnet.

![](https://codimd.web.cern.ch/uploads/upload_37eb22ed74ed1013552f0de0abd1e67b.png)
https://gis.cern.ch/gisportal/Racks.htm?rna=[%272253098%27]

This is a main unit **T-type** magnet
https://norma-db.web.cern.ch/magnet/idcard/2407/

![](https://codimd.web.cern.ch/uploads/upload_8ea95f58488ca2d9f37ca03cbeff4af4.png)

https://edms.cern.ch/ui/#!master/navigator/document?D:100524417:100524417:subDocs

![](https://codimd.web.cern.ch/uploads/upload_399177fe768f50c06e81d7c1abf0a562.png)


Matthew took some measurements at injection by varying the current in all dipoles which affects this particular magnet:
https://gitlab.cern.ch/mfraser/ps-inj-fringe-field
![](https://codimd.web.cern.ch/uploads/upload_62d7f49d2d8aa4ff1d552ebeacdea8d0.png)


The beam is kicked by a Septum Magnet Injection - type C **PI.SMH42** after passing the main unit to "capture" the reference trajectory.
https://layout.cern.ch/elements?id=54016163&parentId=43074350&circuitId=0&version=LS2&navigator=MACHINE&tab=BASIC_ELEMENT

Some info on the septum SMH42:
https://edms.cern.ch/ui/file/1477011/3.0/PS-M-ES-0001-30-00.pdf
Integrated field strength [T.m] = 0.510
Peak current for nominal deflection [kA] = 31.2

The position of the beam is recorded at the **PI.BSGF42** SEM grid.
https://layout.cern.ch/elements?id=54972572&parentId=2194472&circuitId=0&version=LS2&navigator=MACHINE&tab=BASIC_ELEMENT

![](https://codimd.web.cern.ch/uploads/upload_5fa9d3c7269c3debaf808b2408f30fb4.png)

## Tracking simulation

I created a new folder in acc-model-eliott-fork/ps_injection/kick_response_injection_tracking

### Initial position and angle of tracking:
Now that we have the correct field map, we need to find the initial position and angle.

First iteration where I scale the fieldmap, transfer to MADX and read position on SEM Grid.

I need to find the correct injection position and angle, as well as, the septum SMH42's kick angle.

![](https://codimd.web.cern.ch/uploads/upload_29a52e4d0b210c17d4573f1ce06708ad.png)



### Current scaling factor
Now to find the relationship between current and scaling factor. We are in the linear regime at low current and momentum (533 A, 2 GeV/c)

![](https://codimd.web.cern.ch/uploads/upload_5728d6b204d0f6c67dedb664fece602c.png)

![](https://codimd.web.cern.ch/uploads/upload_89dfe1c06f520893bfa41d6ed3f4593f.png)
![](https://codimd.web.cern.ch/uploads/upload_7e38a18feae3f36a1c36e86f29434885.png)
![](https://codimd.web.cern.ch/uploads/upload_9f93be19149c9d88b5f9e9e310cdc72e.png)

![](https://codimd.web.cern.ch/uploads/upload_aa282de20c8bc39ddca4e6a797c9734c.png)
![](https://codimd.web.cern.ch/uploads/upload_74dda3d41ad38ec45590577d449bb300.png)

So, **1333 Gaus [Gs] corresponds to 533 A**

### Logical for SMH42
![](https://codimd.web.cern.ch/uploads/upload_dfb638a1d02bc890af46607ceabef7da.png)

From measurement 2021-11-11 18_51_25: SMH42 **31056.43 A**
So with a transfer function of 0.206 Tm = 12970 A => **0.493 Tm**

### Injection position and angle

https://edms.cern.ch/ui/#!master/navigator/document?D:100921999:100921999:subDocs
![](https://codimd.web.cern.ch/uploads/upload_3c1f347fad67488d74add54b48c555c5.png)

From this drawing I get that at the start of the magnet, the angle is roughly 6.5 deg and 590 mm in MADX ref frame.


![](https://codimd.web.cern.ch/uploads/upload_d0dd03aee57f70d250a235f2c7b9bb96.png)

![](https://codimd.web.cern.ch/uploads/upload_ae56f45d35943702609b0d2f1661366c.png)

![](https://codimd.web.cern.ch/uploads/upload_3c6b7060d1f849bd4cd7d0bec604aad4.png)

Pretty close with the rough numbers from drawing !

#### GEODE points position:

![](https://codimd.web.cern.ch/uploads/upload_70b736ee92ef4825c06860cab37fc4db.png)


Distance between end of SS40 and beam position in MAD-X reference frame: **0.548635119956767 m**
Angle between BTP and SS40 is : **0.1203164935414029 rad** or 6.894 deg

Seems to be worse but the position from Geode is very different from the one from the drawing. I need to double check this.

![](https://codimd.web.cern.ch/uploads/upload_e6bb97dae9d324dbfe72e1f9854cca79.png)


0.54473/cos(6.894) = 0.5486 m

![](https://codimd.web.cern.ch/uploads/upload_c9c45dd4cabfe2fb4cf507e8ea980275.png)


### Measurements from drawing

With a more accurate measurement from drawing using Adobe PDF Annotator I get very nice results using: 
```
extraction_offset = 0.587
extraction_angle = -6.2*np.pi/180
```
![](https://codimd.web.cern.ch/uploads/upload_2ac2da6f9064855e5f4ecb76e9b59d60.png)
**Remark**: This is actually **wrong** because the beginning of the magnet isn't at the border but inside...

Source code: https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/66793eee598ce2c2d0844e5056fb354754f49f92/ps_injection/kick_response_injection_tracking/kick_response_BTP_injection_loop.ipynb

Something interesting is that I ran the simulation for 30 points and there is a parabolic pattern around the linear fit for the simulation and the measurements.

![](https://codimd.web.cern.ch/uploads/upload_4c557ea5fe7852f9fae8ff1c06611f91.png)

![](https://codimd.web.cern.ch/uploads/upload_dd4caf53bbc760e0eef156727db518e6.png)

Source code: https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/5632b34ca643b666f23295bd2adf4fa670155f57/ps_injection/kick_response_injection_tracking/kick_response_BTP_injection_loop.ipynb


![](https://codimd.web.cern.ch/uploads/upload_ad0d76e0bf8f6f611e2802c6d960e2cb.png)
![](https://codimd.web.cern.ch/uploads/upload_474f61090f734a39d0048ce22a952549.png)
![](https://codimd.web.cern.ch/uploads/upload_962f34b3f793a7782506f4b71dc5e2c9.png)

Some new points with I checked using geode.


[Source code: points_faisceaux_visualizer.ipynb](https://gitlab.cern.ch/eljohnso/btp_stray_elements/-/blob/b6576745221ce7fd71ef2cf515842b7af941baf2/points_faisceaux_visualizer.ipynb)

![](https://codimd.web.cern.ch/uploads/upload_19d8963881100ee01e5de41286e204a1.png)



[Source code: kick_response_BTP_injection_loop.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/dff4e1ef5183c6b2ab9ae95e98e158ed7ce6011b/ps_injection/kick_response_injection_tracking/kick_response_BTP_injection_loop.ipynb)

![](https://codimd.web.cern.ch/uploads/upload_09430fe8573f24d98cc93c54853ef64e.png)

![](https://codimd.web.cern.ch/uploads/upload_4c9490e597e503e4e5ff4c58ee5d011b.png)

Remark: Difference might be because injection position and angles isn't perfectly aligned with the GEODE reference beam line. It might also be because the magnet model is straight.

I found the emittance of the beam with an optimiser in this note: [[Finding emittance through minimizing]]

I also did a little of beam distribution tracking in this note: [[Beam size through tracking]]

This is useful to find [[Multipole component model from injection]]