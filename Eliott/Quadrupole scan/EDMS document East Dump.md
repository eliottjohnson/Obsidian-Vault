# EDMS document East Dump

Matthew requested an EDMS document with specifications on the East Dump line.

Template can be found on [cernbox](https://cernbox.cern.ch/index.php/apps/files/?dir=/EDMS%20documents&):

## Introduction and motivation

The East Dump line allows setting the beam up for the different lines in the East Area (T8, T9, T10/T11) without impacting users using parallel MDs. Extraction and optics studies can be performed to improve the beam quality without needing a dedicated MD. Recent studies have measured the mean dose rate values (background and PS beam losses included) as a function of the intensity per spill and have shown that above 3E+11 protons per spill in a super-cycle length of 42 seconds reaches the limit for non-designated area low occupancy of 2.5 $\mu Sv/h$ which triggers the RP monitor PAXP502.

1) Protons per spill max which equates to the protons per cycle

Minimum protons per pulse (ppp)  is 6E+11 during the shortest super-cycle which is 24 cycle. As one cycle is 1.2 s, the shortest supercycle is 28.8 s and thus the minimum protons per second is 2.1E+10 p/s.

3) Minimum intensity required for the dump to be useful is 1 cycle per supercycle
	* Specifiy protons per second (on average)
	* What is the shortest supercycle length
4) T Energy (kinetic): 2 GeV -> 23 GeV
	* In momentum converts to 2.8 to 24 GeV/c
	* Beam momentum would range from 2.78 GeV/c to 23.92 GeV/c

5) Beam size 1$\sigma$ at the dump wall using the [[Nominal beam size at East dump wall]] plots.
	* H 2.13 [mm]
	* V 2.89 [mm]
	* Specify the front face, roughly the size of the BTV screen for steering. The BTV screen is a square of -5 to +5 cm so this should be the region where beam could be steered.
	* Approximate the beam as gaussian although not gaussian in the horizontal plane

6) Specify the $\frac{\Delta p}{p}$ total
7) Plots of the optics
	* $\sigma(s)$
	* $\beta(x)$
	* etc
8) Add the BTV profiles from measurements [[BTV filters]].

Conclusion