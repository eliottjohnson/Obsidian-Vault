
## Slow extraction

[Chiara's ABTEF Talk](https://indico.cern.ch/event/1198785/)

Slow extraction requires a mechanism to move the beam into the resonance:
* Sextupoles to excite the resonance Q = 1/3
* Particles are slowly pushed into the resonance and gain amplitude
	* Once at high amplitude, particles are kicked by a septum

### Phase space

There are two region in phase space:
* The **stable** region (inside the triangle)
	* In the center, the invariants of the motion are **unperturbed ellipses**
	* At bigger amplitudes the ellipses take on a **triangular shape**
* The **unstable** region (outside the triangle)
	* The particle "lock" onto 3 separatrices and increase in amplitude as they move from one separatrix to the other
* How the beam is moved across the last stable triangle into the unstable region determines the length and quality of the spill

![[Pasted image 20221027115546.png|425]]

## Steinbach Diagram

The **Steinbach diagram** shows the beam and resonance in amplitude-momentum space, where the amplitude $A = \sqrt{\epsilon}$ is computed from the particles emittances.

* The large grey arrows indicate:
1) The motion of the beam into the resonance
2) The outward movement of the unstable particles that form the spill

* The resonance appears as a "V"-shaped region centred on the resonant tune.
* A particle will be stable if its emittance is smaller than the acceptance of the stable triangle.
![[Pasted image 20221027115722.png]]

## Spiral step
https://cds.cern.ch/record/2650734/files/CERN-THESIS-2018-278.pdf
Particles which are on one arm of the separatrix in one turn will be on the counter clockwise rotated arm in the next turn. Particles return to the same arm every three turns, but always a little further from the middle than earlier. If we track the phase space position of one unstable particle it seems like if it were “walking” outwards with increasing steps. The so-called spiral step is an important parameter of the slow extraction. Assume a particle which is just barely on the circulating side of the wires in one turn, then three turns later it is the extracted particle which is furthest away from the origin. The difference between the particle’s x coordinates in this turn and 3 turns later is called the spiral step. In other words, this is the length of the section on which particles are extracted or lost

## PS Tune control

The tune can be controlled with different quadrupolar elements such as:

* PFW (Pole-Face Windings)
* QSE (Quadrupole for slow extraction)
* LEQ (Low energy quadrupoles)
	* See [[Cern Control Center Tips and Tricks#Trim the tune function with LEQ]]

[[PS Tune control explanation]] from Marc Delrieux

## Transit time

Transit time is the average time a particle takes to escape the triangle and get extracted. If you push all particles at the resonant tune then they will all start with different initial conditions. Some of them will take 100 turns to escape de triangle and some of them will take 1000 turns for example. Particles that are close to the fixed point will take a very long time to move to the separatrices.

An example of a particle in the resonance experiencing transit time: [[Creating a third integer resonance triangle with PTC#Gif of transit time]]

Of course, the transit time is a distribution and if you plot the number of turns when the particle was lost then you'll see a gaussian.

## TFB extraction

Another method of slow extracting is with the Transverse Feedback Blowup.

You have to **not** ramp the B-field (COSE) and then chirp with the Q-meter. The beam has a range of tunes and you have to excite all the tunes for them to be extracted. You need to sweep multiple times (chirp) through these frequencies because every time you pass through it extracts particles that are close in tune and approaches particles that are far away. With a fixed frequency (no chirp) you might extract a small portion of particles.

[**TFB driven SX on EAST4**](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3605176)

In this plot you can see the the frequency of the chirping.
![[Pasted image 20221027113708.png|1000]]


In this plot you can see how it becomes harder and harder to extract particles that are in the core. This is because with a certain gain, you increase the size of the triangle but particles in the centre are hard to extract. You would need to increase the gain as a function of time during the spill to have a constant rate.

![[Pasted image 20221027113837.png]]