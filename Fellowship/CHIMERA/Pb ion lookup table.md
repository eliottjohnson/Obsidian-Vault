See [[Current scaling for Ions]] for the excel spreadsheet
See [[Ions theory]] for some info on number of electrons, etc.
See [[Ion kinetic energy]] for the theory behind the Pb ion lookup table

[Source code: ion_kinetic_energy](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/ion_kinetic_energy.ipynb)

![[kinetic_energy_lookup_table_zoom_B_field 1.png|1425]]

Chimera
![[Pasted image 20221215162111.png]]

### PS B-field in Gauss to Ekin/nucleon

```python
B = 3102
Ekin = (193.737692/208)*(np.sqrt(((1/((3.3356/(70.0789*54)*10000)/B))/193.737692)**2+1)-1)
print(Ekin)
```


The ramp on POPS [[Cern Control Center Tips and Tricks#Change the B-field of the PS]] changes the energy of the ions
[Logbook entry](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3635313)

![[Pasted image 20221018111720.png|725]]

