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
Time it takes for one turn in the PS = **2.1 $\mu s$**
* $t = \frac{circumference}{c} = \frac{628}{3e8} = 2.1e-6 [s]$

5.12e2 * 2.1e-6 = 1.752e-3 s = 1.8 ms

#### Bounds

Start extraction at 1200 to 1599
interval 1 ms
Nb of Acq (nb of chirps)



![[Pasted image 20221028150919.png]]

## MD

[PS Logbook Event](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3643633)

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


XSEC23 set to HIGH at 16:02 LT

XSEC23I2 set to HIGH at 16:12

Injection oscillation to follow up with YASP

On a mis le XSE, QSE and LEQ to 1090 ms before extraction to remove the spike
16:52 LT

Intensity scan at 16:59

No bump
Spike is lost in the machine
Pulsed close to khz for now

Amplitude, repetition rate
Grab the raw data for the function on the plates, we need the raw voltage (ask Tom in charge of instrument)

[PSMD Logbook Entry #1](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3643689)

**Qmeter2 BBQ Settings**  
Pickup: Long  
Accuracy: 256  
From: 1260ms  
To: 1759ms  
**Interval: 4ms / 0.25 kHz**  
n Acq: 250  
H plane strength: 0.35  
Chirp Freq Range H: 0.3 to 0.35 Hz

![[Pasted image 20221102092655.png|575]]

![[Pasted image 20221102092711.png|575]]

![[Pasted image 20221102092721.png|375]]

![[Pasted image 20221102092729.png|525]]

[PSMD Logbook Entry #2](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3643684)

**Qmeter2 BBQ Settings**  
Pickup: Long  
Accuracy: 256  
From: 1260ms  
To: 1759ms  
**Interval: 2ms / 0.5 kHz**
n Acq: 250  
H plane strength: 0.35  
Chirp Freq Range H: 0.3 to 0.35 Hz  

![[Pasted image 20221102092741.png|550]]

![[Pasted image 20221102092749.png|625]]

![[Pasted image 20221102092800.png|325]]

![[Pasted image 20221102092808.png|500]]

[PSMD Logbook Entry #3](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3643681)

**Qmeter2 BBQ Settings**  
Pickup: Long  
Accuracy: 256  
From: 1260ms  
To: 1759ms  
**Interval: 1ms / 1kHz**
n Acq: 500  
H plane strength: 0.35  
Chirp Freq Range H: 0.3 to 0.35 Hz

![[Pasted image 20221102093008.png]]
![[Pasted image 20221102093021.png|575]]

![[Pasted image 20221102093049.png|225]]

![[Pasted image 20221102093030.png|375]]

![[Pasted image 20221102093042.png|400]]



Long /Short length of physical thing in RF

Accuracy (turns) how many turns your measure for 256

Gain 0.01

Plan

Gain scan at several frequency of chirp

# Thursday

[Repository for MD8923](https://gitlab.cern.ch/tbass/md-8923/-/blob/master/script.ipynb)

```python
QMETER_DEVICE = 'PR.BQL72/Setting'

QMETER_SETTINGS = { 'ex_mode': ('#exMode', 1), 'acq_on': ('#acqState', 1), 'acq_mode': ('#acqMode', 0), 'det_fft_window': ('#fftWindowFunction', 2), 'n_measurements': ('#nbOfMeas', 12), 'n_turns': ('#nbOfTurns', 1024), 'interval': ('#acqPeriod', 6), 'from': ('#acqOffset', 482+170), 'ex_h_amplitude': ('#exAmplitudeH', 0.06), 'ex_v_amplitude': ('#exAmplitudeV', 0.06), 'ex_h_enable': ('#exEnableH', 'True'), 'ex_v_enable': ('#exEnableV', 'False'), 'chirp_h_start': ('#chirpStartFreqH', 0.23), 'chirp_h_stop': ('#chirpStopFreqH', 0.27), 'chirp_v_start': ('#chirpStartFreqV', 0.25), 'chirp_v_stop': ('#chirpStopFreqV', 0.40), 'bias_h': ('#biasH', 0), 'bias_v': ('#biasV', 0), 'time_const_1h': ('#timeConstant1H', 1), 'time_const_2h': ('#timeConstant2H', 1), 'time_const_1v': ('#timeConstant1V', 1), 'time_const_2v': ('#timeConstant2V', 1), 'DC_det_1': ('#DCdet1', 0), 'DC_det_2': ('#DCdet2', 0), 'ex_pattern': ('#exPattern', 1), }

[x for x in japc.getParam('PR.BQL72/Setting').keys() if 'exAmplitude' in x]

japc.getParamInfo('PR.BQL72/Setting#exAmplitudeV')
```

Automatic gain scan