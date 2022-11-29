https://madx.web.cern.ch/madx/releases/.MADXCourses2022/

## Macro

not functions

they are **text substitution** in your code

LISP and FORTAN are the oldest codes

when you pass stuff into a macro it takes it as a string so if you pass -3.5 it will take 

Careful with **cases**. Identifier are converted to lower case but strings are not converted.

Careful with **pair brackets**

**$** signes are converted to integer **literals**

option echomacro (This will show the substitution of the macro)

If you have mutlitple variable the substitution runs left to right and you might substitute *multiple times* things and erase variables

Naming convention (because everything is global): macroname.__varname

Exec is the only way to use line in a loop (it doesn't work in a while loop)


%g to output a float as an integer if it's an integer


## Special

Memorize commands
tw : twiss betx=1, bety=1;
exec tw; ! rerun the twiss command

multipole don't have length so you can't specify a length

50Hz ripple of the power converters
qf k1 := k1.qf + k1ripple.qf * sin(k1freq.qf * tr$turni) ;

To check if an element is already sliced, you can check the length of the elements

rbarc True/False is to specify if it's a sbend of rbend and you specify the length of the arc

## Generative

option echo, everything in my script will be replicated in the terminal

Redirect option, you can echo to a file and then load the echo

beta block: optics condition of the beam at this place

save.beta(): macro to save the beta block

## Tables

Calculate the size of the beam

copytable

# Lattice Intermediate

Dispersion suppressor (DSS)

# Optics Intermediate

Note: there is a bug if the phase advance inside a magnet is more than pi/2, because the code converts things more then pi/2 by trigonometric rules. The solution is to slice.

beta* is the beta at the location of the IP
L* is the length from the IP at which we can start to add elements

LHC superconductive magnets has strong hysteresis (switch branch of histeresis with changing dI/dt direction)

beta block is a data structure

write phase advance in terms of angles

When you do a twiss on a range, you need to specify the initial conditions (beta0)

Important when matching is to put lower and upper limits

You can do the heavy calculation once and save all the output of MAD-X in a file
truncate erase the content of a file
.4g you specify that the power supply has a limit in the precision

assign echo = terminal; means you close the previous file were you wrote your output and start rewritting to the terminal

## IP design

symmetric, doublets
asymmetric, triplets

matching and changing the length of the drift (position of the magnets)

# Miscellaneous

Save the seed

Jacobian = how things vary in a linear way

matching does a twiss at each step and changes by a small amount a quantity

phase advance only has a sense in normalized plane

use chrom option to calculate chrome if you think that your planes are coupled.
(otherwise it uses the non nomrlizde phase space ellipse which is wrong to compute the chroma if planes are tangled)

vlength = True, does a use before every twiss during a match

Check of aperture is only at the begining, you can use monitor to check aperture
if you want to check the aperture in a bend not only at the begining you can slice it to check multiple time inside

You use **thick** not to have to rematch the optics

The physics is only true in the middle of the drift

