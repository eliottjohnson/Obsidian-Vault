# PYJAPC simple tutorial

The simplest script is to grab a parameter in the East Area

![](https://codimd.web.cern.ch/uploads/upload_7e7d5cf2392aa472e14e7febb3dc5f5c.png)


``` python
import numpy as np
import pyjapc

japc = pyjapc.PyJapc(noSet=True)
japc.setSelector("CPS.USER.EAST3")
print(japc.getParam("F61.QFN01/MEAS.PULSE#VALUE"))
```

Outputs: ``` 619.9862060546875 ```

You can set a value (simulated because notSet=True):

``` python
japc.setParam("F61.QFN01/REF.PULSE.AMPLITUDE#VALUE",600) 
```

Subscription to a parameter. You need to run in interactive mode otherwise the terminal closes:

```
python -i script_name.py
```

``` python
def myCallback(parameterName, newValue):
	print(f"New value for {parameterName} is: {newValue}")

japc.subscribeParam("F61.QFN01/MEAS.PULSE#VALUE", myCallback)
japc.startSubscriptions()
```

![](https://codimd.web.cern.ch/uploads/upload_ebad2911833be0a5277d0f019db9d932.png)

Setting the BTV number of acquisition

```
japc.setParam("F61D.BTV010/MultiplexedSetting#reqUserImageSelection", [True,True,True,True,True,True,True])
```

To know what settings you can play with, open in the TN ```FESA3 Navigator```
Don't forget you can use regex and wildcards

![](https://codimd.web.cern.ch/uploads/upload_ab685749bf83d989a3d929a57c9a67fd.png)

Click on the device and ``` Launch ``` it.

![](https://codimd.web.cern.ch/uploads/upload_d295bd959830d301737bae3ed36b3e15.png)

Setting the the screen in of a BTV.
Some parameters require no selectors as they are independant from timing.

```
japc.setSelector("") #Screen select requires no selector
japc.setParam("F61D.BTV010/Setting#screenSelect", 'FIRST')
```

More info [wikis JAPC](https://wikis.cern.ch/display/JAPC/Basic+Actions#BasicActions-Selectors) and [pyjapc doc](https://acc-py.web.cern.ch/gitlab/scripting-tools/pyjapc/docs/stable/api_docs/pyjapc.PyJapc.setParam.html?highlight=enum)