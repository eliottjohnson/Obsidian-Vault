
Matthew requested an EDMS document with specifications on the East Dump line.

Template can be found on [cernbox](https://cernbox.cern.ch/index.php/apps/files/?dir=/EDMS%20documents&):

## Introduction and motivation

The East Dump line allows setting the beam up for the different lines in the East Area (T8, T9, T10/T11) without impacting users using parallel MDs. Extraction and optics studies can be performed to improve the beam quality without needing a dedicated MD. Recent studies have measured the mean dose rate values (background and PS beam losses included) as a function of the intensity per spill and have shown that above 3E+11 protons per spill in a super-cycle length of 42 seconds reaches the limit for non-designated area low occupancy of 2.5 $\mu Sv/h$ which triggers the RP monitor PAXP502.

1) Protons per spill max which equates to the protons per cycle

See [[Super-cycle length]] information.

Minimum protons per pulse (ppp)  is 6E+11 during the shortest super-cycle which is 24 BP. As one BP 1.2 s, the shortest super cycle is 28.8 s and thus the minimum protons per second is 2.1E+10 p/s.

With margin

Minimum protons per pulse (ppp) is 6E+11 + 25% = 7.5E+11 ppp during the shortest super-cycle which is 24 BP. As one BP is 1.2s the shortest super cycle is 28.8 s and thus the minimum protons per second is 2.6E+10. If we have two east cycle then 2.6 x 2 = 5.2E+10

RP limits for each EAST targets:

 *   6.6e10 protons/second to T8-IRRAD/CHARM  
 *   3.3e10 protons/second to T9 Target  
 *   3.3e10 protons/second to T10/T11 Target

See also [[EAST Flux limit]]

For two cycles per SC, 4.2E+10 p/s

3) Minimum intensity required for the dump to be useful is 1 cycle per super cycle
	* Specify protons per second (on average)
	* What is the shortest super cycle length
4) T Energy (kinetic): 2 GeV -> 23 GeV
	* In momentum converts to 2.8 to 24 GeV/c
	* Beam momentum would range from 2.78 GeV/c to 23.92 GeV/c

5) Beam size 1$\sigma$ at the dump wall using the [[Nominal beam size at East dump wall]] plots.
	* H 2.13 [mm]
	* V 2.89 [mm]
	* Specify the front face, roughly the size of the BTV screen for steering. The BTV screen is a square of -5 to +5 cm so this should be the region where beam could be steered.
	* Approximate the beam as gaussian although not gaussian in the horizontal plane

6) Specify the $\frac{\Delta p}{p}$ total
	* 6.79e-4
7) Plots of the optics
	* $\sigma(s)$
	* $\beta(x)$
	* etc
8) Add the BTV profiles from measurements [[BTV filters]].
   
   
### Publishing on EDMS

[EDMS: East Dump Specification](https://edms.cern.ch/document/2779463)

Giulia Romagnoli will add the dumps in the lines and position them in Layout.

Giulia Romagnoli & Silvia Schu-Erhard take care of experimental areas (incl. East Area), configuration management and hardware baseline documentation.
They will attach the doc to the correct place in EDMS, assign relevant reference and advise you on the reviewers too. They will also launch the approval process of the document afterwards.

Thomas Birtwistle takes care of the PS Complex primary lines (Booster, PS Ring, etc...)

## Silvia Schuh-Erhard

We had a brief discussion on Monday 07.11.2022
Did a great job correcting the document.

Suggested to put the appendix in the text (maybe no need for this time).

Read her comments before 3:30.

Wednesday next week deadline for document circulation

## Smallest size on the beam dump wall

![[Pasted image 20221219171941.png]]

Beam dump wall beam size $1\sigma$:
Horizontal : 0.50178 mm
Vertical: 2.30663 mm

Ellipse area: 3.636 $mm^{2}$

K1
QFN01: 0.32435110
QDN02: -0.1590138
QFN03: 0.11912984

Current:
408
371
223