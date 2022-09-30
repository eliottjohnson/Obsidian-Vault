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

## How to operate YASP

1) Control
2) YASP PS
3) LOWENERGY
4) File
5) Online Context Selection
6) Cycle -> East_T8_22 and Particle Transfer -> T08Transfer
7) Sub-configuration selection -> T8-EXTENDED


### Custom twiss import to YASP
[https://mattermost.web.cern.ch/abt/pl/jzzuqfdchp81dnhdt79k7g4zxo](https://mattermost.web.cern.ch/abt/pl/jzzuqfdchp81dnhdt79k7g4zxo)

YASP accepts the import of custom twiss by going to `Optics & Model` then `Optics Config & Details` and Expert tab.

The Twiss needs to use specific column. For instance generated in the following way
```python
madx.select(flag='twiss', clear=True)
madx.select(flag='twiss', column=['name', 's', 'betx', 'mux', 'alfx', 'dx', 'bety', 'muy', 'alfy', 'dy', 'l',  'angle', 'k1l', 'k2l'])
_ = madx.twiss(**beta0, file='/tmp/twiss.tfs').dframe()
```
![[Pasted image 20220927101715.png]]


### Automatic Kick response measurement with YASP


Optics & models
Response matrix measurement

Status control
Edit corrector status


## Bugs with config
* Trim break the correctors (pulse too long)
* H and V points do not move even if YASP publishes


