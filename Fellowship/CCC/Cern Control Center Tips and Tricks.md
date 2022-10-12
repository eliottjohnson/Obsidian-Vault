# Cern Control Center Tips and Tricks

## How to find the calibration curve

Many elements, dipole, quadrupole have calibration curves from current in A to Testla or integrated Field. Do find them:

1) Control -> PS InCA Tools -> LSA DB Configuration ProDb
2) PS/C/PSRING
3) File -> HW Devices -> Logical HW Devices

![[Pasted image 20221012095616.png]]

## SSH into one of the CCC computer
```bash
ssh -Y eljohnso@cwx-xxx-xxx
```

## Copy data from CCC computer to TN

``` bash
ssh -Y eljohnso@cwe-513-vpl305

cp -r /user/cpsop/EliottFolder/quad-scan-east /afs/cern.ch/user/e/eljohnso
```
