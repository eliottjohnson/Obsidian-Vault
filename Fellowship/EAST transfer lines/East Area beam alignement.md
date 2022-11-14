https://indico.cern.ch/event/1219916/


[Source code mwpc_and_bpm_analysis_third_measurement.ipynb](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/mwpc_and_bpms_quad_scan/mwpc_and_bpm_analysis_third_measurement.ipynb)
Problem: the beam moves vertically when we do optics changes

![[Fellowship/EAST transfer lines/Attachments/quad_scan_focal_mwpc_no_screen_in_with_beam_following.gif|950]]

It can either be two things:
1) Quadrupole misalignment
2) Beam misalignment

The more a quadrupole is misaligned, the more the beam is bent
![[ealign_position_change.gif|950]]

The more a misaligned quadrupole is pulsed, the more it bends the magnet
![[ealign_current_change.gif|950]]


We find that the difference in beam position is 11 mm
![[ealign.png|950]]

The vertical corrector also explain this and it would mean that the IRRAD BPMs are misaligned by -5 mm to + 5mm

![[vertical_correctors.png|950]]

![[vertical_correctors_zoom.png|950]]

## Test for Wednesday the 16th of November
* Remove the vertical correctors
* quad scan of QDN7 on MWPC
	* If the Vertical centroid does not move then this means the beam is well aligned in the quadrupole and that the BPMs are misaligned