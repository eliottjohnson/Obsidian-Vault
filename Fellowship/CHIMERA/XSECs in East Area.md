Continuation of the discussion on [[SEC calibration EAST]] and e-mail thread from Maarten Van Dijk from 17th October 2022

## Maarten
* There is a **activation foil measurement** that Maarten is doing in the North Area
* Fast mode of the XSEC (BSI) electronics does not work properly
	* We need to measure the charge collected on the XSEC (BSI) in the fast mode in a way that we can calibrate with the fBCT.
	* This calibration could be extrapolated to the calibration in the slow mode.

## Luana

* Main **issue**: fast extraction pulse is too fast to time the sampling to catch the extraction, the electronics don't have the bandwidth necessary
	* **Solution** would be to **link a scope** directly to the xsec in fast extraction
		1) Series of fast extraction to the F61 dump to measure signal from detector
		2) Miguel  Martin Nieto can assist with this (must be done before 3rd of November as he is away until 24th nov)
		3) Contact Romain Brice Ruffieux to ask if logged measurements are calibrated.

## Matthew

* Organise via ASM a parallel MD for 24 or 25th October
	* Send fast extracted proton and ion beams to East Dump
	* Measure fBCT and XSEC **connected to scope**
		* Ruben says: very noisy on fBCT with 1e11 protons, perhaps below detection limit with ions.
* Low priority: repeat comparison between fBCT in **T8** and dowstream XSEC also with **scope** (we'll need to move it)
	* This requires to open **EA1 zone** and IRRAD/CHARM **EA2** 
	* Activities being prepared by different teams (OP , BI Beam Instrument, STI Sources, Targets and Interactions) for the 26th of October

## Federico Ravotti

* Plot of the T8.XSEC signal against T8.BCT calibration
	* done with Romain in march 2022
	* The plots shows that the spill charge integrated by the electronics was globally **under-estimated** 
	* T8.BCT only used to cross-check measurements done with Aluminium foils activation technique
	* Aluminium foils (Al) used to calibrate the T8.XSECs with slow extraction.
	* Does **not** need the Fast Extracted (FE) beam to perform a direct XSEC calibration on T8

![](file:///C:/Users/ELIOTT~1/AppData/Local/Temp/msohtmlclip1/01/clip_image002.gif)

* Ruben wants to install a scintillator in IRRAD during MD 26th of october
	* Cannot be exposed to protons
	* This would **not be compatible** with the scope connected to XSEC as we will be using protons
* Minimize extra-parallel MD not to reduce intensity delivered to T8.

## Miguel Nieto 64890

* Will install the scope in the rack on Tuesday morning
* Only need passive dosimeter because it's not directly next to the beam lines

## Ruben

* BCT signal is at its detection limit for 1e11 protons (i.e. charges). If there are less charges than this, it will not detect.
* This means that for ions, it won't detect either as they are not enough charges.

# XSEC Calibration - Plan for MD8823 - Tuesday 25th of October

1) Miguel to install scope on the XSEC23 in F61
	* Scope is in Prevessin, needs to come to the office to grab it
2) Send a few concurrent shots to East Dump of:
	1) Fast protons
		* Several intensities
		* ![[xsec_intensity.png|500]]
		* `PR.BCT/HotspotIntensity#dcBefEje2`
		* `F61.BCT01/Acquisition#totalIntensityAutoCh1`
	2) Fast ions (the fBCT signal might be low with ions)
3) Record 100 shots ~ 1h with protons and 100 shots with ions
* Data saved onboard scope
PSB MD1
PS MD2

Can't do the whole intensity scan because we are using the East Dump

[PS Logbook](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3639633)


![[Pasted image 20221025101903.png|975]]