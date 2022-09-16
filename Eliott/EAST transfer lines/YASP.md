# YASP

YASP is a script to steer the beam in the control room using numerical kick prediction.
It is useful when loading a new optics because it **resteers** the beam which is time consuming.
Ask Denis, Marcel and then Jorg Wenniger

To-Do:
* [ ] Implement new corrector (dipoles)
* [ ] Add BTV, MWPC UCAP and BPMs devices as steerers
* [ ] Create a set of intermediate optics file not to loose the beam

There is a table in LSA called "STEERING_CONFIG_PARAMS" which contains all the configuration as well as the monitors and correctors for each configuration.

### List of UCAP devices

These are the devices we would like to add

They are in the EXCTRACTION-61 -> CPS:EA-INSTRUM working set (except MWPC)

**BPMs:**
PS-LOG-BPM-IRRAD-UCAP_BPM_01/Positions
PS-LOG-BPM-IRRAD-UCAP_BPM_02/Positions
PS-LOG-BPM-IRRAD-UCAP_BPM_03/Positions
PS-LOG-BPM-IRRAD-UCAP_BPM_04/Positions

**BTVs:**
PS-LOG-BTV-UCAP_F61_BTV012/Positions
PS-LOG-BTV-UCAP_F61D_BTV010/Positions
PS-LOG-BTV-UCAP_T8_BTV020/Positions
PS-LOG-BTV-UCAP_T8_BTV035/Positions
PS-LOG-BTV-UCAP_T8_BTV096/Positions

**MWPC:**
* PS-LOG-MWPC-UCAP_IRRAD_2080/
	* HighGainPositions
	* HighGainProfilesAcquisition
	* **LowGainPositions** -> gives HCenter/HSigma, VCenter, VSigma
	* LowGainProfilesAcquisition

Jorg is missing a field with an official machine sequence name to identify each element.

Marc has added a field called Positions/DeviceName

MWPC doesn't work yet ? (Not in the working set)

We will only do the T8 line as it is the easiest one to do.