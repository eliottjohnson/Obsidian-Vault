---

kanban-plugin: basic

---

## Day list

- [ ] * [ ] Write in the codilog the marche à suivre to perform a quadrupole scan and find init params
- [ ] * [ ] Check BPM UCAP and logging if I get the same values
- [ ] * [ ] Continue to write the CHIMERA document
- [ ] * [ ] First moment, second moment
- [ ] * [ ] Plot ellipse of stray field model
- [ ] * [ ] Check Aperture restriction
- [ ] **Air scatter**
- [ ] * [ ] Calculate the new beta, beta1=bet0*pi/4
- [ ] * [ ] The change in Beta is only if you want to rematch your beam to the scatterer.
- [ ] * [ ] Maybe you could track distributions kick with a thin kick after the air, recalculate the distribution and continue tracking
- [ ] **YASP**
- [ ] * [ ] upload custom twiss with different optics
- [ ] * [ ] Add corrector strength to model and when you change optics, try to get back the same optics
- [ ] * [ ] Add dipoles as correctors
- [ ] * [ ] Add BTV as steerers
- [ ] * [ ] Put Alex and Betina in copy
- [ ] **East Dump Specification**<br><br>* [x] Use pessimistic situations (2 cycles dumped consecutively)<br>* [ ] add margin to max. intensity<br>* [x] Look at comments<br>* [ ] Check with Matt final list of reviewer<br>* [ ] Start EDMS review procedure with Thomas Birtwistle


## Stray field geometry with Miro

- [ ] * [ ] Set up a meeting with Alex to find the currents in the MUs<br>* There are 5 loops<br>* [ ] Find out the current in each loops<br>1) F8L<br>PFW<br>2) wide<br>3) narrow<br>4) focusing<br>5) defocusing
- [ ] 4 Tasks for Miro<br>* PFW currents<br>* MU63 shims<br>* F16 shims<br>* BTP injection mu-metal


## Mid Term

- [ ] T8 misalignment
- [ ] Dipanwita would like to have beam size at the entrance and exit of F6x bends
- [ ] Also beam size that includes the sweep
- [ ] EDMS document on East dump<br>* [ ] Read comments<br>* [ ] Check with Matthew the final list of reviewers<br>* [ ] Start EDMS review procedure with Thomas Birtwistle


## Long Term plan

- [ ] Summer 2021 Medium term plan:<br>Injection multipole test with new multipole<br>Add multipole extraction to MAD-X<br>Compare measurements with model<br>Slow extraction simulation with maptrack<br>Discuss with Rebecca Taylor<br>Kick response F16 https://codimd.web.cern.ch/vbCKYWnkSXyyrCLgahP7Rg
- [ ] HE corrector optimisation with fast extracted beam<br>Octupoles for CHIMERA<br>Optimiser with a H corrector to corrector for sweep ?<br>Fast beam: Does the beam still saturate with filter ? If you add a delay the beam will decay and saturate less, does it change the beam size ?
- [ ] Notes:<br>No dispersion in the vertical plane<br>Does the model predict a big sweep at the dump<br>Beam size changes with radial steering
- [ ] Rastering:<br>Laminated magnet to fight eddy currents<br>Plot X and Y functions as a function of time<br>Plot [Tm] and [ms] to discuss feasability<br>Discuss beam size (the smaller, the faster you need to raster)<br>Spiral inward instead of outward<br><br>VLC stream BTVs subscribe to a timing event, so that the callback get triggered at the time associated with the trigger.
- [ ] No date<br>UDEMY lecture on image processing<br>Check who is ramping, dipoles, quadrupoles, HE, bump, PFW<br>How do you grab the spill ? On SEC070 and SEC094 ?<br>Upload quad scan data to gitlab      <br>Tell stephane what filter we need in BTV020 and BTV035<br>Dispersion * 0.3/% with MAD-X model, look at the dispersion at the dump<br>Mask the center of saturated beam<br>Do this for BTV35
- [ ] Alex Ideas<br>Compare fit of beam size of saturated beam when you fit only on the curvature or when you fit with unsatured beam<br>Does the VLC stream acquisition movemement we see on beam size and sweep change as we are further away or closer from the F8L ?<br>Can you do a Dispersion measurement with a fast beam
- [ ] Ideas from Yann<br>low level cpymad from his example repository. Something lib...


## Following MD

- [ ] Following MD<br>Optics change during the spill: is the dynamic effect because we ramp the quads with momentum? MD ramp and don't ramp the quad and look at the beam size if it's still dynamic.<br>MD to CHARM on a Wednesday to test predictiveness of the model<br>Grap BPM data from Federico (published ?)<br>Quad scan measurements dedicated T8 at high intensity on IRRAD BPMs<br>VLC stream on the BTV PR57 to see if the spiral step changes. If it moves in the ring. Use a timing event to trigger the callback event.
- [ ] Unplanned:<br>Fast extraction and kick response measurement with the model including new fringe fields and new lower beam loss. With Kicker and septum.<br>HE corrector optimisation with fast extraced beam<br>Ramping the transfer line with p to measure dispersion
- [ ] 5 - 19th october cryostat (no dedicated MD in T8)


## CHIMERA

- [ ] CHIMERA<br>Discuss tasks to advance with the CHIMERA run in mind at the end of the year<br><br>Later<br>Do Radiation Protection Refresher<br>Import North Optics for T9, T10 for Denis, same procedure as I did for T8<br>Change the values at injection with the ones I found<br>SWAN_projects/btp_stray_elements/multiple_field_component_injection<br>SWAN_projects/acc-models-tls-eliott-fork/ps_injection/bt3btp_lhcindiv/stitched/jmad/kick_response_new_tracking_MFC_model<br>Gil + Marc<br>Optimiser sur les high-level knob (bump en [cm])<br>Fix the tail on the BPM, sweep ?<br>The beam gets smaller on the BPM1-4, it gets focused horizontally and defocused vertically we would like parallel


## IRRAD

- [ ] No dedicated MD possible week of 5th to 19th oct because of cryostat




%% kanban:settings
```
{"kanban-plugin":"basic","date-picker-week-start":1,"show-checkboxes":false}
```
%%