[Source TI Handbook](https://www.ti.com/seclit/eb/sgzy002a/sgzy002a.pdf)

* Radiation impacts semiconductor in three ways:
	1) Single-event effects (SEEs)
	2) Dose effects
	3) Dose-rate effects
		* induced by detonation of a nuclear weapon (generate high-intensity pulse of gamma radiation and neutrons)
		* high flux of ionizing radiation produces photocurrents that can temporarily overwhelm on-chip power supplies

## Destructive and non-destructive single-event effects

### Non-destructive SEEs (soft errors)
* Observable event or corruption in an output or data state
* Does not damage or destroy the actual circuit component
* If combinational logic or analog circuits with no memory:
	* Disruption is **transient and self-recovering**
	* Circuit functionality returns after a short duration once the excess charge in the struck junctions has been removed
* In memory component
	* Radiation event can change the data state of the erroneous state
	* Data is erroneous and persistent until the subsequent overwrite of the data
	* No damage to the device, only the **data is corrupted**

#### Single Event Transients (SETs)
* Occurs when an energetic ion traverses an electronic device (if it has enough energy to reach the semiconductor substrate where the active device is place)
* The ion leaves a high density of ionized excess **electron-hole (e-h) pairs** (charge carriers) in its wake
* Restorative mechanisms
	1) Carrier recombination
#### Single Event Upsets (SEUs)
#### Single Event functional interrupts (SEFIs)
#### Single Event Latchups (SELs)
	* Max current is limited such as permanent damage does not occur

### Destructive SEEs (hard errors)

* Can be the same effects as from soft errors but the device is permanently damaged or destroyed

Power electronics errors (higher operating currents and voltages)
#### Single Event Latchups (SELs)
#### Single Event Gate Rupture (SEGR)
#### Single Event Burnout (SEB)
