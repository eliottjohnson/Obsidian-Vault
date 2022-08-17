# Bumper BSW57

Bumpers in SS53, 59, 61 (septum type, Fig. 12, right) and 67 to approach the beam to both magnetic septa. [Source: Beam extraction](https://indico.cern.ch/event/385590/contributions/912478/attachments/1155188/1660160/PS50_FE_SE_CT_MTE_v11.pdf)

![](https://codimd.web.cern.ch/uploads/upload_12a52038950a39150716bb60a96400ca.png)

![](https://codimd.web.cern.ch/uploads/upload_0fea318d986d7c73b3f0c95f6c1e9fc8.png)


Information on these bumpers can be found in [Alex's codiMD](https://codimd.web.cern.ch/Q_j8goubQ36gx6ybA5pUIA) where it is specified the mapping between current and integrated field for 3/4 magnets.

"All magnets apart from PE.BSW57.61 have **half the kick** due to only two out of four coils being connected."

**PE.BSW57.53 and PE.BSW57.67 (old name 206):**
[EDMS 1161510](https://edms.cern.ch/ui/file/1161510/1/1161510.pdf)

![](https://codimd.web.cern.ch/uploads/upload_fb35b3845c3d984e54db47f9ca2f086a.png)

**PE.BSW57.59:**
[EDMS 2220045](https://edms.cern.ch/ui/file/2220045/0.1/PS-SM-Note-76-11-ocr.pdf)

![](https://codimd.web.cern.ch/uploads/upload_57877ef87261c02a2a12da2785679363.jpg)


----

Data from the BPM's in the PS were taken on 14.09.21 at different currents and switching the QSE on/off.

* 460 [A]
* 488.65 [A]
* 545.94 [A]
* 848.35 [A]

57_BUMP_OFF_QSE_OFF_460_ref.txt 57_BUMP_ON_QSE_OFF_488_65.txt
57_BUMP_OFF_QSE_OFF_488_65.txt   57_BUMP_ON_QSE_OFF_542_94.txt
57_BUMP_OFF_QSE_OFF_542_94.txt   57_BUMP_ON_QSE_OFF_848_35.txt
57_BUMP_OFF_QSE_OFF_848_35.txt
57_BUMP_ON_QSE_OFF.gz
57_BUMP_OFF_QSE_OFF.gz           57_BUMP_ON_QSE_ON_460_ref.txt
57_BUMP_OFF_QSE_ON_460_ref.txt   57_BUMP_ON_QSE_ON_488_65.txt
57_BUMP_OFF_QSE_ON_488_65.txt    57_BUMP_ON_QSE_ON_542_94.txt
57_BUMP_OFF_QSE_ON_542_94.txt    57_BUMP_ON_QSE_ON_848_35.txt
57_BUMP_OFF_QSE_ON_848_35.txt    57_BUMP_ON_QSE_ON_848_35_XSE_OFF.txt
57_BUMP_OFF_QSE_ON.gz
57_BUMP_ON_QSE_ON.gz


[Link to Data](https://gitlab.cern.ch/acc-models/acc-models-tls/-/tree/EliottBranch/ps_extraction/east-fast-extraction/BSW57_Data)

----

# Bump strength calculation

Short script to simulate the beam and give an optimal current for the BSW.
[Source: fast-extraction-east-bump-strength-calculation.ipynb](https://swan005.cern.ch/user/eljohnso/notebooks/SWAN_projects/acc-models-tls/ps_extraction/east-fast-extraction/fast-extraction-east-bump-strength-calculation.ipynb)

![](https://codimd.web.cern.ch/uploads/upload_83944ebd56036c591150ae3f3ca44e0d.png)

Another [version](https://gitlab.cern.ch/acc-models/acc-models-tls/-/blob/9e0ff754cb50792dd11a4d72c694a5d0661514e3/ps_extraction/east-fast-extraction/fast-extraction-east-bump-strength-calculation.ipynb) with the bumper transfer function from Alex's codilog (that better match measurements). This suggest lower currents ~ 750 A.

![](https://codimd.web.cern.ch/uploads/upload_8f5e6fb571db33723a001b8c56bcc2e1.png)


# Bumper current comparison

Comparison between the different currents we took data from on the 14.09.21.

Linearity is expected because the source for .53 and .67 specifies that the magnet are linear up to 850 A and .59 is linear up to ~850 A according to mm paper.



[Bumpers current comparison code on Gitlab.](https://gitlab.cern.ch/acc-models/acc-models-tls/-/blob/EliottBranch/ps_extraction/east-fast-extraction/compare-currents.ipynb)

**Conclusion** : from the plot, the increase in position is linear with current up to 840 A which confirms the sources.

![](https://codimd.web.cern.ch/uploads/upload_fc3a69d9c57dd456f3446ebbeee35bc7.png)


----

# Difference between codiMD and madx settings

I find very different angles using the definition in github and the definition from your codiMD.

I'm trying to fit the MADX simulation with data I took beginning of the week with 848 [A] on BSW57. 

So I convert this current to a kick using:

```
current = 848
bump_strength = current * (300e-6) / 2 / (24*3.3356)
bump_string = 'kpebsw57 = '+str(bump_strength)+' ;'
madx.input(bump_string)
```

Then I run the simultion with the bump strength definition for the three other bumpers from github:

```
PE.BSW57.53   , KICK :=-kPEBSW57*1.06492*PE.BSW57.59->L/PE.BSW57.53->L;
PE.BSW57.59   , KICK :=+kPEBSW57; 
PE.BSW57.61   , KICK :=-kPEBSW57*1.19887*PE.BSW57.59->L/PE.BSW57.61->L;  
PE.BSW57.67   , KICK :=+kPEBSW57*1.06492*PE.BSW57.59->L/PE.BSW57.67->L;
```
This gives me these angles:
```
-0.0014413948292938577
0.0015889195347163925
-0.002190644156973258
0.0014413948292938577
```
However **if I run the simulation with the transfer function from the codilog** I match the data closer and the angles are different:

```
bsw57_53_strength = -current*318e-6/2/(24*3.3356)
bsw57_59_strength = +current*300e-6/2/(24*3.3356)
bsw57_61_strength = -current*179e-6/(24*3.3356)
bsw57_67_strength = -bsw57_53_strength

kick53_string = 'PE.BSW57.53   , KICK :='+str(bsw57_53_strength)+' ;'
kick59_string = 'PE.BSW57.59   , KICK :='+str(bsw57_59_strength)+' ;'
kick61_string = 'PE.BSW57.61   , KICK :='+str(bsw57_61_strength)+' ;'
kick67_string = 'PE.BSW57.67   , KICK :='+str(bsw57_67_strength)+' ;'
```
Angles:
```
-0.0016842547067993762
0.0015889195347163927
-0.0018961106447615622
0.0016842547067993762
```
I calculated the scaling factor and they would look like this:
```
PE.BSW57.53   , KICK :=-kPEBSW57*1.2443478260869565*PE.BSW57.59->L/PE.BSW57.53->L;
PE.BSW57.59   , KICK :=+kPEBSW57; 
PE.BSW57.61   , KICK :=-kPEBSW57*1.03768115942029*PE.BSW57.59->L/PE.BSW57.61->L;  
PE.BSW57.67   , KICK :=+kPEBSW57*1.2443478260869565*PE.BSW57.59->L/PE.BSW57.67->L;
```
Not sure why I find this discrepency...

![](https://codimd.web.cern.ch/uploads/upload_154088f39a7a6bb92028b99118f1f717.png)


----

# Varying the strength of the kicks

I checked the transfer function from the sources for .53 .59 .67 that agree with Alex's codiMD transfer function: https://codimd.web.cern.ch/Q_j8goubQ36gx6ybA5pUIA

For .61, Alex uses I_BSW57 * 179E-6 / BRHO whereas if you calculate with Jan length and field you get I_BSW57 * 166E-6 / BRHO. This only gives a slight difference.

![](https://codimd.web.cern.ch/uploads/upload_fdef1e6e9d466e109e2ca59968223647.png)

Here I tried to match the .61 strength but it seems the phase is delayed/advanced by pi/2

![](https://codimd.web.cern.ch/uploads/upload_5925cf7cc6ffffa52476b822b50a6196.png)


----


I'll use the bump strength from Alex's codiMD (not the ones from MADX) as they match more closely the simulation and add SMH61 as a kicker and run this command:

```
madx.input('PE.SMH61 , KICK := kPESMH61')
```
The nominal value from the [codiMD](https://codimd.web.cern.ch/Q_j8goubQ36gx6ybA5pUIA#BSW57) is $\int B dL =  0.247$ Tm (at I=2350 A). The kick angle $\theta= \frac{0.247}{Brho} = \frac{0.247}{24\cdot3.3356} =$ 0.00309 rad.
The fringe of the SMH61 might change the tune of the beam when it is bumped (you can add  this to the list of things to do with Oliver) 

* Varying the strength of SMH57 small values (not close to nominal) we observe that it shifts the height and the position of the bump. [Source code](https://gitlab.cern.ch/acc-models/acc-models-tls/-/blob/EliottBranch/ps_extraction/east-fast-extraction/changing_individual_bump_strength_SMH57.ipynb)

![](https://codimd.web.cern.ch/uploads/upload_36b6fff458207832996a6c6d7cc890b6.png)

* Varying the strength of SMH61 small values we observe that it changes the height of the bumps. [Source code](https://gitlab.cern.ch/acc-models/acc-models-tls/-/blob/EliottBranch/ps_extraction/east-fast-extraction/changing_individual_bump_strength_SMH61.ipynb)

![](https://codimd.web.cern.ch/uploads/upload_ebf220de54953aced732cb7448b803d6.png)



* Kick with SMH57 and SMH61

![](https://codimd.web.cern.ch/uploads/upload_6208310964a7f0fd4e34935df85527c3.png)


![](https://codimd.web.cern.ch/uploads/upload_aa0d44ca77e0dd4280878f856653946c.png)

**Conclusion:** the simulation fits closer with a small kick in the septums.
I've added a way to calculated the diff_squared between the data and the simulation which I need to minimize. [Source: changing_individual_bump_strength_both_septums.ipynb](https://gitlab.cern.ch/acc-models/acc-models-tls/-/blob/EliottBranch/ps_extraction/east-fast-extraction/changing_individual_bump_strength_both_septums.ipynb)

TODO: I need to find a way to optimize without trying values by hand. Maybe two loops. One in i where I increase smh57 strength and one in j where i increase smh61 strength.

![](https://codimd.web.cern.ch/uploads/upload_d43c7c7fc479c98baa07d911f45d8efb.png)


# Measurement to take to check effect of septa
* Check with Oliver and take data in the CCC, four sets of data.

Path: /user/cpsop/EliottFolder/21_09_21

Use **YASP** to measure the closed-orbit with beam. On the fast cycle with KFA71 turned off and with the internal dump in.

1. Bump ON, SMH57 OFF, SMH61 OFF
1. Bump ON, SMH57 ON, SMH61 OFF
1. Bump ON, SMH57 OFF, SMH61 ON
1. Bump ON, SMH57 ON, SMH61 ON

"So when you take your four sets of measurements you can also do a **tune measurement** (QH and QV) and see if you see a shift... this is just for curiosity.
In a fringe field the field is changing across the beam's envelope, this looks to the beam like a quadrupole field and you might see a shift in the tune. I'd only expect this on the SMH61, and it'll probably be quite small."

If this intuition is correct this should match the actual simulation because in the data we took SMH57 and SMH61 were impacting the beam.

----

Scaling factor 1.8 for the BSW57 curve


SMH57 was out on the 21st and intervened on on the 22nd. Couldn't get beam time for SMH57 because Federico needed a single cycle to East otherwise it interferes with his measurements.

[BPM and tune measurements](https://gitlab.cern.ch/acc-models/acc-models-tls/-/tree/EliottBranch/ps_extraction/east-fast-extraction/BSW57_Data/21_09_21):
[Logbook entry](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3371707)

| Bump | QSE | XSE | SMH57 | SMH61 | KFA71 | Current |
| ---- | --- | --- | ----- | ----- | ----- | ------- |
| OFF  | OFF | OFF | OFF   | OFF   | ON    | 828     |
| ON   | OFF | OFF | OFF   | OFF   | ON    | 828     |
| OFF  | OFF | OFF | OFF   | ON    | ON    | 828     |
| ON   | OFF | OFF | OFF   | ON    | ON    | 828     |
| OFF  | ON  | OFF | OFF   | OFF   | OFF   | 828     |
| ON   | ON  | OFF | OFF   | OFF   | OFF   | 828     |

The kicker KFA71 doesn't have an effect on the BPM.

![](https://codimd.web.cern.ch/uploads/upload_e35d2a0f2506ed473482efff267e42a6.png)

[Afternoon data](https://gitlab.cern.ch/acc-models/acc-models-tls/-/tree/EliottBranch/ps_extraction/east-fast-extraction/BSW57_Data/21_09_21_afternoon)

Plot of the effect of SMH61 On/Off and tune measurement. [Source code](https://gitlab.cern.ch/acc-models/acc-models-tls/-/blob/EliottBranch/ps_extraction/east-fast-extraction/compare-SMH61.ipynb)
There is only half a mm difference between the two curves and the tune doesn't change significantly either.

**Conclusion:** the stray of SMH61 doesn't have a big effect on the position. Contradictory with the conclusion of the simulation where adding a kick in the septums got is closer to data.

![](https://codimd.web.cern.ch/uploads/upload_0fdffc05f6acea51ead91bcc3f3b3457.png)

