# PS beam energy

## Some intro about how it is defined, including the lookup tables

See [[Pb ion lookup table]]

[Source code: read_bfield_pickles.ipynb](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/read_bfield_pickles.ipynb)


![[variation_b_field_chimera 2.png|1300]]

![[average_b_field_chimera 1.png|500]]

![[hist_b_field_chimera 2.png|375]]

![[energy_scan_chimera 1.png|475]]

![[energy_scan_timestamp_chimera 1.png|475]]


## The nice colour showing which energy was used during each moment of the test

[Source code: gain_vs_xion.ipynb](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/gain_vs_xion.ipynb)
![[Pasted image 20221130110611.png|775]]

# Beam intensity

## RFKO and gain settings throughout the test

[Source code: rfko_gain_analysis](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/rfko_gain_analysis.ipynb)

![[Pasted image 20221130103506.png|950]]

![[Pasted image 20221130103511.png|350]]

## Intensity measurements on SEC and XION, including intensity vs. gain

[Source code: gain_vs_xion.ipynb](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/gain_vs_xion.ipynb)

![[Pasted image 20221130110629.png|825]]


## RFKO

Time structure

[PS logbook entry: RFKO time structure](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3657771)

![[Pasted image 20221130111711.png|375]]

# Spill time profile

## Gas scintillator, SEC, XION, etc.

[Source code: gain_vs_xion.ipynb](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/gain_vs_xion.ipynb)
![[Pasted image 20221130110602.png|400]]

[PS logbook entry: spill and rfko gain changes](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3656662)

![[Pasted image 20221130111829.png|425]]

### How does the spill shape change with gain setting ?



# Beam spatial profile

## MWPC

-   Independence of beam profile with beam intensity, impact of energy on the beam shape, “explanation” of the dips (i.e. comparison with and without Montract), etc.

![[Pasted image 20221130111920.png|600]]

* make a plot of the MWPC beam size before and after my quadrupole scan to see if there is a change in beam size to confirm.


### CHIMERA quadrupole scan

[PS logbook entry: CHIMERA quadrupole scan](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3659020)

[[MWPC ion quadrupole scan]]

### Dispersion measurement on the East Dump with the ion beam

During the CHIMERA nov run 2022 we changed the B-field from 2500 to 2600 G and we observed the shift in position of the beam.

It moves to the left by ~20 mm. We see the beam movement because the bending magnet to the east dump do not scale with momentum. Also the beam size $\sigma$ shrink from 9.58 to 8.47 mm.

2500 G
![[Pasted image 20221209160140.png|475]]

2600 G
![[Pasted image 20221209160220.png|475]]