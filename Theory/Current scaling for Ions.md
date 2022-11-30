# Current scaling for Ions

Otherwise you can take the currents for protons, convert to k with the non-linear magnetic curve, scale down the k by a factor 54/82 and then recompute the current which gives very close results to what Marc and Matthew found.

![|1100](https://codimd.web.cern.ch/uploads/upload_5619938e20ef9b23cde7a035f030ba02.png)

[Cernbox link: ion_scaling_east.xlsx](https://cernbox.cern.ch/index.php/s/iIHyDnR9Aeovgnr)

Do I need to change in MADX the type of particle ?

## Marc strength for Slow, Fast and ions East Area


|              |               | 2018 settings |                |                              | 2021 settings |             |         |
| ------------ | ------------- | ------------- | -------------- | ---------------------------- | ------------- | ----------- | ------- |
| old name     |               | Proton        | Pb             | Ratio                        | T8 SE         | T8 FE       | T8 ions |
| QFO01        | F61.QFN01     | 580           | 580            |                              | 620           | 550         | 620     |
|              | F61.DHZ01     | -10           | -10            |                              | 0             | 0           |         |
| QDE02        | F61.QDN02     | 210           | 138,29         | 54/82                        | 404           | 404         | 264,6   |
|              | F61.DVT01     | 70            | 46,1           | 54/82                        | 0             | 0           |         |
| QFO03        | F61.QFN03     | 388           | 255,51         | 54/82                        | 378           | 388         | 243,7   |
|              |               |               |                |                              |               |             |         |
| F61.BHZ01    | F61.BHZ01.A/B |               |                |                              | 544           | -540 (dump) |         |
|              |               |               |                |                              |               |             |         |
| QDE04        | F61.QDN04     | 335           | 220,61         | 54/82                        | 166           |             | 109,1   |
|              |               |               |                |                              |               |             |         |
|              | F61.BHZ02.A/B |               |                |                              | 562           |             |         |
|              |               |               |                |                              |               |             |         |
| F61S.BHZ01   | T8.BHZ03      | 442           | 261            | reduced 54/82 - 30           | 245           |             | 161,3   |
| F61S.BHZ02   |               | 1,5           | 0,99           | 54/82                        |               |             |         |
| F61S.QFO01   | T8.QFN05      | 358           | 235,76         | 54/82                        | 370           |             | 239,2   |
| F61S.QDE02   | T8.QDN06      | 378           | 248,93         | 54/82                        | 370           |             | 239,2   |
| F61S.GSDHZ01 | T8.DHZ02      | sweep         | modified sweep |                              | 127           |             | 83,82   |
| F61S.DVT01   | T8.DVT02      | 0             | 0              |                              | -17           |             | -11,22  |
| ZT8.BHZ01    | T8.BHZ04      | -377,6        | -235           | a bit reduced 54/82-13.66)   | 359,6         |             | 232     |
| ZT8.BHZ02    | T8.BHZ05      | -377,6        | -235           |                              | 359,6         |             | 232     |
| ZT8.GSDVT01  | T8.DVT03      | -15           | -9,75          | a bit reduced (54/82 = 9.88) | 5             |             | 3,3     |
| ZT8.GSDHZ01  |               | sweep         | same sweep     |                              | -30 ?         |             | -45     |
| ZT8.QDE01    | T8.QDN07      | 300           | 177,56         | reduced 54/82 - 30           | 310           |             | 204     |
| ZT8.QFO02    | T8.QFN08      | 229           | 160,8          | reduced 54/82 -10            | 340           |             | 223,7   |

Using the transfer function script

[Source code: quadrupole_transfer_function.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/EliottBranch/ps_extraction/east-fast-extraction/quadrupole_scan/quadrupole_transfer_function.ipynb)

I get for **slow extraction**:
quadrupole k1
```
620 Q74L :  0.4786507380149811
404 Q120C :  0.17273254187152737
378 QFL :  0.19777578293544015
166 QFS :  0.09044110316475104
370 QFL :  0.19414764578020668
370 QFL :  0.19414764578020668
310 Q200L :  0.0714888875564616
340 Q200L :  0.07834672422752528
```
dipole k 
```
544 MCB :  0.04639036343321235
562 MCB :  0.047098178033049325
245 MCB :  0.025530807457577943
359.6 MCB :  0.036617064813441326
359.6 MCB :  0.036617064813441326
```

For **Fast extraction**:
Only the first three quadrupole settings are different but they should be the same.
```
550 Q74L :  0.4324413947741286
404 Q120C :  0.17273254187152737
388 QFL :  0.20231095437948202
```

For **Ions** settings used in the CCC by Marc and Matthew around 12.11.2021
quadrupole k1
```
620 Q74L :  0.4786507380149811
266 Q120C :  0.11439304606201117
249 QFL :  0.13309086901634573
109 QFS :  0.05951523616114955
243 QFL :  0.12987508152405955
243 QFL :  0.12987508152405955
204 Q200L :  0.04707548866770596
230 Q200L :  0.053051425030978934
```
dipole k 
```
310 MCB :  0.03208472049830346
330 MCB :  0.034002979141016285
157 MCB :  0.016370765565893054
216 MCB :  0.022444564829506044
216 MCB :  0.022444564829506044
```

Script for ion scaling
[T8_ion_scaling.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/EliottBranch/ps_extraction/f61t8/T8_ion_scaling.ipynb)

Some info [here](https://gitlab.cern.ch/search?search=+PARTICLE%3Dlead&nav_source=navbar&project_id=126483&search_code=true&repository_ref=2021) on how to change beam parameter for ion: `Beam, particle=lead, pc=0.08856*A, ex=2.5E-6, ey=2.5E-6, charge=54, mass=A*0.9315, BUNCHED;`

### See also the [[Pb ion lookup table]]

## For dipoles

$Kick = \frac{I_{corrector}\cdot TF}{B\dot\rho}$


![[Pasted image 20221130094624.png]]

## For quadrupoles

![[Pasted image 20221130094636.png]]