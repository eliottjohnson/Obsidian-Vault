# PS stray field initial note from Matthew

## CERN Accelerator Optics Repo (acc-models)

https://acc-models.web.cern.ch/acc-models/

## OPERA models:
https://edms.cern.ch/document/2140704/1

## Mechanical models:

## MU16

### CATIA

https://edms.cern.ch/ui/#!master/navigator/external?SMTI137:312511:SMTI137:312512

### Drawings 

* Magnet (EDMS# 223695 v. AE, PS_LM___0043 v. AE): https://edms.cern.ch/document/223695/AE
* Vacuum chamber (789944 v. AC, PS_VCBCB0001 v. AC): https://edms.cern.ch/document/789944/AC


## First studies of MU16 by Jaime (2018)

* Email 5 July 2018:

```
Dear Matthew,

I received your email when I was meeting with Anthony discussing the appropriate way of sharing the data.

I post-processed the simulations at I_MC=5386 A. I send you all the results in 3 text files (formatted as agreed with Anthony) for each case:

1.       field_PS_main_I_5386_a_line_1.table is the reference case
2.       field_PS_main_I_5386_a_line_2.table is the reference case +10mm in x
3.       field_PS_main_I_5386_a_line_3.table is the reference case -10mm in x
4.       field_PS_main_I_5386_a_line_4.table is the reference case +10mm in y
5.       field_PS_main_I_5386_a_line_5.table is the reference case -10mm in y

In my model (which is straight by the way, it does not take into account the angle between the blocks), the closed block is in the positive z direction and the open block in the negative z direction.

Please let me know if there is something that is not clear or if you need any further information.

Cheers,
Jaime.
```

* OPERA Geometry:
![](https://codimd.web.cern.ch/uploads/upload_e839decc91427034583a1fc5c979f6fc.jpg)


## OPERA vs. MADX reference

Reference frame of the OPERA model is located on theoretical trajectory: defined by a radius of 70079 mm subtending angle $\theta = 2\pi/100 = 62.8~\text{mrad}$ with a chord of length 4400 mm. The sagitta defining the offset of the OPERA reference is then $R(1-\cos(\theta/2)) = 34.5~\text{mm}$

Jaime provided Point A 310 mm upstream of the reference arc, which opens another other offset of $L\tan(\theta/2) = 9.7~\text{mm}$ from the MADX reference.

The field map extracted at an offset of 51 mm is then located roughly 51 mm + 35.4 mm + 9.7 mm = **95.2 mm** in the MADX model.

## Existing MU fringe model (found in old repo)

The model as implemented previously deflects the beam strongly back towards the inside of the ring (31 mrad = same strength as SMH16!), with quad and sextupole components (presently we align the stray on the extracted beam)

        D16STRAY: RBEND,L=2.20480,ANGLE=0.015,K1=-.047,K2=0.33;
        F16SHIM : RBEND,L=2.19624,ANGLE=0.021,K1=0.0;


* MADX position at input to D16TRAY and output to F16SHIM, KFA71 and SMH16 setting from measurement pre-LS2 (LHC = LHCINDIV)

* **Comment:** ignore F16SHIM OUT values as this does not take into account change of reference trajectory inside the main bend (output position is much closer to 3e-1!) 

| Beam type | X: D16STRAY IN | X': D16STRAY IN | X: F16SHIM OUT | X': F16SHIM OUT |
| --------  | --------       | --------        | --------    | --------    |
| LHC       | 1.078422e-01   | 3.131043e-02    | 1.714903e-01|-5.284928e-03|
| TOF       | 1.173072e-01   | 2.975372e-02    | 1.741146e-01|-6.840921e-03|
| AD        |  1.101851e-01  | 2.973021e-02    | 1.668834e-01|-6.865152e-03|
