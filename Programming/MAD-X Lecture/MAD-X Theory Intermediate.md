https://madx.web.cern.ch/madx/releases/.MADXCourses2022/

## Macro

not functions

they are **text substitution** in your code

LISP and FORTAN are the oldest codes

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

