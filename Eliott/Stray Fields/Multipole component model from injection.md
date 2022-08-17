# Multipole component model from injection

This is a new way to compute the multi-component field model. The old one can be found here:  [[Comparing with old BTP model]].

[Source code: multiple_field_component_injection.ipynb](https://gitlab.cern.ch/eljohnso/btp_stray_elements/-/blob/master/multiple_field_component_injection.ipynb)

![](https://codimd.web.cern.ch/uploads/upload_f8607a95938e477239154d93d702dc06.png)

![](https://codimd.web.cern.ch/uploads/upload_37731b58b053f2536ff9bc9af3b6ae5a.png)

Different order of fit
![](https://codimd.web.cern.ch/uploads/upload_65bee1feef51b4805fcc3e7ec69a7244.png)

Dipole
![](https://codimd.web.cern.ch/uploads/upload_e25a0b90315228c88d9b5c5ba4833ed3.png)
Quadrupole
![](https://codimd.web.cern.ch/uploads/upload_abb8108d64abb68122344719d09d1a9d.png)
Sextupole
![](https://codimd.web.cern.ch/uploads/upload_81e3122365c251a8869472fa01c4676d.png)
Octupole
![](https://codimd.web.cern.ch/uploads/upload_df8cf522ff7c62bddeaf6d54e48d6d90.png)

Now with **interpolation** we get rid of the steps in the functions

![](https://codimd.web.cern.ch/uploads/upload_76a934b03940ef96a086ccbaa04929d0.png)

Longer transverse probing. Should look at width of beam pipe.
![](https://codimd.web.cern.ch/uploads/upload_0c5a1c6b5e07d5a72d51d039d976812d.png)

Dipole (x-check: same field a felt during tracking)
![](https://codimd.web.cern.ch/uploads/upload_a9ddf30c5694eea1438508d51e97cda6.png)
Quadrupole
![](https://codimd.web.cern.ch/uploads/upload_ed98ca8ffdeed7a27057e1a64592befb.png)
Sextupole
![](https://codimd.web.cern.ch/uploads/upload_a4c45d127b082fb725d047f546e6e6e2.png)
Octupole. Did they forget to put the coefficient on the octupole component ?
![](https://codimd.web.cern.ch/uploads/upload_6a7a2ee3622faca8e7b0a7b7e44fd8d0.png)

Multipole components are perpendicular to track (to be checked at extraction with sign of sin/cos). Tried with very low momentum.
![](https://codimd.web.cern.ch/uploads/upload_85b48b31c2053b68acca8601bd7be677.png)

Comparison between deflected and not deflected

![](https://codimd.web.cern.ch/uploads/upload_92beeba063e62ead0f5546f504281ac8.png)

Small difference when using s instead of z because of the small angle
![](https://codimd.web.cern.ch/uploads/upload_0c79805112262a17ede6dd909b6a41fb.png)

