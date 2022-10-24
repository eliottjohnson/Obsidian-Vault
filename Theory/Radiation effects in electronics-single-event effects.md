
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
	* Data is erroneous and persistant until the subsequent overwrite of the data
	* No damage to the device, only the **data is corrupted**

* Single Event Transients (SETs)
* Single Event Upsets (SEUs)
* Single Event functional interrupts (SEFIs)
* Single Event Latchups (SELs)
	* Max current is limited such as permanent damage does not occur

### Destructive SEEs
