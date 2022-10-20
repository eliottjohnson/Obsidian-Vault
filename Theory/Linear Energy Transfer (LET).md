[Source: Texas Instrument Handbook](https://www.ti.com/seclit/eb/sgzy002a/sgzy002a.pdf)

* LET is a function that provides the energy loss **per unit length**
* LET is strongly non-linear as a function of particle energy
* units:
	* $MeV cm^{2}/mg$
	* $MeV/mm$

* As the iron ion loses kinetic energy, it moves more slowly and has more time to generate more charge through more interactions with matter through which it is traversing.
* LET peaks at low energy also called **Bragg peak**
* Blue line is the range an ion travels in the material and thus the amount of material required to stop an ion at a particular kinetic energy.
	* i.e. with zero kinetic energy, an ion needs zero material to be stopped and does not an issue for device reliability

LET and range are **statistical in nature**
Variation is known as **straggling**

![[Pasted image 20221020144418.png]]

* If shielding is not thick enough to completely stop a particle it will reduce the particle energy
	* This will increase the LET => more radiation induced charge
* For microelectronics LET is a direct measure of an event's ability to upset these device
* SEE are largely dependent on the LET
	* microelectronics have areas extremely sensitive to charge injection
* For heavy ions: Stopping power = LET
	* Stopping power considers all energy-loss mechanism:
		* radiative energy (Bremsstrahlung)
		* delta rays production (secondary electrons)
		* creation of atomic defects
* LET varies as a function of particle:
	* energy
	* type (proton, electron, ligh ion, heavy ion, etc...)
	  material through which particle is travelling

Simulation of 1,000 50-MeV iron ions incident (from left) on a silicon target.
Each ion has a unique path defined by random multiple interactions with target nuclei and electrons.
Each interaction reduces the ion energy by a small amount and can change its trajectory.
Ultimately, all of the ions were “stopped” or absorbed.
![[Pasted image 20221020145907.png]]