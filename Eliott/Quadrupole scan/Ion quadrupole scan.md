# Ion quadrupole scan

Two quadrupole scans were performed with Ions at high and low energy.

For measurement we use the code from [[Quadrupole Scan#Quadrupole scan with filters MD7505]]: 
[Source code: quad_scan_east_dump_multiple_with_filters.py](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/quad_scan_east_dump_multiple_with_filters.py)

## High energy
[Logbook link](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3623232)

IEAST_LI_Pb_22
LEIR: PB54_2BP_2021_06_09_EARLY_2400ms_V1

SWAN_projects/acc-models-tls-eliott-fork/ps_extraction/f61d/F61D_beam_size_ion_quadrupole_scan.ipynb
SWAN_projects/quad-scan-east/ion_quad_scan/create_df_from_filter_quad_scan_ions1.ipynb
1)  
``` python
current1 = np.linspace(0.45, 0.47969, number_of_k_to_scan)  # init 0.47969  
current2 = np.linspace(-0.1149, -0.1149, number_of_k_to_scan)  # init -0.1149  
current3 = np.linspace(0.134, 0.134, number_of_k_to_scan)  # init 0.134
```

![[Pasted image 20220927172608.png]]


SWAN_projects/quad-scan-east/ion_quad_scan/create_df_from_filter_quad_scan_ions2.ipynb
2)  
``` python
current1 = np.linspace(0.47969, 0.47969, number_of_k_to_scan)  # init 0.47969  
current2 = np.linspace(-0.08, -0.13, number_of_k_to_scan)  # init -0.1149  
current3 = np.linspace(0.134, 0.134, number_of_k_to_scan)  # init 0.134
```
  ![[phase_advance_check['quad_scan_east_slow_ions_high_energy_2022_09_26_16h00m25s'].png]]
3)  
``` python
current1 = np.linspace(0.47969, 0.47969, number_of_k_to_scan)  # init 0.47969  
current2 = np.linspace(-0.1149, -0.1149, number_of_k_to_scan)  # init -0.1149  
current3 = np.linspace(0.10, 0.16, number_of_k_to_scan)  # init 0.134
```
![[phase_advance_check['quad_scan_east_slow_ions_high_energy_2022_09_26_16h50m24s'].png]]

## Low energy
[Logbook link](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3623828)

IEAST_Pb:10.7_ZGeV_22

1)  
``` python
current1 = np.linspace(0.47969, 0.47969, number_of_k_to_scan)  # init 0.47969  
current2 = np.linspace(-0.1149, -0.1149, number_of_k_to_scan)  # init -0.1149  
current3 = np.linspace(0.1, 0.16, number_of_k_to_scan)  # init 0.134
```
  
2)  
``` python
current1 = np.linspace(0.47969, 0.47969, number_of_k_to_scan)  # init 0.47969
current2 = np.linspace(-0.16, -0.08, number_of_k_to_scan)  # init -0.1149
current3 = np.linspace(0.134, 0.134, number_of_k_to_scan)  # init 0.134
```
  
3)  
``` python
current1 = np.linspace(0.42, 0.49, number_of_k_to_scan)  # init 0.47969
current2 = np.linspace(-0.1149, -0.1149, number_of_k_to_scan)  # init -0.1149
current3 = np.linspace(0.134, 0.134, number_of_k_to_scan)  # init 0.134
```
  
Perhaps the stray field will change at 2 GeV which would change the beta and alpha. That would be bad if we can't scale by 54/82 with energy.
It will be interesting to see the difference at low energy for a few different reasons: (I) different QSE strength? (II) different stray field effect of MU in saturation?