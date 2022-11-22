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
if the beam is off centered, the taylor expansion might be inacurate and you shouldn't 