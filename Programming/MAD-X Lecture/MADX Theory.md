https://madx.web.cern.ch/madx/releases/.MADXCourses2022/

Laurent Deniau

Symplectic, conserve energy (no energy drift)

5d = dp energy deviation


To save the output to a file:
.\madx-win64-gnu.exe madx_test.madx > my_script.out


### **Show** command

show a;
show sbend;
show twiss;

Tell you all the variable the commands take.

Re matrix = First order matrix

Xsuite

case insenstive (no difference between upper case and lower case)

Variable by default set to zero

### Lexemes

comments:
!
//
/* */

Numbers:
Only double precision floating point
+3.5e5

regex

Maximum 46 characters for a variable name

Denormal number makes the cpu go into a special mode and takes the calculation way longer

## deferred expersionn

If you change a value, everything is calculated from it

c :=3*b 

command:
	drift
	return
factories:
	sequence
	drift

Special constructs;
	if
	elseif
	else
	while
	line
	macro

The dot "." is part of the identifier, in the LHC it is a separator.


numerical instabitiy when converting 60 deg to radian (with raddeg)

Only number can go into a variable, (not a=True;) while not work

different operator <>

Operators only have one argument

* random distribution ranf()
* gauss()

deferred expresssion is like a lambda function is python

If you store a number, use "="
If you store an expression, use ":="

### Changes the seed:
eption, seed=123456789;

the global seed is 123456789

### Commands

option -info # False
option info # True

(option +info is wrong)

value, option->info

### Factories

context:

sequence ... endsequence

You cannot create subsequences inside the sequence (not reetrant)

bvflag, reverse the direction of the beam

use, computes the position of the elements

tfs tabular field separated

Use places the implicits drifts DRIFT_0, DRIFT_1

dumpsequ to see the negative drift

# Sequences

kmin, kmax

focusing: +
defocusing: -

Optic file: strength file
Working point of the machine

Define the errors last because any use will remove the errors

Add length around magnets with l.de


From the top, going right is positive


In survey, the crosses are the **end** of the element. We always dump at the end of the element.

Survey plots the machine from below

Angle convention is positive move to the right

When you install a element in a sequence and you place it with from. Default is center.
but you can refer = entry.

Length of sequence is the position of the end marker

Drifts shorter than 1 $\mu m$ are discarded

# Optics

Transfer line need initial parameters. Closed machine tries to find a closed solution.

Field which is a potential can be expressed as a series.

Magnetic rigidity, $B\rho = P_{0} / q$ related to the radius of curvature

Strength (k) means the optics scales with the machine momentum (high and low energy)

sbend: k = theta/L
If you want a dipole turned off, put 10e-12 not zero otherwise it replaces it with k0=angle/l

quadrupoles:
if the beam is off centered, the taylor expansion might be inacurate and you shouldn't eoffset the quadrupole but rather recompute the expansion.

$\Delta pt$ momentum deviation

optics is 5D, tracking is 6D

Dispersion is variation of orbit vs varation of energy

At pi there is no phase advance, no solution. So pi/2 you should not use even number of cells.

FODO cell, focus the beam
sbend, bend the beam

q1 horizontal tune
q2 vertical tune

tune is expressed in unit of 2pi

One cell is a FODO cell
A high tune, your machine is reactive but unstable
Low tune, machine is stable but not reactive.

We try to maximise the length of bending magnets because the longer the magnet, the less the bending and the less the sychrotron radiation.

Dipole has focusing effect on horizontal plane

Interpolate when you plot slice the elements and recalculates the twiss

## Matching

Matching the phase advance of the cells

step is only the initial step. After it'scomputed by the jacobian

units of 2 pi
lmdif calls = 20 is the name of the algorithm

tolerance is the square of the constraint

First we match the quadrupole, for the linear part and the transport
Then we match the sextupole to correct the chroma (change of tune with respect to energy)

global parameter of the sequence dq1

You can combine 5 sextupoles to correct 4 order, octopolar term

Touching the sextupole is fully orthogonal to the linear part (the quadrupol to change the tune)

## Errors

Micado optimises the numbers of kickers

Corrects horizontal plane and then vertical plane

mlist list of monitor

kick strength is the sum of the kick and svkick

## Tracking

Thin lenses

makethin converts your sequence in thin lenses

start position depends if onepass or not onepass (around design orbit or not)

in the starting condition you can specify the time, this is useful for the RF

You can do something that changes after each turns
simulate a ripple, tr$turni x 50Hz in the deferred strength of your ripple

Never go below 3 slices

**simsumrule**  (to lookup online) correction on the boundary teapot

slices: teapot 4-5-6
continuous is a waster of calculation except if:
	injecting fields errors inside a quadrupole it's a good idea to slice the magnet and insert a multipole

