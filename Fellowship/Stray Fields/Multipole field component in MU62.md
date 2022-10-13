# Multipole field component in MU62
See [[Multipole component model from injection]] for the first iteration.

Notebook to create multipole field component model in the MU62 for the East extraction.

[Source code: mfc_mu62.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/EliottBranch/ps_extraction/east-fast-extraction/mfc_mu62.ipynb)

Beam momentum 24 GeV/c

## Tracking
We track a particle through the stray fields of [[MU62]].

![[mfc_mu62.png|800]]

Settings for the starting point of tracking

```python
extraction_offset = 0.132 m
extraction_angle = 0.0139626 rad
x_offset = + extraction_offset * np.cos(subtending_angle/2)
z_offset = + extraction_offset * np.sin(subtending_angle/2)

track_end_z_m = chord/2 

ang_glob = (subtending_angle/2 + extraction_angle, 0.0)
pos_glob = (-sagitta+x_offset,  0.0, -(chord/2+z_offset))
```



## Probe the field transversely

We probe the field transversely at different s-steps along the particle trajectory inside the vacuum pipe that has a total width of 70 mm, see [[MU62#MU62 Beam pipe aperture]]

We run a loop for each point in the track we save the $B_{y}$ field perpendicularly to the track  and run a polynomial fit of third order on By as a function of $x_{\perp}$

Each field component is then the polynomial fit constant divided by $B\rho$

![[mfc_mu62_polifit.png|800]]

![[mfc_mu62_track_with_probing.png|1025]]

## Compute the s along the track

We then use Pythagoras to compute the s-length along the track (369 points)

![[mfc_mu62_4_components.png|725]]
![[mfc_mu62_track_with_probing 1.png|900]]

## Export the MFC to a file

the BTP stray element MFC model can be found here [[Comparing with old BTP model#BTP Stray element]]

The format for the .ele file is as follows:
``` python
stray1 : multipole,knl:={2.11E-07,-3.11E-06,5.25E-05,-0.001056026};
stray2 : multipole,knl:={2.78E-07,-4.03E-06,6.74E-05,-0.001303161};
stray3 : multipole,knl:={3.54E-07,-5.09E-06,8.47E-05,-0.001548501};
```

When you export the multipole component you need to multiply by the length of the multipole element i.e.:  $$\frac{L_{Total}}{l_{element}}$$

The format for the .seq file is a follows:

``` python
stray1, at = 29.93606067;
stray2, at = 29.95606067;
stray3, at = 29.97606067;
```

### Integration in MAD-X

Modify the F61D transfer line sequence to add the MFC before the Q74L quad

Length between end of MU62 and Q74 is ~ 0.45 m

![[Pasted image 20220920102038.png|425]]

## Initial conditions in the PS Ring at the last turn

I used the twiss parameters upstream of MU62 from the slow extraction twiss in the PS Ring from the code in [[East Slow Extraction Eliott]] but mainly this code: [slow_extraction_trajectory_maptrack_inital_conditions.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/EliottBranch/ps_extraction/east-fast-extraction/Check%20scripts/slow_extraction_trajectory_maptrack_inital_conditions.ipynb)
![[Pasted image 20220920170255.png|925]]
And then feed these parameter at the entrance of the transfer line

[Source code: F61D_with_stray.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/c6cbcafacca274000d2bfc501f39cf711375de90/ps_extraction/east-fast-extraction/f61d_with_stray/F61D_with_stray.ipynb)

![[east_dump_optics_with_stray 1.png|900]]

However, I don't the same initial parameter that I had measured.

You can also track using [[PTC_TRACK]]. For now just a random distribution.

![[east_dump_optics_with_stray_ptc_track.png|875]]
