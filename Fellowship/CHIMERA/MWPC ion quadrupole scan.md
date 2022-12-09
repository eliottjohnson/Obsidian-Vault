During the CHIMERA nov 2022 run we did some quadrupole scan on the MWPC located in CHARM
[Source code: quad_scan_mwpc_chimera.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/EliottBranch/ps_extraction/f61t8/quad_scan_mwpc_chimera.ipynb)
[PS logbook entry](https://be-op-logbook.web.cern.ch/elogbook-server/GET/showEventInLogbook/3659020)

The first thing only one minimum in the horizontal plane but a lot of nice minimum in the vertical plane.

We notice that the quadrupoles are scaled only with one momentum (the one in the ring) and does not take into account the fully stripped ion momentum.
What this means is the the logical k values set in the working set calculates are current as if the momentum of the beam is a partially stripped ion beam with 54 charges but this is wrong after the first quad where the ions are fully stripped to 82 charges.

Some images of the MWPC quad scan raw measurement:

![[quad_scan_t8_ion_2022_11_27_13h10m52s_raw_measurement 1.png|375]]


![[quad_scan_t8_ion_2022_11_27_13h25m53s_raw_measurement 1.png|375]]

![[quad_scan_t8_ion_2022_11_27_13h32m53s_raw_measurement 1.png|375]]

![[quad_scan_t8_ion_2022_11_27_13h45m31s_raw_measurement 1.png|375]]

![[quad_scan_t8_ion_2022_11_27_13h56m20s_raw_measurement 1.png|375]]

![[quad_scan_t8_ion_2022_11_27_14h12m07s_raw_measurement 2.png|375]]

![[quad_scan_t8_ion_2022_11_27_14h26m22s_raw_measurement 1.png|375]]

Then I try to fit to MAD-X

