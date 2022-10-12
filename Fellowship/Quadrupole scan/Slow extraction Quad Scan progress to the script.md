# Slow extraction Quad Scan progress to the script

* [ ] Find a way to characterize the spill
* [x] Acquire the profile during the spill
    * [x] Fit them
        * [x] Start with Gaussian
        * [x] Horizontal plane distribution isn't gaussian, maybe use a double gaussian
        * [x] Calculate first moment: mean
        * [x] Calculate second moment: RMS
    * [ ] Average them
    * [ ] This gives an average beam size throughout the spill
* [x] See the dynamic effect during the spill
    * [x] Beam size changes in time
        * [x] Use the ctime
    * [x] If beam size changes it mean we are not doing COSE
    * [x] If the beam size changes it means the optics isn't constant and something in the machine isn't scaling with momentum
    * [x] Plot a waterfall beam size as a function of time in each plane
* [ ] If you don't average the beam size, it's like if you were doing x-number of quad scan (one per acquisition basically) with different optics at each time
* [ ] Think about normalization, if the rate of extraction isn't constant, each acquisition will have a different height/intensity
    * [ ] Normalize by the area under the projection
    * [ ] Look in Google how to normalize a gaussian
    * [ ] Look at the difference between the waterfall of normalized and unnormalized projections
* [x] Remove the background
* [x] UCAP, virtual device that does python
    * [x] Beam position as a function of time
    * [x] Average beam position
    * [x] [Marcel's logbook entry](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3531699)
* At low energy, it should be more COSE
    * Machine is linear
    * Optics is much more constant
    * Quadrupolar component of the combined function machine follows the dipole component better

![](https://codimd.web.cern.ch/uploads/upload_0ba5dafe081bc4eb9545a181c7dce4b2.png)

[Source code permalink: blit.py](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/18bc2b71e2d9d15a675849e68311f04945c287c7/blit.py)

![](https://codimd.web.cern.ch/uploads/upload_35ec1a923c608257f7bd94100557f05e.png)


https://stackoverflow.com/questions/54851012/fitting-data-with-multiple-gaussian-profiles-in-python?rq=1

![](https://codimd.web.cern.ch/uploads/upload_ccd512d7652404ecfebab70c7e0c0e4d.png)

* [ ] Run the optimizer with the HE correctors
    * [ ] Check the emittance in the PS with the wire scanner
    * [ ] Also do a tune measurement
    * [ ] Do some steering to cancel the oscillation and get a really small beam size
* [ ] If there is still a sweep
    * [ ] Optimizer with two correctors to cancel sweep
        * [ ] cancel position
        * [ ] cancel angle
* [x] Overclock:
    * [x] Try with a small width and/or length to get faster acquisitions
* [ ] Kick response measurement through the stray field
    * [ ] With KFA71 and SMH57 and SMH61