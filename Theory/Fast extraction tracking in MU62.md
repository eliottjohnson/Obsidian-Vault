# Fast extraction tracking in MU62


[Source code: full_line_with_matrix_from_tracking.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/6f15ce0cacddbc601dfb0761ae8ff69dfb20e64a/ps_extraction/east-fast-extraction/full_line_with_matrix_from_tracking.ipynb)

First part of the code is fast extraction tracking
![](https://codimd.web.cern.ch/uploads/upload_f1465ad0cfed713bdd61a78578bda871.png)

Some good settings would be in MADX entering the MU62:

```
extraction_offset = 0.132 # Roughly 13 cm
extraction_angle = 0.0139626 # 0.80 deg
```

![](https://codimd.web.cern.ch/uploads/upload_6cd121642f51bf3b74e6fb5fce25035b.png)

Built a new function to take pixel coordinates and convert them to fieldmap coordinate. Will be useful for optimizing.

![](https://codimd.web.cern.ch/uploads/upload_8edb061f2b32d54d61f0ce86ae020e97.png)

##### Two scenarios
[Source code: slow_extraction_main_unit_excursion.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/4d7c5c604fa25770f9971e38dbbca9a34fee6ebd/ps_extraction/east-fast-extraction/Check%20scripts/slow_extraction_main_unit_excursion.ipynb)

1) no angle

With an optimizer I find that to be centered at the end of the vacuum chamber you need to be outside at the entry

![](https://codimd.web.cern.ch/uploads/upload_147cb6d8d8dcd53b9519a26d5f569d3d.png)

If I set the boundaries of the vaccum chamber, I can't get center at the exit. That with the largest boundaries, it looks like the aperture is even smaller upstream.

![](https://codimd.web.cern.ch/uploads/upload_6d9cdcbf28602db4f2fe06789580421f.png)


```
extraction_offset = 0.16911142441079288 # Roughly 13 cm
extraction_angle = 0.0
```
![](https://codimd.web.cern.ch/uploads/upload_d49d8dd64a5401d4239c84361738e125.png)

2) Centered but you need to determine angle coming in

With the optimizer, I find that if you're perfectly in the middle of the beam pipe at the entry of MU62, you need to have a ~0.687$^\circ$ angle entering the magnet because of the curvature of the stray field.

![](https://codimd.web.cern.ch/uploads/upload_ebdba6aee99b9570013507dbb6527dd6.png)


```
extraction_offset = 0.132 # Roughly 13 cm
extraction_angle = 0.012
```

![](https://codimd.web.cern.ch/uploads/upload_d978c5c82196b77e6357a1d5b69432d3.png)


Maybe I can optimize with both variables ? More complicated.