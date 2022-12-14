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

![[Pasted image 20220927172608.png|650]]

SWAN_projects/quad-scan-east/ion_quad_scan/create_df_from_filter_quad_scan_ions2.ipynb
2)  
``` python
current1 = np.linspace(0.47969, 0.47969, number_of_k_to_scan)  # init 0.47969  
current2 = np.linspace(-0.08, -0.13, number_of_k_to_scan)  # init -0.1149  
current3 = np.linspace(0.134, 0.134, number_of_k_to_scan)  # init 0.134
```
  ![[phase_advance_check['quad_scan_east_slow_ions_high_energy_2022_09_26_16h00m25s'].png|650]]
3)  
``` python
current1 = np.linspace(0.47969, 0.47969, number_of_k_to_scan)  # init 0.47969  
current2 = np.linspace(-0.1149, -0.1149, number_of_k_to_scan)  # init -0.1149  
current3 = np.linspace(0.10, 0.16, number_of_k_to_scan)  # init 0.134
```
![[phase_advance_check['quad_scan_east_slow_ions_high_energy_2022_09_26_16h50m24s'].png|650]]

## Low energy
[Logbook link](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3623828)

IEAST_Pb:10.7_ZGeV_22

1)  
``` python
current1 = np.linspace(0.47969, 0.47969, number_of_k_to_scan)  # init 0.47969  
current2 = np.linspace(-0.1149, -0.1149, number_of_k_to_scan)  # init -0.1149  
current3 = np.linspace(0.1, 0.16, number_of_k_to_scan)  # init 0.134
```

![[quadrupole_scanquad_scan_east_slow_ions_low_energy_2022_09_27_11h28m57s.png|650]]

2)  
``` python
current1 = np.linspace(0.47969, 0.47969, number_of_k_to_scan)  # init 0.47969
current2 = np.linspace(-0.16, -0.08, number_of_k_to_scan)  # init -0.1149
current3 = np.linspace(0.134, 0.134, number_of_k_to_scan)  # init 0.134
```

![[quadrupole_scanquad_scan_east_slow_ions_low_energy_2022_09_27_13h10m38s.png|675]]

3)  
``` python
current1 = np.linspace(0.42, 0.49, number_of_k_to_scan)  # init 0.47969
current2 = np.linspace(-0.1149, -0.1149, number_of_k_to_scan)  # init -0.1149
current3 = np.linspace(0.134, 0.134, number_of_k_to_scan)  # init 0.134
```

![[quadrupole_scanquad_scan_east_slow_ions_low_energy_2022_09_27_12h40m58s.png|675]]

Perhaps the stray field will change at 2 GeV which would change the beta and alpha. That would be bad if we can't scale by 54/82 with energy.
It will be interesting to see the difference at low energy for a few different reasons: (I) different QSE strength? (II) different stray field effect of MU in saturation?

Same in the vertical plane but not in the horizontal plane.

## Comparison of the measurements

![[quadrupole_scan_Pb_ions_qfn01.png|875]]

![[quadrupole_scan_Pb_ions_qdn02.png|875]]

![[quadrupole_scan_Pb_ions_qfn03.png|875]]

Big difference in the QSE
![[Pasted image 20220929161005.png|875]]

See [[MWPC ion quadrupole scan]] for some quadrupole scan with ions in T8 on the MWPC.

## 750 MeV/u

Measurement on the Monday 17.10.2022

![[Pasted image 20221017141011.png|525]]

Inaki increased Voltage on spill monitor

![[Pasted image 20221017162558.png|525]]

1) 
``` python
current1 = np.linspace(0.42, 0.49, number_of_k_to_scan)  # init 0.47969
current2 = np.linspace(-0.1149, -0.1149, number_of_k_to_scan)  # init -0.1149
current3 = np.linspace(0.134, 0.134, number_of_k_to_scan)  # init 0.134
```

2)  
``` python
current1 = np.linspace(0.47969, 0.47969, number_of_k_to_scan)  # init 0.47969
current2 = np.linspace(-0.16, -0.08, number_of_k_to_scan)  # init -0.1149
current3 = np.linspace(0.134, 0.134, number_of_k_to_scan)  # init 0.134
```

3)  
``` python
current1 = np.linspace(0.47969, 0.47969, number_of_k_to_scan)  # init 0.47969  
current2 = np.linspace(-0.1149, -0.1149, number_of_k_to_scan)  # init -0.1149  
current3 = np.linspace(0.1, 0.16, number_of_k_to_scan)  # init 0.134
```
