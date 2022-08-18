# Multipole field component in MU62
See [[Multipole component model from injection]] for the first iteration.

Notebook to create multipole field component model in the MU62 for the East extraction.

[Source code: mfc_mu62.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/EliottBranch/ps_extraction/east-fast-extraction/mfc_mu62.ipynb)

Beam momentum 24 GeV/c

## Tracking
We track a particle through the stray fields of [[MU62]].

![[mfc_mu62.png]]

Settings for the starting point of tracking

extraction_offset = 0.132 m
extraction_angle = 0.0139626 rad
x_offset = + extraction_offset * np.cos(subtending_angle/2)
z_offset = + extraction_offset * np.sin(subtending_angle/2)

track_end_z_m = chord/2 

ang_glob = (subtending_angle/2 + extraction_angle, 0.0)
pos_glob = (-sagitta+x_offset,  0.0, -(chord/2+z_offset))

## Probe the field transverly

We probe the field transversely at different s-steps along the particle trajectory inside the vaccum pipe that has a width of