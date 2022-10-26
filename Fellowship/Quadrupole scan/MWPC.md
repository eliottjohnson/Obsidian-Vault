
### In the CCC open with CESAR application

Control -> CESAR T8 -> Analog Wire Chambers Profile

Horizontal: XBZT8.ZT8.BXMWPC103:PROFILE
Vertical: XBZT8.ZT8.BXMWPC104:PROFILE

[Timber: MWPC](https://timber.cern.ch/query?tab=Variables)
![|1025](https://codimd.web.cern.ch/uploads/upload_d4a65fbcd544f8f4eec3269fcfcda36f.png)

### Simple SWAN python script for NXCALS
![[Pasted image 20220929171954.png]]

``` python
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
# source the nxcals python libs
from nxcals.api.extraction.data.builders import *
from scipy.optimize import curve_fit
from datetime import datetime

# build the query and load data into spark dataframe UTC Time
start = "2022-07-13 12:59:30.000"
end = "2022-07-13 13:10:30.000"
df = DevicePropertyDataQuery.builder(spark).system("CMW").startTime(start).endTime(end).entity().parameter("BXMWPC_2080/Acquisition").build().toPandas()
df_qfn01 = DevicePropertyDataQuery.builder(spark).system("CMW").startTime(start).endTime(end).entity().parameter("RPAEK.251.F61.RQNCL007/MEAS.PULSE").build().toPandas()
df_qdn02 = DevicePropertyDataQuery.builder(spark).system("CMW").startTime(start).endTime(end).entity().parameter("RPAEK.251.F61.RQNEL014/MEAS.PULSE").build().toPandas()
df_qfn03 = DevicePropertyDataQuery.builder(spark).system("CMW").startTime(start).endTime(end).entity().parameter("RPAEK.251.F61.RQNEF021/MEAS.PULSE").build().toPandas()
```

The array has two profiles. First half is with low gain, the other with the high gain.

![](https://codimd.web.cern.ch/uploads/upload_da0cb498e0777a4344ae45977a305f35.png)

``` python
sc.stop()
spark.stop()
```


Change gain on SEC70 channel 8