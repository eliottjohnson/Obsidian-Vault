# PS Stray field

The [[PS stray field initial note from Matthew]] explains the existing model in the TT2 extraction and a few exchanges regarding the OPERA model.

## Field maps Gitlab Repository:
https://gitlab.cern.ch/ps-opera/ps-main-unit-type-u
https://gitlab.cern.ch/ps-opera/ps-main-unit-type-s
https://gitlab.cern.ch/ps-opera/ps-main-unit-type-r
https://gitlab.cern.ch/ps-opera/ps-main-unit-type-t

## Field map visualization
[[Field map visualization]]

### Opera model construction:
https://edms.cern.ch/ui/file/2284054/0/2-211-v0_tif_cpdf.pdf
![]![](https://codimd.web.cern.ch/uploads/upload_4c4e54e611d9ade1891b2b442eb4782d.png)


https://edms.cern.ch/ui/file/2140704/2/note_magnetic_model_jra_v_1.0_docx_cpdf.pdf

![](https://codimd.web.cern.ch/uploads/upload_5b88bbf5bae2ba175285bdb4f014e792.png)

Question to Miro:
I noticed that between the U and T type, the fields Bx, By, Bz are inverted.

Answer from Miro: 
I quickly checked – it’s due to the way they set up the models. You’ll find a similar “discrepancy” between the R and S units. In fact, in order to be able to use the same model for all configurations, they just swapped the current directions. So the **U is exactly like the T** (**same for R and S**), only the current direction has been reversed (or the **-z origin** if you like). So basically, as you have seen, exactly the same fields, just different signs, you’ll need to choose a convention I assume

This means that we do not need a copy of U and T (or R and S). Only one of them is enough to produce the T-type from the U-type you flip the signs of all the fields and the sign of z.


We can see from this plot that for a closed block, the high field is to the outside of the magnet whereas for an open block it is closer in.
![](https://codimd.web.cern.ch/uploads/upload_aa5cc1025cc407048702552f814fa832.png)

![](https://codimd.web.cern.ch/uploads/upload_a0cdddbe33a8e38d0986f94084e18215.png)

![](https://codimd.web.cern.ch/uploads/upload_e48e7be791dd9647cfe2f88345ece774.png)
https://edms.cern.ch/panoramas/viewer?fov=54.00&id=55349355&lat=-2.08&lon=28.14
![](https://codimd.web.cern.ch/uploads/upload_a0ced16a785e2a5d079277381d175801.png)


I think we have to do these flipping

```
if (MU_type == "T"):
    print ("flipping signs of B-fields")
    fieldmap.loc[:,'z'] *= -1
    fieldmap.loc[:,'Bx'] *= -1
    fieldmap.loc[:,'By'] *= -1
    fieldmap.loc[:,'Bz'] *= -1
if (MU_type == "R"):
    print ("flipping sign of B-fields and x")
    fieldmap.loc[:,'Bx'] *= -1
    fieldmap.loc[:,'By'] *= -1
    fieldmap.loc[:,'Bz'] *= -1
    fieldmap.loc[:,'x'] *= -1
    fieldmap.loc[:,'z'] *= -1
if (MU_type == "S"):
    print ("flipping sign of x and z")
    fieldmap.loc[:,'x'] *= -1
```

![](https://codimd.web.cern.ch/uploads/upload_79a52f562c87bdc50ef909f309aca8d8.png)


### Reference change from OPERA to MADX

![](https://codimd.web.cern.ch/uploads/upload_de91c540f02d5297e44bb7ed0c5442b4.png)

## TT2TT10 extraction stray field simulation
[[TT2 TT10 extraction stray field simulation]]

In this test I replace Francesco stray field implementation with a matrix that describes the stray fields. I also replace a normal MU with a custom matrix built with tracking.

## MU62
[[MU62]]

## MU63
Info on the [[MU63]] magnet.

## Magnetic measurement of septums
[[Magnetic measurement of SMH57]]
[[Magnetic measurement of SMH61]]


# Injection BTP
[[Injection BTP]]

## Transfer matrix using tracking at injection
[[Transfer matrix using tracking at injection]]

## Kick response with old model
[[Kick response with old model]]


# East Area Extraction

## Optics measurements
https://gitlab.cern.ch/mfraser/f6x-t8-optics/-/tree/eliott_branch

https://be-op-logbook.web.cern.ch/elogbook-server/GET/showEventInLogbook/3414119
https://be-op-logbook.web.cern.ch/elogbook-server/GET/showEventInLogbook/3417681


## Kick response
[[Kick response attempts through tracking]]

## Tune and chromaticity measurements
[[Tune and chromaticity measurements]]

## Three turns extraction:
[[Three turns extraction]]

## Fast extraction tracking in MU62
[[Fast extraction tracking in MU62]]

## Gradient felt at East extraction
[[Gradient felt at East extraction]]

## Distribution of particles through MU62
[[Distribution of particles through MU62]]

## Full line with matrix from tracking

Source code: https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/7ec1a316b6961dbca166ae9ceca50cdb5124a32b/ps_extraction/east-fast-extraction/full_line_with_matrix_from_tracking_center_to_strength.ipynb
![](https://codimd.web.cern.ch/uploads/upload_53fff3189179ef81cf0cc4e057d3b23b.png)

## Sign comparison with septums
[[Sign comparison with septums]]

## Excursion in MUs
[[Excursion in Main units during a slow extraction]]