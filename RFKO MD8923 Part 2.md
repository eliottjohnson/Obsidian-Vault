## Go to [[RFKO MD8923 Week 44]] Part 1

MD done on Thursday 3rd of November 2022

[Logbook entry](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3644863)

Some info on **Fourier transform**

We should as much as possible overlap the chirp boxes not to have frequency in the spill

Even if the chirp box overlap perfectly, it doesn't mean you won't have a frequency in your spill. Because the chirp frequency range will extract particles close to the resonance and move the other so you'll see square boxes.
A solution would be to chirp the frequency with a very small range and a very small gain (you would never extract the frequency that you don't chirp and they would be lost in the machine but it's good for low intensities)

![[IMG_4804 (002).jpg|250]]

There is a convolution between the box frequency (sinc in time domain) and the dirac at 1ms of the chirp. A measurement would be to increase the time between chirps to 1 ms and then scan the acq in turns.


![[Pasted image 20221102161151.png|250]]

![[Pasted image 20221102161156.png|225]]

![[IMG_4806 (002).jpg|450]]

Look at BXSCAL_1100, BXSCAL_1101

The sampling rate can be changed via the counterSampling

[Repository for MD8923](https://gitlab.cern.ch/tbass/md-8923/-/blob/master/script.ipynb)

```python
QMETER_DEVICE = 'B'

QMETER_SETTINGS = { 'ex_mode': ('#exMode', 1), 'acq_on': ('#acqState', 1), 'acq_mode': ('#acqMode', 0), 'det_fft_window': ('#fftWindowFunction', 2), 'n_measurements': ('#nbOfMeas', 12), 'n_turns': ('#nbOfTurns', 1024), 'interval': ('#acqPeriod', 6), 'from': ('#acqOffset', 482+170), 'ex_h_amplitude': ('#exAmplitudeH', 0.06), 'ex_v_amplitude': ('#exAmplitudeV', 0.06), 'ex_h_enable': ('#exEnableH', 'True'), 'ex_v_enable': ('#exEnableV', 'False'), 'chirp_h_start': ('#chirpStartFreqH', 0.23), 'chirp_h_stop': ('#chirpStopFreqH', 0.27), 'chirp_v_start': ('#chirpStartFreqV', 0.25), 'chirp_v_stop': ('#chirpStopFreqV', 0.40), 'bias_h': ('#biasH', 0), 'bias_v': ('#biasV', 0), 'time_const_1h': ('#timeConstant1H', 1), 'time_const_2h': ('#timeConstant2H', 1), 'time_const_1v': ('#timeConstant1V', 1), 'time_const_2v': ('#timeConstant2V', 1), 'DC_det_1': ('#DCdet1', 0), 'DC_det_2': ('#DCdet2', 0), 'ex_pattern': ('#exPattern', 1), }

[x for x in japc.getParam('PR.BQL72/Setting').keys() if 'exAmplitude' in x]

japc.getParamInfo('PR.BQL72/Setting#exAmplitudeV')
```

1) Automatic gain scan
* Started at 14:37
* Chirp freq from 0.3 - 0.35
* We notice that Acq Offset needs an -240 offset
* ended at 15:10


![[Pasted image 20221103154627.png|550]]

![[Pasted image 20221103154639.png|550]]

![[Pasted image 20221103154647.png|550]]

![[Pasted image 20221103154654.png|550]]
![[Pasted image 20221103154722.png|550]]

* Started at 15:14
* Chirp from from 0.2-0.35
* **Injection Timing** is **235** ms so you have to add it to Acq Offset
* ended at 15:35

![[Pasted image 20221103154729.png|550]]

![[Pasted image 20221103154735.png|550]]

* Started at 15:40
* Chirp from 0.32-0.35
* ended at 16.02
* Careful last point will be freq scan


[[RFKO frequency scan]]
Started at 16:04 ended at 16:27

[[RFKO acquisition scan]]
Started at 16:31 ended at 16:38


CHIMERA BEAM
Started at 16:41
0.32 - 0.34
Gain from 0.01 - 0.1
1ms
256 turns
Acquisition 500
data start at 16:46
Start extracting at 0.05 gain

![[Pasted image 20221103170300.png|675]]

![[Pasted image 20221103170320.png|675]]

![[Pasted image 20221103170328.png|675]]

![[Pasted image 20221103170337.png|675]]


Scan from 0.04 - 0.05 with 0.32-0.33 
Started at 17:09
XSEC23 measurement restarted at 17:15
Gain changed to high at 17:18 on XSEC23
ended at 17:22


High sampling period for ten shots
At gain 0.041
chirp range from 0.32-0.34
sampling of bxcals set to 10
At 17:26 (same file) we went to 0.042
10 shots at that intensity

At 18:13 XSEC23 intensity. I've added the gain saving to the XSEC python script
gain 0.041 no beam
gain 0.0415 little beam
You get a nicer spill if you don't overshoot the resonance (0.32 to 0.3333 instead of going to 0.34)
Started 10 points at 18:29:39 for statistics
ended at 18:44