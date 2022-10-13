# BPMs in T8

###########  [New PS UCAP Node for T8 BPMs positions](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3526405)  ############
The 4 T8 BPMs positions are published if the beam dynamic destination is T8.
The node is triggered by XTIM.PX.ECY-CT/Acquisition, then it calculates a 2D gaussian fit from the 39 patches located on each BPM.
The class PS.BPM.IRRAD.UCAP publishes:
- ProfilesAcquisition/HRawProfile->Horizontal projection from the Raw Data
- ProfilesAcquisition/VRawProfile->Vertical projection from the Raw Data
- ProfilesAcquisition/HFitProfiles -> Horizontal Projection from the Fit on 50 points
- ProfilesAcquisition/VFitProfiles -> Vertical Projection from the Fit on 50 points
- Positions/HCenter -> Horizontal position
- Positions/VCenter -> Vertical position
- Positions/HSigma -> Horizontal width
- Positions/VSigma -> Vertical width
- Positions/DynDest -> Dynamic destination

The 4 new BPM devices are
PS-LOG-BPM-IRRAD-UCAP_BPM_01
PS-LOG-BPM-IRRAD-UCAP_BPM_02
PS-LOG-BPM-IRRAD-UCAP_BPM_03
PS-LOG-BPM-IRRAD-UCAP_BPM_04

It can be used by YASP for a T08 steering. 

In the pictures are attached an example on historical values.