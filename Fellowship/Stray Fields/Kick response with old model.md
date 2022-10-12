# Kick response with old model

[Source code: kick_response_old_btp.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/ac4f2390439c39efd7752c041b218fba655bb6ca/ps_injection/bt3btp_lhcindiv/stitched/jmad/kick_response_old_btp_model.ipynb)

```
for i in range(len(stray_df)):
    madx.input("Select, flag=error, clear = true;")
    madx.select(flag='error', pattern='^'+stray_df.loc[i].Name+'$') 
    madx.command.efcomp(dkn=[-stray_df.loc[i]["K0 (Dipole)"]*scaling_factor,
                             -stray_df.loc[i]["K1 (Quadrupole)"]*scaling_factor,
                             -stray_df.loc[i]["K2 (Sextupole)"]*scaling_factor,
                             -stray_df.loc[i]["K3 (Octupole)"]*scaling_factor
                            ])
```

![](https://codimd.web.cern.ch/uploads/upload_84dda7154aa9222d26af2f3a6753815a.png)


Added the tracking slope via pickle. I dump the slope from [kick_response_BTP_injection_loop.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/681a252eb41a109012e588b4a0ba0ed5c0006858/ps_injection/kick_response_injection_tracking/kick_response_BTP_injection_loop.ipynb) and open them up in this script.

Comment: I think both models expect the magnet to be flat and the magnet might be slightly sideways ? In any case, the change is Y-position is small.

Question: Are the beam size measurement one sigma ?
Answer: Yes because it's the sigma of the gaussian fit.