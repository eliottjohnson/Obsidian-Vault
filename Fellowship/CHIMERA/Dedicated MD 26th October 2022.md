
## Beam settings

* We will use during the whole MD the **750 MeV/u Pb ion beam**
	* Trade-off between lower energies and intensities
	* We won't be "at the limit" but rather keep some **margin** to have better visibility on the instruments

```ad-warning
**No protons on Wednesday** (such as a spare EAST in old super cycle) as this would break the plastic scintillator
```

## High priority

* Simulated **nominal slow extracted beam** we will use on the 23-28 November run
	* Low energy **750 MeV/u** (20 min)
	* Low intensity

* Several minutes with fixed beam settings
	* Perform characterization with **solid-state detector**
	* One beam configuration will be broken down with **degrader**
* Instruments:
	* SECs
	* XIONs
	* [[MWPC]]
	* [[Gas scintillator spill monitor]]
	* R2E
		* [[counting scintillator (plastic scintillator)]] - only use ions because protons would damage it
		* solid-state silicon detector (diode)
		* [[SRAM]]s

* **Intensity scan**, test three techniques :
	* LEQ strength and function shape
	* Bump23 strength
	* Bump23 + Feedback that shakes the beam
All the intensity would be at SE flat-top
Test spill length

![[Pasted image 20221024130702.png|975]]

## Schedule

```ad-important

Call Andreas and Natalia before and after beam modification to inform them when they can start logging data. They will separate the data logging into separate files.

```

**PS Shutdown from 08:00 to 12:00**
Access from 09:00 to 12:00

* Beam setup
	* Keep a note of the LEQ settings for afternoon degrader test
* High intensity data taking (~20 min)
* Low intensity setup (~ 20 min)
	* Keep a note of the LEQ settings + Bump23 height for afternoon degrader test
* Low intensity data taking (~20 min)

- **Degrader access installation at 16:15**

* High intensity data taking (~20 min)
* Low intensity data taking (~20 min)


## Access

IRRAD access is planned from 09:00 to 12:00. The cryostat needs an hour to move plus some additional time for the entry and exit of the zone. They'll stop the beam between 00:00 and 01:00 the night before.

Andreas and Natalia will install the plastic scintillator also during the 09:00 to 12:00 access and will require much less time

3h PS shutdown overlaps with the access

* Access person from RP
	* Arnaud Devienne
	* Jean-Fran??ois Gruber
* One access at **16:15**
	* To install the degrader in the MONTRAC
* One access at **18:30**
	* Remove the scintillator (IRRAD)
	* Remove the diode and SRAM (CHARM)


## Low priority
* **[[MWPC Quadrupole scan#Low energy]]**, (30-60 min)
	* in IRRAD/CHARM
	* two last quads
		* k7 scan = -0.04, -0.1
		* k8 scan = 0.07, 0.08
	* find minimum
	* before degrader installation
	* high intensity
	* (would actually be best at 2 GeV/u to have less air scattering)

* Fast extraction and SEC calibration, see [[XSECs in East Area#Matthew]]

## Intensity degradation

See [[Intensity control for CHIMERA]]
* LEQ tune sweep adjustment
* Bump technique on 23
* TFB blow-up
* Marc tried on the 20.11.22 to degrade the intensity with a bump on [[TPS15 Dummy septum]] with bumpers 12-20 at the start of flat top


## Summary of the MD

[Logbook entry](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3641009)

No beam from 12-13 because of IRRAD access
No beam from 13-16 because of a faulty extraction kicker magnet from LEIR (great help from Nico Madysa)

### LEQ

The LEQ were kept fixed.
![[Pasted image 20221027085416.png|525]]

### Bump23
![[Pasted image 20221027091122.png|525]]

We pushed the bump from 0.00321 (barely touching) to high around 0.00334 (completely kills the beam)

### TFB

![[Pasted image 20221027085050.png|450]]

![[Pasted image 20221027085113.png|450]]

Then we used the TFB
Start - End BLU: 505 - 795
Exc DDS1harmonic 6.26000 (we scanned 6.25500 to 6.26500)
and the gain to 0.1200 works well

![[Pasted image 20221027091016.png|450]]

Some **jitter** during the blow-up:
* The jitter we saw might be due to the radial loop still being active when we make the bump in 23 to reduce the intensity.
* At low intensity the radial loop will be perturbed, also we also have a radial loop pick-up inside.
* Next time we need to do the intensity reduction **after** loop has been turned off

### MWPC

![[Pasted image 20221027090857.png|775]]
![[Pasted image 20221027090928.png|775]]
![[Pasted image 20221027090948.png|775]]

### XSEC70

![[Pasted image 20221027091100.png|775]]

### Spill monitor

![[Pasted image 20221027091617.png|675]]
## Analysis
### Spill XSEC23

![[xsec_spill_history_750_MeV_MD_26th 1.png|1200]]

#### Spill at high intensity without any intensity degradation
![[xsec_spill_high_intensity_750_MeV_MD_26th.png|800]]

#### Spill with bump23
![[xsec_spill_bump23_750_MeV_MD_26th.png|800]]

#### Spill with bump23 + TFB
![[xsec_spill_bump23TFB_750_MeV_MD_26th.png|800]]

Zoom on bump23 + TFB
![[xsec_spill_bump23TFB_rescaled_750_MeV_MD_26th.png|800]]

#### Comparison of the spill shape at different intensites

No significant spill shape change at different intensities

![[xsec_spill_compare_shape_750_MeV_MD_26th.png|800]]

#### Intensities

Integral of the spill data

![[xsec_spill_750_MeV_MD_26th_intensities.png|800]]


![[xsec_spill_750_MeV_MD_26th_intensities_sorted.png|800]]

### Scintillator

The instrument is the [[Gas scintillator spill monitor]] in F61

![[scint_750_MeV_MD_26th_comparison_with_xsec_time.png|800]]

Scintillator doesn???t have enough **gain** to see well enough the ion spill
* Hard to distinguish between the two cycles

![[scint_vs_xsec_750_MeV_MD_26th.png|800]]

* Weak correlation between the XSEC and gas Scintillator
* Next week:
	* Inaki increase the voltage of the gas scintillator by 50 V
	* Look at BXSCINT_1001 instead of BXSCINT_1000
	* Maybe change scintillator gas from N2 to Ar+N2 mix
![[scint_750_MeV_MD_26th_comparison_with_xsec.png|800]]