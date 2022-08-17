##  Comparing with old BTP model

The better way of computing the multipole field component can be found here: [[Multipole component model from injection]]

BTP Stray element
https://gitlab.cern.ch/acc-models/acc-models-tls/-/blob/2021/psb_extraction/btp/BTP.ele

https://gitlab.cern.ch/acc-models/acc-models-tls/-/blob/2021/psb_extraction/btp/BTP.seq

Having a look at the old model used for BTP. It is composed of 233 thin multipole inserted at the end of the transfer line.

### Theory:
$$
B_{y}(x,y) = B_{0} + B_{1}x + B_{2}\frac{1}{2}(x^{2}-y^{2}) + B_{3}\frac{1}{6}(x^{3}-3xy^{2})
$$

where

$$B_{i} = K_{i}B\rho$$
#### In the old BTP model, we have $K_{0}, K_{1}, K_{2}, K_{3}$

$$ K_{0}L = \frac{B_{0}L}{B\rho} $$

where $$ L = \frac{totalLength}{\# elements} $$

So to extract the pure $K_{0}$, I divide by L


#### For **tracking**, we get the field components so I divide by $B\rho$

$$ B_{0} = K_{0}B\rho $$

$$  K_{0} = \frac{B_{0}}{B\rho} $$

The $K_{1}$ was computed using two tracks and:

$$ K1=\frac{\frac{\Delta By}{\Delta x}}{B\rho} $$

The K0*L component as a function of s looks like this

![](https://codimd.web.cern.ch/uploads/upload_9dce5ef2f0911b01a2f047ba161e9ae4.png)


Plotting the By as a function of z for the tracking at injection looks like this.

![](https://codimd.web.cern.ch/uploads/upload_5f1c6d5fb81b997e58805624b256165e.png)

Comparison with Adobe Annotator (wrong):

![](https://codimd.web.cern.ch/uploads/upload_15f50f45337b7253b599ff4609b3cb2c.png)
![](https://codimd.web.cern.ch/uploads/upload_1de486a054596a574a221329bf2c4a0e.png)

#### Start point for comparison
The old model and tracking do not start at the same point so I need to calculate the difference in length s.

s = 123.284 mm

Source code: https://gitlab.cern.ch/eljohnso/btp_stray_elements/-/blob/2918a30ffbbd3da15bd5a0abe2ccfb50fe600f04/points_faisceaux_visualizer.ipynb

![](https://codimd.web.cern.ch/uploads/upload_fe629758d59d8ec4b981da7aff10ca00.png)


#### Comparison with geode points **T-type** magnet:
Source code: https://gitlab.cern.ch/eljohnso/btp_stray_elements/-/blob/75dffbed5fb5680d56fa1b7c001bf574d6bbe8d1/plot_B_field_from_tracking_angles_from_geode.ipynb

Because the old BTP model in on a straight line and the tracking follows a curve, here we are basically looking at the difference between bent and straight.

![](https://codimd.web.cern.ch/uploads/upload_862699cab368d8ccd5f7e0ddccde55f9.png)
![](https://codimd.web.cern.ch/uploads/upload_feb13466f30781dce5a9751f0f411431.png)

#### Comparison with geode points **U-type** magnet:
Just for a sanity check. Of course this isn't the correct magnet type.

![](https://codimd.web.cern.ch/uploads/upload_198fc84acf64fc18d0627d39c599673c.png)
![](https://codimd.web.cern.ch/uploads/upload_d8c6f9449ec004d674ca51c1feb034a7.png)


I seem to have made a mistake. I took from here that:
https://edms.cern.ch/ui/file/2140704/2/note_magnetic_model_jra_v_1.0_docx_cpdf.pdf
![](https://codimd.web.cern.ch/uploads/upload_d7cc5cd599cc2631c0b43319e3935a34.png)

but I'm pretty sure that open is defocusing and closed is focusing. This would explain the difference when comparing with the multipole comparison.

To prove this, 

https://edms.cern.ch/ui/#!master/navigator/document?D:100523609:100523609:subDocs
![](https://codimd.web.cern.ch/uploads/upload_59169ffabff69b0217d371d2ae624fe6.png)

https://edms.cern.ch/ui/#!master/navigator/document?D:100523631:100523631:subDocs

![](https://codimd.web.cern.ch/uploads/upload_9af5fc2a40c88edb8e6c537c220c5a10.png)

https://indico.cern.ch/event/321796/contributions/1702330/attachments/621867/855649/PS_MagneticModel2014_Final4.pdf
![](https://codimd.web.cern.ch/uploads/upload_fd0fc73116e31fa3d5b1cf212d60a150.png)
