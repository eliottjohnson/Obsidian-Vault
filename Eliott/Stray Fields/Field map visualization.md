# Field maps visualisation

## By as a function of x
Dipole component as a function of the transverse coordinate (x)

[Commit: script and plots to show By as a function of x](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/commit/953724ca613f11c376864979f7f4d8839e98fa3f)

[Source code: check_field_maps_faster.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/953724ca613f11c376864979f7f4d8839e98fa3f/ps_injection/kick_response_injection_tracking/check_field_maps_faster.ipynb)

This is a U-type magnet at 24 [GeV]. First Defocusing (D), then Focusing (F).
Pay attention to the x-axis between top figure and bottom figure.

We observe that it is not linear. The 
/**quadrupole component isn't constant**
. By is not a straight line, it's curving. The gradient accross the beam isn't constant, the further away from the magnet you get a different focusing/defocusing effect.

![](https://codimd.web.cern.ch/uploads/upload_f75a5c824c0cca94c2550a4c3727ff87.gif)

### Focusing
![](https://codimd.web.cern.ch/uploads/upload_8f00122df745b0f56efa0e12bff35a24.png)
### Defocusing
![](https://codimd.web.cern.ch/uploads/upload_d2fa4d68553ca46b74de779681ba39f6.png)

![](https://codimd.web.cern.ch/uploads/upload_bd985c65094c9cefcab6bc1eb4a265f7.png)

$$ \boldsymbol{G}(x_{j},z) = \frac{\Delta\boldsymbol{B}}{\Delta x} = \frac{\boldsymbol{B}(x_{i+1},z) - \boldsymbol{B}(x_{i},z)}{x_{i+1}-x_{i}} $$

Fieldmap            |  Master thesis
:-------------------------:|:-------------------------:
![](https://codimd.web.cern.ch/uploads/upload_7c14fb0d3a048f47a36916302917eb2d.png) | ![](https://codimd.web.cern.ch/uploads/upload_9ad77e9291afd6b5c79decc91f613400.png)

[Source check_field_maps_faster.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/0715d511bcd1a957f56eecc2450e86ee58437c12/ps_injection/kick_response_injection_tracking/check_field_maps_faster.ipynb)
![](https://codimd.web.cern.ch/uploads/upload_c0a2254a2fab94d37cafd43169aad7ed.png)


[Source check_field_maps_faster.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/ef4150c259f8fe5d9c19d5073e40b6040a40ea0a/ps_injection/kick_response_injection_tracking/check_field_maps_faster.ipynb)


![](https://codimd.web.cern.ch/uploads/upload_ed7a2a841aa6d9f339cce9323bd7e81d.png)

![](https://codimd.web.cern.ch/uploads/upload_ef4641ae58e761fc73db4e97859206f1.png)

![](https://codimd.web.cern.ch/uploads/upload_5190a7439b907ed35571ea24db5d64ba.png)


Linear region for main unit fields is +-10 [cm]
![](https://codimd.web.cern.ch/uploads/upload_aff47c363bb3a007a537fbcd350c3b8f.png)

Rotating 3D dipole component

![](https://codimd.web.cern.ch/uploads/upload_550cb701c37f258596b4df2ca1fc6e17.gif)

## Bx as a function of y

![](https://codimd.web.cern.ch/uploads/upload_b34a715ec77f6535c0c1209c6cdcf102.gif)

### Focusing
![](https://codimd.web.cern.ch/uploads/upload_3bfcfdd4b3f81d69440805c3376b0016.png)

### Defocusing
![](https://codimd.web.cern.ch/uploads/upload_a83e32a3d600f96d0124630522842fac.png)

![](https://codimd.web.cern.ch/uploads/upload_14927a0b93de77d47e9249f6fec84313.png)

![](https://codimd.web.cern.ch/uploads/upload_d4cbc9bd0c7431ffa8fe930450a71baf.png)


If I zoom in we see that the gradient is ~+-4.3 which is the same as for the By(x) in the center
![](https://codimd.web.cern.ch/uploads/upload_b04c20688bb78ee399d633a9545afae3.png)



![](https://codimd.web.cern.ch/uploads/upload_43a3048fc2af7f3ffcad887b4408dea0.gif)

3D Gradient
![](https://codimd.web.cern.ch/uploads/upload_ec03c32430e3b4a842346a6e4d6c26ae.png)


Small tool to interactively show the fieldmap
[Source code: check_field_maps_interactive.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/7b26865fd85dcaec5a853588627dd9b80414ade5/ps_injection/kick_response_injection_tracking/check_field_maps_interactive.ipynb)

![](https://codimd.web.cern.ch/uploads/upload_8bdf71c980251838bf075c43ba2c6b62.gif)


[Source code: check_field_maps_faster.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/953724ca613f11c376864979f7f4d8839e98fa3f/ps_injection/kick_response_injection_tracking/check_field_maps_faster.ipynb)
![](https://codimd.web.cern.ch/uploads/upload_d87fe1990bce0e2f66f5a9ee3ef5e99f.png)
![](https://codimd.web.cern.ch/uploads/upload_ac2685a3d345f13fa9fc4be236541d54.png)
![](https://codimd.web.cern.ch/uploads/upload_26b3dfcfd44038bb64cdbb4ef3234a0d.png)
![](https://codimd.web.cern.ch/uploads/upload_28e99bc7f9547882a675aa20aec1eee9.png)
![](https://codimd.web.cern.ch/uploads/upload_5ba1ac238ec46c9f7f45ac73cafd04c4.png)
![](https://codimd.web.cern.ch/uploads/upload_9009f2564eb8b32a445f8abf0f45581f.png)
![](https://codimd.web.cern.ch/uploads/upload_9c8794e570241fa884e20f469804b1e2.png)
![](https://codimd.web.cern.ch/uploads/upload_52e16dbced753212b4e942046a65836b.png)
![](https://codimd.web.cern.ch/uploads/upload_2a08c09e2514a52103723897b4b5e32c.png)
![](https://codimd.web.cern.ch/uploads/upload_84ba8b93c3e91090d29a9517f04e1b30.png)
