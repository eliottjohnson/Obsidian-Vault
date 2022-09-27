# MWPC

Horizontal: XBZT8.ZT8.BXMWPC103:PROFILE
Vertical: XBZT8.ZT8.BXMWPC104:PROFILE

[Timber: MWPC](https://timber.cern.ch/query?tab=Variables)
![](https://codimd.web.cern.ch/uploads/upload_d4a65fbcd544f8f4eec3269fcfcda36f.png)

Simple SWAN python script

``` python
import matplotlib.pyplot as plt
import pandas as pd
# source the nxcals python libs
from nxcals.api.extraction.data.builders import *

# build the query and load data into spark dataframe
start = "2022-07-12 23:50:00.000"
end = "2022-07-13 00:00:00.000"
df = DevicePropertyDataQuery.builder(spark).system("CMW").startTime(start).endTime(end).entity().parameter("BXMWPC_2080/Acquisition").build()

p_df = df.toPandas()
```

The array has two profiles. First half is with low gain, the other with the high gain.

![](https://codimd.web.cern.ch/uploads/upload_da0cb498e0777a4344ae45977a305f35.png)

``` python
sc.stop()
spark.stop()
```


