# MD Planning

### MD Objectives & beam requirements (part 1) – (SY-ABT | OP),
-   bringing back to life the 5.4 GeV/u cycle and setup a ~ 1 GeV/u ion cycle (Marc & Gil),
-   extraction using transverse damper excitation (low & stable beam intensities to EAST) (Matt, Pablo, Thomas):
	-   setting duplicate cycles with transverse damper option,
	-   testing this extraction mode for ion cycle(s),
-   characterization of the transfer line optics (Eliott):
	-   Quad scan & YASP (Yet Another Steering Program),
-   testing low energy (2GeV) proton transport to T8,
-   testing ions transport to T8 at different energies,

### MD Objectives  & requirements (part 2) – (R2E).
-   Focus on the needs related to beam instrumentation and logging:
	-   Testing if all BI logging is working correctly,
	-   Calibration of the SEC70 with T8.FBCT (ions, FAST),
		-   Different ion energies?

 ### Discussion:
-   Formal request procedure & timeline,
-   Actions distribution,
-   AoB

Ion cycle setup in PS on the dump (by Marc) at nominal energy.
Revived last years cycle to the east dump.

Two beams: one bunch version, other version nominal with two bunches (higher intensity) the second one is working.
What intensity do we want ?
* Lower intensity range, maybe easier to have a higher intensity beam and change extraction with different extraction techniques (transverse damper, need to steer extraction with bump height)
* 2e6 ions per spill last year.
* 1e10, 6e10 charges, so to lower we need to change extraction technique = play with the tune sweep (PFW)
* Look at spill with scintillator for spill as a function of time
* How low can we go with intensity with tune sweep ?
* BPM in IRRAD can measure time profile of the beam

Optics measurements in parallel to dump (optics measurement) and to T8
T8 PPM ? Will be done with Kostas.

5 to 19th cryostat: MD dedicated to T8 can start **26th of October and one on 2nd (16th) of November**. Check with Salvatore in CHARM. Also if MONTRAC available.
Is 1 GeV/u (1 GeV per nucleon) low enough with FLUKA for transmission ? We need more than 50% transmission. 1 GeV is 20% transmission so we would need high intensity.

LINAC3 and LEIR team for operational support. Piquet.

Encourage BI team to be there on the 26 and 16th. Connect picoscope on XSEC070 in IRRAD.

Federico's VISTAR BPM, pay attention to timings of DAQ.
Change scale on website.

~~Add YASP Jorg Marcel on MWPC (and BTVs but maybe won't see with ions) in the next few weeks.

### Requirements:
Shape of beam: gaussian
200-300 ms spill
Beam size: Small beam, big beam
	small: FWHM 3 cm 2e4 - 2e7 ions/spill
	big: FWHM 10 cm 1.75e5 - 1.75e8 ions/spill
	at target which is the MWPC/MONTRAC
	last year was 
Beam energy: 100 - 400 MeV/n provides an interesting LET range of 15-35 MeVcm^2/mg. Work with 1GeV/n and degrade it with polyethylene
Beam intensity: discuss with LEIR for lower intensity in LEIR to PS. Simon and Reyes suggested to make a test. Problem will be the RF loops. Maybe one high intensity bunch and one low intensity bunch.

### MD plan for 28th sept

Start beam at 11h and give back at 19pm.

Intensity scaling ?
Lower energy ?

* Slow spill at nominal rigidity 24 GeV to have references on BTV. Then 2 GeV slow extraction.
* See if scaling is done with LSA, use YASP or other steering tools.
* If trouble, switch to protons for YASP.
* Federico with a picoscope in IRRAD.

Quad scan on dump at another date at lower energy.


## 28.09 MD plan:
-   1) Recovering the high intensity, nominal energy beam we had last year.

-   2) Performing fast extraction for SEC calibration (especially if we progress with the pico-scope solution).

-   3) Reducing the intensity, if possible to at least ~1e6 ions/spill (again, similarly to what we did last year).  Special attention to be devoted to impact of intensity reduction on spill duration.

-   4) Repetition of fast extraction to have another calibration point at lower intensity (Not possible for Marc).
	- Early or Nominal intensity in LEIR to have two points
	- Can't trust signal from XSEC in fast mode (lot of noise from Federico) - ringing of the signal.
		- checking if impedance is matched
		- struggle to get absolute measurement of intensity
		- calibration done by clean transmission from the ring
	- XSEC in slow mode
		- Full of systematic errors
		- unreliable
	- XION can be trusted
		- can count single events

-   5) Repeat the steps above, with ~2 GeV/n energy

* Bonus, machine far more linear at lower energy

### Kick response with YASP
must be done to T8 pick up sign inversion, etc
maybe be to be done with protons
automatic routine for kick response

Try to further push down the energy, to experimentally determine the lower energy limit for “clean” beam transport

Ask Denis to upload twiss to YASP

**BCT is logged ?**
SEC signal and picoscope
**Duration of the spill** would be an important metric.

Does the MWPC need a special setting for low energy ions.
Ionization chambers move in an out of the beam.

### Dedicated MD Wednesday 28.09.22

scintillator BCCGA
Working set -> PS-Sampler -> CPS 

LEIR down -> contacting Rheyes

800 ms spill would be possible - tbd with Ruben

EAST4  Fast 24 GeV = 5.4 GeV/u
MD3 Slow 24 GeV = 5.4 GeV/u
MD4 Slow 2 GeV/u
MD7 Slow 1 GeV/u