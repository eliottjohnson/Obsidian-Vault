# TT2 TT10 extraction stray field simulation
1) First, we create a custom matrix using Ewa's code and running [function_create_matrix.ipynb](https://gitlab.cern.ch/ydutheil/ps-stray-tracking/-/blob/EliottBranch/function_create_stray_matrix.ipynb). The start of the tracking in the fieldmap is computed using the ejection madx script [get_initial_conditions_lhc_q20.madx](https://gitlab.cern.ch/acc-models/acc-models-tls/-/blob/2021/ps_extraction/tt2tt10_lhc_q20/stitched/get_initial_conditions_lhc_q20.madx).


![](https://codimd.web.cern.ch/uploads/upload_b5e16b398d90a632dc1c78b3b520dbd3.png)

2) Next, we extract the beam from the PS to get the initial condition at the Handover to TT2 with a modified version of the Francesco's code [compare_initial_conditions_with_tracking_matrix](https://gitlab.cern.ch/ydutheil/ps-stray-tracking/-/blob/EliottBranch/compare_initial_conditions_with_tracking_matrix.ipynb) where the d16stray and f16shim element are replaced by the stray matrix.


![](https://codimd.web.cern.ch/uploads/upload_07cbe37faafd8f37acb264b3e820a5b7.png)



Remark: the sequence definition adjusts itself according to the length of the stray matrix.

![](https://codimd.web.cern.ch/uploads/upload_af9b0d9663a844bb4463f0e0b61607e4.png)

Yann pointed out that one must be careful that MADX doesn't change the matrix by simpletifying it.

```
sympl=False
```

changes slightly the matrix

![](https://codimd.web.cern.ch/uploads/upload_b3cdf56c6b08b5012216838dbaf7827e.png)

to follow up.

### Quick test to replace the magnet BHU16's definition in Madx by a matrix from tracking in fieldmap.

[Source replace_MU_PS_ring.ipynb](https://gitlab.cern.ch/ydutheil/ps-stray-tracking/-/blob/EliottBranch/replace_MU_PS_ring.ipynb)

I want to see if replacing a magnet in the PS optics file by a matrix produces by Ewa's tracking gives close results. This would help debug more complicated scenarios.

The BHU16's model in madx is described below.

/ps_mu.seq
```
PR.BHU16: SEQUENCE, refer = CENTRE,  L = MU_L;
 PR.MP16.D:  PR_MPD,  AT = 0.0;
 PR.BHU16.D: PR_BHD,  AT = L_D/2;
 PR.MP16.J:  PR_MPJ,  AT = L_D;
 PR.DHZ17.A: PR_DHZ,  AT = L_D;
 PR.BHU16.F: PR_BHF,  AT = L_D + L_F/2;
 PR.MP16.F:  PR_MPF,  AT = MU_L;
ENDSEQUENCE;
```

And this is the replaced sequence.

/ps_mu_Eliott.seq
```
PR.BHU16: SEQUENCE, refer = ENTRY,  L = MU_L;
 MYMAINUNIT16_label: MYMAINUNIT16, AT = 0.0;
ENDSEQUENCE;
```

MYMAINUNIT16 is a matrix produced by running [function_create_stray_matrix_bending.ipynb](https://gitlab.cern.ch/ydutheil/ps-stray-tracking/-/blob/EliottBranch/function_create_stray_matrix_bending.ipynb). This outputs a my_main_unit16.ele file that has to be called before the PS sequence definition.


![](https://codimd.web.cern.ch/uploads/upload_37fc2735c5fe2d8e5396ff0843d5f754.png)


**Conclusion**: I think this quick test is very successful. Looking at the betx as a function of s, the simulation with the matrix from tracking matches closely the reference one. As a sanity check, there is also a plot with both definitions removed.

![](https://codimd.web.cern.ch/uploads/upload_d191cc0b29fea5ccbccef3f1e7841f27.png)
