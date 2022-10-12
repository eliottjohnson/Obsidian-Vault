# SEC calibration EAST

Kacper, Natalia, Andreas, Ruben.

December: Fast and Slow runs at different energies

SEC70 needs **firmware change** for fast extraction

XSEC023
![[Pasted image 20220912104607.png]]

![[Pasted image 20220912105302.png]]

XSEC070
![[Pasted image 20220912104519.png]]

XSEC094
![[Pasted image 20220912104739.png]]

### Goal:
* calibrate SECs (mainly SEC71) with ions and protons as a function of fast extraction with the T8.fBCT.
* Have an absolute intensity measurement

### Test (proposed by Matthew and F. Roncarolo):

To be done week of 19-23th Sept

Split signal from XSEC (in F61) and acquire raw signal on **picoscope**
* Send a parallel beam to the East dump
* Save shots of the fast and slow extractions
* Offline: Integrate picoscope signal and compare to adjacent fBCT to calibrate the signal
* Goal: absolute measurement of signal and slow extraction
* Varying intensities: 1e5 - 1e7 protons per spill

2nd test:
* Move picoscope to IRRAD area and connect it to a computer with FESA

**Future:
* Picoscope installed in IRRAD with UCAP at end of the year


### BCT: Beam Current Transformer

-   Measures the absolute beam intensity by subtracting the current in "signal" and "noise" time windows.
-   Measures the current in a circular ring through which the beam passes. The current is induced by the spill.
-   [Presentation of Giueseppe on the topic](https://indico.cern.ch/event/971222/contributions/4091313/attachments/2182897/3687832/CHARM_ion_beam_calibration_full.pdf)
-   Only works for fast extraction (spill duration < 1$\mu S$)
-   I think because if slow extraction then the signal isn't strong enough and it gets lost in the noise.

### SEC: Secondary Emission Counters

- Measures the beam intensity by counting the electrons emitted by the passage of the beam through thin foils.
 * *$I = r\cdot N_{SEC}$ with
	-   I the Beam intensity
	-   r coefficient, (to be computed for Pb ion beams)
	-   NSEC Number of SEC count
-   Work for both slow and fast extraction
- 