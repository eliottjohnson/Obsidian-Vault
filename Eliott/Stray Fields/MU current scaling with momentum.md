# Current scaling with momentum

from my repo

| Name      | Kinetic energy (T) [GeV] | Momentum p [GeV/c] | Current [A] |
| --------- | -------------------- | ---------------- | --------- |
| Injection | 2.01                 | 2.8              | 533       |
| East      | 23.08                | 24               | 4642      |
| LHC       | 25.48                | 26.5             | 5386      |

Transfer function from Miro
![[transfer function B over I to I.png]]

Miro suggest that a 14 GeV/c momentum is somewhere between 2.48-2.49 T/A

Magnetic rigidity
https://en.wikipedia.org/wiki/Rigidity_(electromagnetism)

$R=B\rho=pc/q$
* B magnetic field
* *$\rho$ gyroradius of the particle due to this field
* p momentum
* q charge

if the particle momentum, p, is given in GeV/c, then the rigidity is in Tesla-metres $B\rho=3.3356pc/q$
or
$B\rho \text{ [T m]} = \frac{1}{0.29979}\cdot p \text{ [GeV/c]}$


use this to compute the integrated field needed in a main unit to deflect the nominal deflection angle $2*\pi/100$ at 14 GeV/c


