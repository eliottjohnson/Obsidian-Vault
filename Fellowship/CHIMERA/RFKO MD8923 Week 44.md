> [!warning]
> Send a message to Federico Ravotti on mattermost when we send ions to the Dump.
> No ions to T8 !
> 

> [!warning]
SEC23 to HIGH during MD of the 26th

### TFB blow up (RFKO)

Do TFB **after** the radial loop has been turned off. (see [[Dedicated MD 26th October 2022#Summary of the MD]])

See [[Slow extraction theory#Transit time]] and [[Slow extraction theory#TFB extraction (RFKO)]]

[Logbook entry: TFB driven SX on EAST4](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3605176) with protons

We can set-up the extraction as we did for protons where we touch the resonance  (with GRPOS) and then back off in tune, using the TFB to push the particles into resonance. The machine is static (nothing ramping). We might need to steer through the extraction channel.

Thomas can then get acquainted with the different modes of operation of the TFB excitation and look into scripting it whilst grabbing the spill intensity and beam loss. This will be an important step to benchmark time dependent effects in simulation. At the same time we can see how well we can control the extracted flux for CHIMERA.

This would be a good start to looking at what tune excitation functions would be useful to generate smooth spills and look at how far we can sit from resonance whilst still extracting clean spills.


## Schedule

### Tuesday 1/11/2022

14:00 - 20:00

1) Bump23
	First try the same techniques as we did for CHIMERA during [[Dedicated MD 26th October 2022]] but we bump23 after the RF loop is turned off (you'll see on the MRP when the signal is noisy - which means the beam is debunched)
	We should place the bump23 when the bump57 is stable

2) RFKO
	* The plan is to **remove the ramp** on the B-field and **touch the resonance** with the GRPOS (LEQ would also change the tune but change the optics).
	* Then we'll *chirp* with the Q-meter. Perhaps we can try **faster chirps** to remove the spikes during the spill.
	* We probably won't be able to use the spill monitor (scintillator) with ions at low intensities, only the XSEC23 which has 20 ms between data points.

### Thursday 3/11/2022

14:00 - 20:00

### Plan

Go close to the tune with the radial loop **GRPOS**
Turn of the loop
Increase RF
Steering
Scan

Some settings we could try:
#### Chirp in H Plane
Plane & Strength: 0.2 and we can increase the gain to 1

#### Chirp Frequency range
0.3 - 0.33

#### Accuracy (turns)

Lowest chirps is 512 turns
1 turn = 2.1 $\mu s$
5.12e2 * 2.1e-6 = 1.752e-3 s = 1.8 ms

#### Bounds

Start extraction at 1200 to 1599
interval 1 ms
Nb of Acq (nb of chirps)



![[Pasted image 20221028150919.png]]

## MD

Retracted the bump23
Flatten the ramp on POPS
Removed the LEQ function
Inserted the internal dump 14:22
Put the LEQ flat 
GRPOS increase to slow extract then retract to be just below the resonance 14:43
* We went negative
2581 POPS ramp plateau

Start chirping at 15:35 LT

GRPOS set back to zero
Bump23 after RF to trim the halo of the beam