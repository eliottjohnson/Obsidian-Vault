
Two devices:
* BXSCINT_1000
* BXSCINT_1001

High sampling period
* BXSCAL_1100
* BXSCAL_1101

Sampling period can be set with BXSCAL_1100/EaConfig#counterSampling and this is roughly the sampling period in microseconds multiplided by the number of devices in the crate.

The sampling period is non-uniform and you should use the time array to figure out the sampling period.
![[Pasted image 20221104114008.png]]


White Rabbit TDC, two devices:

-   BXTDC_1000 -> this maps BXSCINT_1000
-   BXTDC_1001 -> for BXSCINT_1001

#Inaki knows about these instruments

## Control

### Voltage increase

### Gas
Concerning the pressure, no, we can’t change the pressure. It’s always slightly higher than atmospheric.
However, we could try another scintillator gas. At the moment, we have N2 (100%), but I have a bottle of  Ar (96%) + N2 (4%) ready to be swapped, which should have a higher light yield. Changing the bottles would take less than 1 hour.

[Image source](https://edms.cern.ch/ui/#!master/navigator/document?D:100567405:100567405:subDocs)
![[Pasted image 20221102085152.png|750]]

## Documentation

[EDMS](https://edms.cern.ch/ui/#!master/navigator/project?P:100567331:100567331:subDocs)
[East Area TDR](https://edms.cern.ch/ui/file/2664547/1/EAR_TDRV01.ch3.5.V01_docx_cpdf.pdf)

## Used

During the [[Dedicated MD 26th October 2022]] where the spill was very low

Compared to normal proton spill

Also used during the [[RFKO MD8923 Week 44]] and the [[Slow extraction theory#TFB extraction (RFKO)]]


## BXSCAL1100

Fast acquisition

![[Pasted image 20221103104023.png|1075]]