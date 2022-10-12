# Finding emittance through minimizing
[Source code: kick_response_old_btp_model.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/cbb97e7bdd19c5092bd967b7241670103ee970ed/ps_injection/bt3btp_lhcindiv/stitched/jmad/kick_response_old_btp_model.ipynb)

I find:
``` 
exn:= 1.65e-06
eyn:= 2.90625e-07
sige:= 0.55e-03
```

Specifications from 2018
![](https://codimd.web.cern.ch/uploads/upload_8a8d37db8d33bcb39b5cf75d41a3946e.png)

![](https://codimd.web.cern.ch/uploads/upload_82c2efe71c8a14f4971eb51c766c6df9.png)

### Emittance measurement from 2021

Further discussion to discuss the emittance on the day of the MD
Found with the [Weekly logs 2021](https://wikis.cern.ch/display/PSBOP/Weekly+Logs+2021), specifically for [INDIV in november 2021](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3418117)

```
exn = 1.6e-6 [m]
eyn = 1.0e-6 [m]
sige (dp/p) = 0.46e-3
```
![](https://codimd.web.cern.ch/uploads/upload_3dd32443b2b9d512f2ec8faeb12a7f2a.png)

![](https://codimd.web.cern.ch/uploads/upload_bf31a7b56863a75b202e57c772f3009c.png)

With these settings, the beam size is closer but there still is an issue with the vertical beam size

![](https://codimd.web.cern.ch/uploads/upload_3c3f9a0da76936ae7e66770d417994c8.png)

![](https://codimd.web.cern.ch/uploads/upload_e224e474dbb16ce0b8bbaac00a26136d.png)
