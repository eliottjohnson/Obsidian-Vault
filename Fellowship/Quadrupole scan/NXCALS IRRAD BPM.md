
[Timber](https://timber.cern.ch/)
![](https://codimd.web.cern.ch/uploads/upload_af83b902fbfc3594b6055014386c16d2.png)


[ccde](https://ccde.cern.ch/nxcals/device/2126025?subscriptionId=35908922)
![](https://codimd.web.cern.ch/uploads/upload_bf6ca7357963385ecf7fe30738d446e3.png)

Voici le nom des BPMS IRRAD :
PS-LOG-BPM-IRRAD-UCAP_BPM_01
PS-LOG-BPM-IRRAD-UCAP_BPM_02
PS-LOG-BPM-IRRAD-UCAP_BPM_03
PS-LOG-BPM-IRRAD-UCAP_BPM_04

![](https://codimd.web.cern.ch/uploads/upload_792b7c7ed42deeb374a73d8df65e6a0a.png)


![](https://codimd.web.cern.ch/uploads/upload_3408f4be6947de6b244c8d93e37c57c9.png)

So you can either grab the data with pyjapc:
``` python
japc.getParam("PS-LOG-BPM-IRRAD-UCAP_BPM_01/Positions")
```

[Logbook entry where Federico explain the intensity](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3592280)

* Even if no beam, the BPM will trigger every 2 min
* The UCAP device does a different fit than the IRRAD Vistar (Irrad vistar fits only the center lines)