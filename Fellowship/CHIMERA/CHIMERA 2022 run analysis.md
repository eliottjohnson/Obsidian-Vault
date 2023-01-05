# PS beam energy

Introduction:

-   Briefly explain what an accelerator is and its importance in scientific research
	- An accelerator is a type of machine that uses electromagnetic fields to accelerate charged particles, such as protons or electrons, to high energies. These particles are then directed through a beamline and used for various scientific and industrial purposes, such as colliding with other particles to study their properties, or producing medical isotopes for imaging and cancer treatment. Accelerators are important tools for advancing our understanding of the fundamental nature of matter and the universe. They are also used in a wide range of applications, from nuclear physics and high-energy particle physics to materials science and medical research.
-   Introduce the concept of beam energy and its significance in the operation of an accelerator
	- Beam energy refers to the kinetic energy of the charged particles in the accelerator beam. This energy is directly related to the speed of the particles, and it determines their ability to perform a given task, such as colliding with a target to produce new particles or reaching a certain depth in a material to be studied. The beam energy is an important parameter in the operation of an accelerator, as it must be carefully controlled to achieve the desired results in a given experiment or application. For example, in particle physics experiments, the beam energy must be precisely tuned to produce the desired particle collisions and allow for accurate measurement of the resulting particles. In medical applications, the beam energy must be carefully controlled to ensure that the particles deposit their energy in the right location and with the right dose to produce the desired effect.

Body:

-   Discuss the various methods used to control beam energy in an accelerator, such as:
    -   RF cavities
	    - The principle behind RF cavities is that an oscillating electromagnetic field can transfer energy to charged particles as they pass through the cavity. By carefully controlling the frequency and amplitude of the RF field, the beam energy can be increased or decreased. This is achieved by using a high-power RF amplifier to generate the electromagnetic field, and by adjusting the phase and frequency of the RF signal to match the phase and velocity of the particles in the beam. The beam energy can be increased by applying a RF field that is in phase with the particles, and decreased by applying a field that is out of phase with the particles.
    -   Magnetic fields
	    - The principle behind using magnetic fields to control beam energy is that a charged particle moving in a magnetic field will experience a force that is perpendicular to its direction of motion. This force will cause the particle to change direction, and its kinetic energy will be conserved. By carefully arranging the magnets in the magnet lattice, the beam energy can be increased or decreased by changing the curvature of the particle's path. This is achieved by adjusting the strength and orientation of the magnets, as well as the particle's injection energy and trajectory.
-   Explain the principles behind each of these methods and how they are used to control beam energy
-   Discuss the challenges and limitations of these methods, and how they are addressed in the design and operation of accelerators

Conclusion:

-   Summarize the main points of the article and the significance of controlling beam energy in an accelerator
-   Discuss potential future developments in this area, such as new methods or technologies for beam energy control.

## Some intro about how it is defined, including the lookup tables

See [[Pb ion lookup table]]

[Source code: read_bfield_pickles.ipynb](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/read_bfield_pickles.ipynb)

This plot shows the variation around the mean magnetic field


![[variation_b_field_chimera 2.png|1300]]

![[average_b_field_chimera 1.png|500]]

![[hist_b_field_chimera 2.png|375]]

![[energy_scan_chimera 1.png|475]]

![[energy_scan_timestamp_chimera 1.png|475]]


## The nice colour showing which energy was used during each moment of the test

[Source code: gain_vs_xion.ipynb](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/gain_vs_xion.ipynb)
![[Pasted image 20221130110611.png|775]]

# Beam intensity

The RFKO technique, or radio-frequency knockout, is a method used to control the beam energy in an accelerator by using RF cavities and magnetic fields in combination. This technique allows for greater precision and flexibility in controlling the beam energy, and it is commonly used in advanced accelerators.

The RFKO technique involves using an RF cavity to accelerate the charged particles in the beam to a high energy, and then using a magnetic field to bend the trajectory of the particles and reduce their energy. This is achieved by carefully adjusting the RF field and the magnetic field to match the phase and velocity of the particles in the beam. The RF field is used to increase the beam energy, and the magnetic field is used to decrease the beam energy. By carefully controlling the strength and orientation of the magnetic field, the beam energy can be precisely controlled and fine-tuned to produce the desired results.

The RFKO technique offers several advantages over other methods of beam energy control. It allows for greater precision and flexibility in controlling the beam energy, and it can be used to accelerate a wider range of particles. It also allows for a smoother transition between high and low beam energies, which is important for certain types of experiments or applications. Overall, the RFKO technique is a powerful tool for controlling the beam energy in an accelerator, and it is widely used in advanced accelerators around the world.


Beam intensity, or the number of particles per unit time in an accelerator beam, is an important parameter in the operation of an accelerator. It determines the rate at which the beam can perform a given task, such as colliding with a target or delivering a dose of radiation. In this article, we will discuss how beam intensity is controlled using the RFKO technique, which combines the use of RF cavities and magnetic fields to achieve precise and flexible control of the beam energy. The RFKO technique offers several advantages over other methods of beam intensity control, and it is widely used in advanced accelerators around the world.

## RFKO and gain settings throughout the test

[Source code: rfko_gain_analysis](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/rfko_gain_analysis.ipynb)

![[Pasted image 20221130103506.png|950]]

![[Pasted image 20221130103511.png|350]]

## Intensity measurements on SEC and XION, including intensity vs. gain

[Source code: gain_vs_xion.ipynb](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/gain_vs_xion.ipynb)

![[Pasted image 20221130110629.png|825]]


## RFKO

Time structure

[PS logbook entry: RFKO time structure](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3657771)

![[Pasted image 20221130111711.png|375]]

# Spill time profile

## Gas scintillator, SEC, XION, etc.

[Source code: gain_vs_xion.ipynb](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/gain_vs_xion.ipynb)
![[Pasted image 20221130110602.png|400]]

[PS logbook entry: spill and rfko gain changes](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3656662)

![[Pasted image 20221130111829.png|425]]

### How does the spill shape change with gain setting ?

Most used gain
![[Pasted image 20230105152806.png]]

Code: https://swan005.cern.ch/user/eljohnso/notebooks/SWAN_projects/quad-scan-east/spill_time_profile_chimera.ipynb

![[Pasted image 20230105145930.png]]

![[Pasted image 20230105145935.png]]

![[Pasted image 20230105145941.png]]

# Beam spatial profile

## MWPC

-   Independence of beam profile with beam intensity, impact of energy on the beam shape, “explanation” of the dips (i.e. comparison with and without Montract), etc.

![[Pasted image 20221130111920.png|600]]

* make a plot of the MWPC beam size before and after my quadrupole scan to see if there is a change in beam size to confirm.


### CHIMERA quadrupole scan

[PS logbook entry: CHIMERA quadrupole scan](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3659020)

[[MWPC ion quadrupole scan]]

### Dispersion measurement on the East Dump with the ion beam

During the CHIMERA nov run 2022 we changed the B-field from 2500 to 2600 G and we observed the shift in position of the beam.

It moves to the left by ~20 mm. We see the beam movement because the bending magnet to the east dump do not scale with momentum. Also the beam size $\sigma$ shrink, as expect at higher energy, from 9.58 to 8.47 mm.

[PS logbook entry: CHIMERA quadrupole scan](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3659020)
2500 G
![[Pasted image 20221209160140.png|475]]

2600 G
![[Pasted image 20221209160220.png|475]]