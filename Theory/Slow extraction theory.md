# Slow extraction theory

## Spiral step
https://cds.cern.ch/record/2650734/files/CERN-THESIS-2018-278.pdf
Particles which are on one arm of the separatrix in one turn will be on the counter clockwise rotated arm in the next turn. Particles return to the same arm every three turns, but always a little further from the middle than earlier. If we track the phase space position of one unstable particle it seems like if it were “walking” outwards with increasing steps. The so-called spiral step is an important parameter of the slow extraction. Assume a particle which is just barely on the circulating side of the wires in one turn, then three turns later it is the extracted particle which is furthest away from the origin. The difference between the particle’s x coordinates in this turn and 3 turns later is called the spiral step. In other words, this is the length of the section on which particles are extracted or lost

# PS Tune control

The tune can be controlled with different quadrupolar elements such as:

* PFW (Pole-Face Windings)
* QSE (Quadrupole for slow extraction)
* LEQ (Low energy quadrupoles)

[[PS Tune control explanation]] from Marc Delrieux

## Two ways to trim the tune function

WorkingSets -> Ring -> Normal quadrupoles -> PSBEAM BSW42 POS INJ1 -> Small function editor -> PSBEAM/QX_LEW

LSA App Suite -> Applications -> Settings Management -> Select MD user cycle -> Working Set Select All -> Property Select All -> Device/Property = PSBEAM/QX_LEQ


TFB -> Working -> DUMP + TFB -> CPS:TRANSV-FEEDBACK -> PA.TFB-DSPU-H -> Right arrow (top right) 3rd window.
Start BLU - End BLU 455 - 520
Exce DDS1harmonic should be close to the tune
Exc DDS1gain: ampltitude of the excitation