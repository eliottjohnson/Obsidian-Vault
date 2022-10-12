# Picoscope test

1. SLOW + SEC023 logging, 1-6E10 ppp
2. FAST + SEC023 + BCT logging, 1-6E10 ppp 
3. SLOW + Picoscope logging, 1-6E10 ppp
4. FAST + Picoscope + BCT logging, 1-6E10 ppp

Check if F61BCT logs to NXCALS with MD cycle

## Pyjapc
### Instrument
F61.BCT01/Acquisition#totalIntensityAutoCh1
F61.XSEC023-I1
F61.XSEC023-I1_Cal
F61.XSEC023-I2
F61.XSEC023-I2_Cal

Change the gain on the XSEC

cfv-157-biea3
T08.XSEC094-I -> GainSetting -> ampGain -> HIGH/MED/LOW

### BLM
F61.BLM008
F61.BLM027

## Timber
https://timber.cern.ch/query

## CCDE
F61.BCT: https://ccde.cern.ch/nxcals/device/1272436?subscriptionId=109700
F61.XSEC023-I1: https://ccde.cern.ch/nxcals/device/2088762
F61.BLM008: https://ccde.cern.ch/nxcals/device/2086247