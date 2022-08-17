# Kick response attemps through tracking

PE.SMH57 - f61.btv010
Source code: https://gitlab.cern.ch/acc-models/acc-models-tls/-/blob/9d5ca6f84fb4f2484c666953b3be84df418c4337/ps_extraction/east-fast-extraction/replace_MU62_PS_ring_Drift_loop_kick_response.ipynb

![](https://codimd.web.cern.ch/uploads/upload_2f27a68ef6cb3b54385069154aaf7085.png)
![](https://codimd.web.cern.ch/uploads/upload_15a330350da97593e224dacfe8aab34d.png)

![](https://codimd.web.cern.ch/uploads/upload_f848b6cc2e12678be8c9659ac0cd6b40.png)


I wasn't using the correct quadrupole settings. Now I'm using:
Computed quad strength with values from 2021-11-12
```
madx.input("kQFN1 = 0.49189524096587295;")
madx.input("kQDN2 = -0.1736860601457675;")
madx.input("kQFN3 = 0.20264345245233242;")
madx.input("kQDN4 = -0.09035092890877705;")
madx.input("kQFN5 = 0.19835470213588094;")
madx.input("kQDN6 = -0.19835470213588094;")
madx.input("kQDN7 = -0.0715419764560099;")
madx.input("kQFN8 = 0.07846539353239797;")
```
### Simple tracking model SMH57
For this model I save the position and angle before entering MU62. I input these coordinates into the tracking model. I track. I read out the position and angle out and build a new sequence that starts at the exit of MU62 - SS63 all the way down to T8.

#### "Good" results with PE.SMH57 on T8BTV035
https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/EliottBranch/ps_extraction/east-fast-extraction/kick_response_through_tracking_t8.ipynb

![](https://codimd.web.cern.ch/uploads/upload_ec673f5206678dcd6730ddc47372900f.png)

If I plot with one sigma it looks much closer...
![](https://codimd.web.cern.ch/uploads/upload_de509a193ed25504aabe8ffd9f147d99.png)


But we can see from the measurements and the simulation that at this point, the septum has very little effect (almost flat slope).
Maybe on BTV096 it has a larger effect ? Let's check.

#### SMH57 on BTV096

![](https://codimd.web.cern.ch/uploads/upload_4e734f88d7f462cdfa52df94d71ad725.png)


I've redone the gaussian fit to have more control and check it visually.
I think that we might get better results with a field map at 24 GeV instead of 26 GeV.

I can increase the number of points in the fit using other acquisitions..

I can try to **scale up/down** the field map to see if this improves things

at **90%** magnetic-field
![](https://codimd.web.cern.ch/uploads/upload_5be22f13b86d89e5ef7a7e3ae7fd5373.png)

at **50%** magnetic-field
![](https://codimd.web.cern.ch/uploads/upload_c6c69b27fce0e94e73fb53d1d9a9cb7a.png)

at **150%** magnetic-field. It looks like increasing the field helps for this BTV, strange. We should be reducing at 90% for 24 GeV/c not increasing.

![](https://codimd.web.cern.ch/uploads/upload_f33e3915c630d8109be3bad7c1228119.png)

##### With the new field map at 24 GeV/c

![](https://codimd.web.cern.ch/uploads/upload_d859cfe91aabbab612af17f1ba43770d.png)
![](https://codimd.web.cern.ch/uploads/upload_f40be052fd35eca81db3b723315f50f3.png)

Slightly better !

#### SMH57 on BTV020
![](https://codimd.web.cern.ch/uploads/upload_818d5bcf160fe7c8c66734717caa0232.png)


#### SMH57 on F62.BTV002

![](https://codimd.web.cern.ch/uploads/upload_45291e1f62a8716e8d86a966c4e82a5f.png)

### KFA71

It seems that with KFA71 something is **inverted**... Usually I need to invert the Xx component of the BTV because of the sign convention in MADX. For KFA71 I don't need to invert Xx and I'm not sure why.
Perhaps it's because the transfer function has a minus sign ?

#### KFA71 on T8.BTV035
![](https://codimd.web.cern.ch/uploads/upload_97d89d4aac7cf71cd9979e40c721f020.png)

#### KFA71 on T8.BTV020
![](https://codimd.web.cern.ch/uploads/upload_e6aa6969d5134696f286b964f12a6611.png)


#### KFA71 on T8.BTV096
![](https://codimd.web.cern.ch/uploads/upload_a305c541a037098803ea78fac3a5ef3f.png)

Some comparison with the new field map and tune matching

![](https://codimd.web.cern.ch/uploads/upload_89af61ac0ba716c231019700a0d62311.png)
![](https://codimd.web.cern.ch/uploads/upload_5fd870a3ceef8a5e751ed9fb8121acf9.png)
![](https://codimd.web.cern.ch/uploads/upload_225f6839957cc353bdd4ad992376cc01.png)
![](https://codimd.web.cern.ch/uploads/upload_4df045cda859d64dc5219541825763b2.png)



#### KFA71 on F62.BTV002
![](https://codimd.web.cern.ch/uploads/upload_c1cd5d70e624b570847fc3eb25950451.png)


![](https://codimd.web.cern.ch/uploads/upload_dcc950f0e05712552889e65b73209d5a.png)

![](https://codimd.web.cern.ch/uploads/upload_ae59ba67216091c37aeda3970fc83da0.png)
