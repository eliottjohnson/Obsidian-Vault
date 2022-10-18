---

kanban-plugin: basic

---

## CHIMERA

- [ ] Finish the CHIMERA doc
- [ ] Read the data from TIMBER of the ion run on the 28th of september including beam size on BTVs and MWPC
- [ ] Look at the BPM readout and MWPC readout at different energies
- [x] Perform quadrupole scans at 750 and 400 MeV/u
- [ ] Analysis quadrupole scan data
- [ ] Save data from spill monitor and XSEC
- [ ] Create a savedata script
- [ ] Picoscope test
- [ ] Send Andreas BPM values from NXCALS for the parallel optics and follow up with his FLUKA simulation.
- [ ] Check Dispersion at BPM1


## Stray Field

- [ ] Magnetic measurement of a spare MU being performed, create slides for Carlo to measure stray fields


## [[IPAC 2023]]

- [ ] Think of an Abtract<br>* Stray fields<br>* East Area ion beams


## [[Multipole field component in MU62]]

- [ ] Connect PS Ring to Transfer line
- [ ] Track twiss from fast extraction and compare with measurement


## [[Emittance blow-up]]

- [ ] Calculate the new beta, beta1=bet0*pi/4
- [ ] The change in Beta is only if you want to rematch your beam to the scatterer.
- [ ] Maybe you could track distributions kick with a thin kick after the air, recalculate the distribution and continue tracking
- [ ] Meeting with Ruben, Andreas, Luigi and Matthew
- [ ] Calculate a monte carlo dipole kicks (c.f. pycollimate)


## [[YASP]]

- [x] upload custom twiss with different optics
- [ ] Add the MWPC in the working set
- [ ] Add corrector strength to model and when you change optics, try to get back the same optics


## [[EDMS document East Dump]]

- [ ] Add Reference from Giulia for the Dump


## MWPC Timing issue

- [ ] Contact Stephen Jackson in charge of the BI-SW section


## Other

- [ ] UDEMY: Python for Computer Vision
- [ ] Write in the codilog the marche à suivre to perform a quadrupole scan and find init params
- [ ] Check BPM UCAP and logging if I get the same values
- [ ] First moment, second moment


***

## Archive

- [x] Wednesday 28 MD with ions
- [x] Prepare the excel sheet I had to convert to ions
- [x] Quad scan for initial parameters with ions
- [x] Look at the 2GeV/n beam and how the momentum scales in LSA, also the B-field. The rigidity will be lower because we gain charges
- [x] Continue understand rigidity for ions with the [[MU current scaling with momentum]] note and Andreas overleaf table
- [x] Marc's code to ion energy to equivalent proton energy
- [x] - Dipanwita would like to have beam size at the entrance and exit of F6x bends
- [x] - Beam size at three bending magnets: MBXHD005, MBXHD001 and MBXHD005
- [x] - MCB magnet aperture (quite large)
- [x] - Check Aperture restriction
- [x] Talk with Denis
- [x] Talk with Jurg
- [x] Add dipoles as correctors
- [x] Add BTV as steerers
- [x] Add device name as an additional field
- [x] Check if device name is correct
- [x] Map device name to optics sequence name
- [x] Export MFC to seq and ele files
- [x] Add MFC to transfer line sequence
- [x] Check Aperture restriction
- [x] Use pessimistic situations (2 cycles dumped consecutively)
- [x] add margin to max. intensity
- [x] Look at comments
- [x] Check with Matt final list of reviewer
- [x] Optics on Slow ions 24 GeV (will be used on wednesday), then slow ions at 2 GeV
- [x] MAD-X use proton beam and then scale current by 54/82
- [x] Prepare a table with the old currents in the line when we had ions
- [x] Check LSA for how it computes the momentum and energy
- [x] How do you scale with energy ?
- [x] Look at the quad scan at low energy
- [x] Ask Jean-Michel how to log BLM-ST for MD3 and MD4 as well
- [x] Try to see the BTV acquisition from the dedicated MD
- [x] Do an FFT on the BLM008-ST samples by first converting the integral to a time series and then doing an FFT
- [x] Discuss with Andreas and Natalia
- [x] Start EDMS review procedure with Thomas Birtwistle
- [x] Plot ellipse of stray field model
- [x] Track single particles from Matt's distribution (non-linear can't do twiss)

%% kanban:settings
```
{"kanban-plugin":"basic","show-checkboxes":true}
```
%%