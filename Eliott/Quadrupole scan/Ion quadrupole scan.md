# Ion quadrupole scan

Two quadrupole scans were performed with Ions at high and low energy.

For measurement we use the code from [[Quadrupole Scan#Quadrupole scan with filters MD7505]]: 
[Source code: quad_scan_east_dump_multiple_with_filters.py](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/quad_scan_east_dump_multiple_with_filters.py)

## High energy
[Logbook link](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3623232)

1)  
``` python
current1 = np.linspace(0.45, 0.47969, number_of_k_to_scan)  # init 0.47969  
current2 = np.linspace(-0.1149, -0.1149, number_of_k_to_scan)  # init -0.1149  
current3 = np.linspace(0.134, 0.134, number_of_k_to_scan)  # init 0.134
```
  
2)  
``` python
current1 = np.linspace(0.47969, 0.47969, number_of_k_to_scan)  # init 0.47969  
current2 = np.linspace(-0.08, -0.13, number_of_k_to_scan)  # init -0.1149  
current3 = np.linspace(0.134, 0.134, number_of_k_to_scan)  # init 0.134
```
  
3)  
``` python
current1 = np.linspace(0.47969, 0.47969, number_of_k_to_scan)  # init 0.47969  
current2 = np.linspace(-0.1149, -0.1149, number_of_k_to_scan)  # init -0.1149  
current3 = np.linspace(0.10, 0.16, number_of_k_to_scan)  # init 0.134
```

## Low energy
[Logbook link](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3623828)

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
```
current1 = np.linspace(0.42, 0.49, number_of_k_to_scan)  # init 0.47969
current2 = np.linspace(-0.1149, -0.1149, number_of_k_to_scan)  # init -0.1149
current3 = np.linspace(0.134, 0.134, number_of_k_to_scan)  # init 0.134
```
  
