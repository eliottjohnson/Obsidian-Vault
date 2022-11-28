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