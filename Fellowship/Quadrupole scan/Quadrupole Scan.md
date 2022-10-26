# Quadrupole Scan

## Previous measurements scripts

* Yann has done a quadrupole scan in the TL toward the SPS and NTOF
    * His [Gitlab for ntof](https://gitlab.cern.ch/ydutheil/ntof)
    * In particular this code: [analysis.ipynb](https://gitlab.cern.ch/ydutheil/ntof/-/blob/master/analysis.ipynb)
    * ![](https://codimd.web.cern.ch/uploads/upload_1cfa296f68c9ee3f7d08ffe669821b6a.png)

    * Wrote a script that acquires data from 3 shots at each quad setting
    * Also change beam energy to measure **Dispersion** at each setting
        * Basically you **change** the **momentum** of the extracted beam for every measurement and thus the **beam position change**
        * Doesn't change beam size
    * Knob is a few quadrupoles together
    * Beam size is **sigma**
    * **Centroid** is center of beam
    * Horizontal and vertical

* Matthew has done a quadrupole scan for the BTY line that goes to ISOLDE
    *  His [Gitlab for BTY](https://gitlab.cern.ch/mfraser/bty-optics-studies)
    * In particular this code: [bty_gps_analysis_2021.ipynb](https://gitlab.cern.ch/mfraser/bty-optics-studies/-/blob/master/bty_gps_analysis_2021.ipynb)
    * Where you **scan** a knob (K or current, same thing) and look at beam size at one or more BTVs. You then **match** the initial parameters to try to match the measurements. ![](https://codimd.web.cern.ch/uploads/upload_975e6deb964dc3fe22c8e7a5317e0e72.png)

* Some thing to consider is to see **minimums** at the BTV
    * On Matthew's measurement there is a minimum on BTY.BSF but **not** on GPS.BSF
    * This can be done with MAD-X to get an idea what quadrupole to change to see minimums


* To **match** you then use a scipy minimize function to try out different initial conditions (ex, ey, dpp) and fit the MAD-X model to the data.

* [BTP Quad scan scripts](https://gitlab.cern.ch/mfraser/btp-quad-scan)

    * The BTP script is coupled to the PS so it complicates the data acquisition: I have to subscribe to the PS device and grab the PSB data by changing the timing selector
    * When coupled with the PS we change the beam energy slightly differently (check the frequency set variable)
    * The BCT check is set to negative to all intensities pass
    * I hardcode noSet = True so nothing is set to the machine right now
    * I added a json read output and it seems to work OK… you need to pull the latest version of pybt for this to work as I found some bugs with data frames
    * Need to check all the details of the code to make sure  it works OK, we can do that with beam soon, next week or the week after.
    * I added also the BTM line (not coupled to the PS) here we can set up and test the scripts as the beam goes to a dump via three grids.

### Additional scripts from Yann to Gaussian 2D

Dans AFS:
cd ~ydutheil/public

in AD_BTV_optimisation/fit_btv.py

![](https://codimd.web.cern.ch/uploads/upload_7a4de5cff49390c2844aa877a29e1e32.png)




regarder fitter.py et 

``` python
    btv_data = japc.getParam('FTA.BTV.9064.DigiCam/PMData', timingSelectorOverride='')


    x, y, x_grid, y_grid, dx, dy, extent = ft.BTV_process(btv_data)
    ax_btv.cla()
    cbar = ax_btv.imshow(btv_data['image2D'], extent=extent, origin='lower')

    try :
        fit, fit_err = ft.BTV_fit(btv_data)
    except:
        print('failed fit, skipping')
        keep_waiting = True
        continue

    data_fitted = ft.twoD_Gaussian((x_grid, y_grid), *fit)

    # contours at +- 1 and 2 sigmas
    levels = np.sort(np.exp(-np.array((1, 2)) ** 2 / 2)) * fit[0] + fit[5]
    ax_btv.contour(x_grid, y_grid,
                        data_fitted.reshape(btv_data['image2D'].shape),
                        levels, colors='w')
```
    
## EAST Area

* Start with BTV at the dump and use the two quadrupoles upstream
* Dump can be use as a parallel MD
* BTV12 and the Dump


### Quadrupole strength is T8
Wrote a small script to quickly adjust the strength of quadrupole with current
[Source code: t8_interactive.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/d965034b9406742b7ba4dbaf5a1f4877df20691e/ps_extraction/east-fast-extraction/t8_interactive.ipynb)

![](https://codimd.web.cern.ch/uploads/upload_d94f1233472ea035e4a3dad4deb901c7.gif)


Some settings I'd like to try during the next run
* Small beam size all through the line with optimizer
![](https://codimd.web.cern.ch/uploads/upload_2bdd47591dde40bf660162bdbc7638c6.png)


* Smallest beam size on all BTVs
![](https://codimd.web.cern.ch/uploads/upload_58dc0841c81a63b6605d2ed2f57e640c.png)


* Smallest beam size on BTV096
![](https://codimd.web.cern.ch/uploads/upload_8bcbf8b33a0df74cea02c0701f24ebf1.png)

## Quadrupole scan to the Dump

![](https://codimd.web.cern.ch/uploads/upload_0b174a68c38791ba041dbee6ded726c8.png)

We have **3 Quadrupoles** and **2 BTVs**

![](https://codimd.web.cern.ch/uploads/upload_9348ea27a6adc90f35bf038cc4509ad1.png)

Quadrupole current range (from the working set)

QFN01 -733 to 733 [A]
QDN02 -537 to 537 [A]
QFN03 -421 to 421 [A]

[Source code: quad_scan_east_dump.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/EliottBranch/ps_extraction/east-fast-extraction/quadrupole_scan/quad_scan_east_dump.ipynb)

|  ![](https://codimd.web.cern.ch/uploads/upload_3bba2743c001113110cc7f81e7af9786.png)   |   ![](https://codimd.web.cern.ch/uploads/upload_5fd5a4b024c7236a894701130c5e3e77.png)  |
| --- | --- |

So with the first quadrupole we don't have enough strength to go trough the minimum.


Plot with the aperture restrictions
![](https://codimd.web.cern.ch/uploads/upload_d0b1c7ba7c03809cfb9414dc32806844.png)

![](https://codimd.web.cern.ch/uploads/upload_ffefbcef3a709211a5921a2cb4429969.png)

Scanning the two last quadrupoles on the last btv

| ![](https://codimd.web.cern.ch/uploads/upload_09c146b81252f1fc539ee7d63b09477f.png) | ![](https://codimd.web.cern.ch/uploads/upload_986f93088ccd522fba4dcabcb0f19207.png)
| --- | --- |

Here we see that if we scan with the last quadrupole we have a minimum in both planes

![](https://codimd.web.cern.ch/uploads/upload_aeb52b83b9a340ac96fdf2720f53623c.gif)

![](https://codimd.web.cern.ch/uploads/upload_821140169f1d64da5450a675ad63bcc3.png)



Not sure we there is two angles after the quadrupole...

If we scan all quadrupoles with the same increase in current
![](https://codimd.web.cern.ch/uploads/upload_70c49d57d06637a051158ca5a9c0f931.png)


## Quad Scan East scripts

https://gitlab.cern.ch/eljohnso/quad-scan-east

![](https://codimd.web.cern.ch/uploads/upload_bd6b6d468ccd860216e8a5139d35c067.png)

- [ ] Need to add MAD-X prediction and beam size calculation from fitting the gaussian
- [ ] Once I have beam

![](https://codimd.web.cern.ch/uploads/upload_b28e8fa7205130e60dd55a6ec2196797.gif)

[Source code: quad_scan_east_dump_auto_scan_trigger.py](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/quad_scan_east_dump_auto_scan_trigger.py)

![](https://codimd.web.cern.ch/uploads/upload_4175a6b7c9a6823e2a74938411c58d11.png)

**Check Centered in Quad** is a script that scan three currents in a specific quadrupole and looks at the mean position of the gaussian fit on a BTV. It takes continuously the last three $\mu$ and you can then steer the beam by hand with a steerer.
[Source code: check_centered_in_quad.py](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/check_centered_in_quad.py)
![](https://codimd.web.cern.ch/uploads/upload_9aa21c04af4889d4713b248f69431fdf.png)

add the venv /user/cpsop/EliottFolder/quad-scan-east/venv/bin/python

## MD Quad Scan East Dump

* [x] Quad scan to east dump
    * [x] Request an MD for week 4 to 8 April (not needed, MD haven't started yet)
    * [x] Use one of the latest acquisition (as in the beginning the spill has dynamic effects)
    * [x] First center the beam by hand (if it isn't centered, the beam will move as you changed quad strength)
    * [x] Look into a centering by script

[PS logbook event: ](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3533876)
![](https://codimd.web.cern.ch/uploads/upload_b5af861d20eed281ff9fca2d62e53479.png)


Rematched initial parameters
[Source code: initial_param_quad_scan.ipynb](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/initial_param_quad_scan.ipynb)

| $\beta_x$ [m] | $\beta_y$ [m] | $\alpha_x$ | $\alpha_y$ | $D_x$ [m] | $D_y$ [m] | $D'_x$ [mrad] | $D'_y$ |
| - | - | - | - | - | -| - | - |
| 81.278 | 3.024 | -19.03 | 1.889 | -7.708 | -1.981 | -1.938 | -0.01 |

![](https://codimd.web.cern.ch/uploads/upload_6fcc6de3c574bcacd32c26991692d05e.png)


[Source code: quad_scan_east_dump.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/EliottBranch/ps_extraction/east-fast-extraction/quadrupole_scan/quad_scan_east_dump.ipynb)
![](https://codimd.web.cern.ch/uploads/upload_5f688899b179ef0135f4a41aca0d92d3.png)

Beam size that exit is very large, probably an effect of the stray fields !

![](https://codimd.web.cern.ch/uploads/upload_a41f426d63a9cc235cfa440d338360e9.png)


Tool to visual the beam size on different BTVs
[Source code: quad_scan_east_dump.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/EliottBranch/ps_extraction/east-fast-extraction/quadrupole_scan/quad_scan_east_dump.ipynb)
![](https://codimd.web.cern.ch/uploads/upload_7d6d5985076c6180c743cff5f27ed6a7.png)

## Second quadrupole scan to East Dump (multi-quad scan)

Scan with QFN01 and then a combination of multiple quadrupoles

[PS logbook entry: 3535982](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3535982)

![](https://codimd.web.cern.ch/uploads/upload_4c988d2fda730c8cd4812de3ccb68cfc.png)

Momentum spread (dp/p) measurement:
[PS logbook entry: ](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3536215)
![](https://codimd.web.cern.ch/uploads/upload_5a645718c690edb2c1d226ccdba333d5.png)


## Using the initial rematched parameters

We get pretty close results

|     |     |
| --- | --- |
|  ![](https://codimd.web.cern.ch/uploads/upload_fbb9a393f7043cfbd71ec83f13e2fe84.png)   |  ![](https://codimd.web.cern.ch/uploads/upload_bee91589659f5ab3c4b2417ae1600a2d.png)   |
|![](https://codimd.web.cern.ch/uploads/upload_94c6ecf6426f56d1ed24331703885e3c.png) | ![](https://codimd.web.cern.ch/uploads/upload_681daf94a808cb5010096472f4d3af20.png)|
|![](https://codimd.web.cern.ch/uploads/upload_a1435077bad14b62ae828e135f2f20c0.png) |![](https://codimd.web.cern.ch/uploads/upload_2da51d18515525064d16398d3299c2e2.png) |
|![](https://codimd.web.cern.ch/uploads/upload_53f92c4e7eb10155b5dc9a305511aa17.png) | |


## Now we fit the initial parameters to the new measurements
### New initial conditions East Area for first multi quad scan (fitted on acq 4)
betx0 = 8.09843982e+01
bety0 = 1.14828044e+00
alfx0 = -1.02992437e+01
alfy0 = 1.02810951e+00
Dx0 = -6.29106942e+00
Dy0 = -1.66369723e+00
Dpx0 = -1.58957627e+00
Dpy0 = 2.48083379e-01
exn = 1.24808650e-07
eyn = 1.50809414e-06
sige = 7.51976960e-04
![](https://codimd.web.cern.ch/uploads/upload_794f85f0dd2c52771bd53ad540886c08.png)

### New initial conditions East Area
betx0 = 7.88505738e+01
bety0 = 9.12591855e+00
alfx0 = -8.85113077e+00
alfy0 = 3.89150284e-01
Dx0 = -3.71596167e+00
Dy0 = 1.06111529e+00
Dpx0 = -1.09112445e+00
Dpy0 = 2.22635623e-01
exn = 1.94484764e-07
eyn = 1.49385093e-06
sige = 7.69017680e-04
![](https://codimd.web.cern.ch/uploads/upload_f501f194d08d09ac6d15072ebb32c933.png)

Now I want to fit all the measurement
The idea is to create two dataframes: one in the horizontal and one in the vertical plane so that I can select different ranges of current.

![](https://codimd.web.cern.ch/uploads/upload_265a136f36ffb2945dcb2543f798ccdf.png)

![](https://codimd.web.cern.ch/uploads/upload_80dccfd643c3becf53df28f870663a58.png)

array([ 8.19920817e+01,  1.00345876e+00, -1.51278591e+01,  5.66687199e-01,
       -4.44798154e+00, -1.46990789e+00, -1.17991258e+00, -1.63015018e-01,
        1.49296881e-06,  4.23196016e-07,  7.58432482e-04])
![](https://codimd.web.cern.ch/uploads/upload_872a6cb1035620b410c3460ffc62056a.png)


This is a picture of the horizontal and vertical plane dataframe before matching.
It's an append of two measurements that have had their range cut off.
![](https://codimd.web.cern.ch/uploads/upload_869d2a1db9daef7c8487697095f79174.png)

![](https://codimd.web.cern.ch/uploads/upload_b512bb16c09beb4e3fc565ee104cf791.png)

Now I add all 5 measurements:
initial conditions:
betx0 = 8.03942769e+01
bety0 = 2.09833303e+00
alfx0 = -1.25041716e+01
alfy0 = -1.11553173e-01
Dx0 = -5.20554087e+00
Dy0 = -1.00223341e+00
Dpx0 = -1.34656718e+00
Dpy0 = -8.72632488e-02
exn = 1.48924155e-06
eyn = 1.51732434e-06
sige = 7.47249503e-04
![](https://codimd.web.cern.ch/uploads/upload_3fb1d79d4f561230e2940d8c953c98db.png)

9.16529886e+01  1.59708544e+01 -1.31925106e+01  2.79200640e-01
 -5.19511017e+00 -9.78341505e-02 -1.44903397e+00 -3.12519595e-01
  5.07277045e-07  1.61376217e-06  6.94155852e-04
![](https://codimd.web.cern.ch/uploads/upload_07553a46028f2d40712c54f92e3f1d68.png)

array([ 9.16529882e+01,  1.59708543e+01, -1.31925112e+01,  2.79200512e-01,
       -5.19511012e+00, -9.78329706e-02, -1.44903384e+00, -3.12518967e-01,
        5.07277015e-07,  1.61376218e-06,  6.94155853e-04])
![](https://codimd.web.cern.ch/uploads/upload_a35b06d54302caece669c3dd6566c9b0.png)

![](https://codimd.web.cern.ch/uploads/upload_57cf108579a8a07c2ee5b67bcf6b77fe.png)


This is with using square of the difference instead of linear:
![](https://codimd.web.cern.ch/uploads/upload_553a35a2d4797453ec460adff016326f.png)
[Source code: optimise_on_big_dataframe.ipynb](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/optimise_on_big_dataframe.ipynb)


From the five measurements, I select acquisition 4 which is at a time where the beam is stabilised (after the F8L eddy currents) and split the data into Horizontal and Vertical planes. I then select a custom range for each measurements.

![](https://codimd.web.cern.ch/uploads/upload_28b115bfe1a33e39422421893ff341ac.png)
![](https://codimd.web.cern.ch/uploads/upload_9391727a59ee9691292effac5ceee025.png)
![](https://codimd.web.cern.ch/uploads/upload_bbf1354ac9d47acd3dd138826fc20b52.png)
![](https://codimd.web.cern.ch/uploads/upload_3df7f8a879a65314e53a4481ffb34ea1.png)
![](https://codimd.web.cern.ch/uploads/upload_0a134ba111c2ee89e62105954bd3f374.png)

![](https://codimd.web.cern.ch/uploads/upload_8e4bb3b71bfe2415c4db96530fad7d2c.png)

Multi-processing, 4x speed boost !
[Source code: optimise_on_big_dataframe_with_multiprocessing.ipynb](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/optimise_on_big_dataframe_with_multiprocessing.ipynb)

[Source code: compare_measurements_with_MADX.ipynb](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/compare_measurements_with_MADX.ipynb)
![](https://codimd.web.cern.ch/uploads/upload_5797e4615b0acd52b6bf0a9aada15ace.png)

Initial parameters where found: [[East Area Initial parameters]]

## Quadrupole scan in BTP

![](https://codimd.web.cern.ch/uploads/upload_998e3717bf317a1f2688549d132937c0.png)

We have **7 Quadrupoles** and **1 SEM-Grid**

* btp.qno10
* btp.qno20
* btp.qno30
* btp.qno35
* btp.qno50
* btp.qno55
* btp.qno60


![](https://codimd.web.cern.ch/uploads/upload_ad067b2922cf3b8777e928a54aa3dd19.png)

![](https://codimd.web.cern.ch/uploads/upload_a456ef898aec80ffa243c70a4aee69cb.png)

Quadrupole current range (from the working set)

QN010 -440 to 440 [A]
QN020 -330 to 330 [A]
QN030 -368 to 368 [A]
QN035 -450 to 450 [A]
QN050 -202 to 202 [A]
QN055 -243 to 243 [A]
QN060 -255 to 255 [A]

![](https://codimd.web.cern.ch/uploads/upload_19f33a48e81c93051c30221f8bdaf45b.png)

[Magnet Transfer function btp.qno10](https://edms.cern.ch/ui/file/2138782/2/report_PXMQNCMNWC_docx_cpdf.pdf)

| Current [A] | Integrated Gradient [T] |
|-------------|-------------------------|
| 0           | 0.0044                  |
| 20          | 0.232                   |
| 40          | 0.463                   |
| 60          | 0.694                   |
| 80          | 0.925                   |
| 100         | 1.16                    |
| 120         | 1.39                    |
| 140         | 1.62                    |
| 160         | 1.85                    |
| 180         | 2.08                    |
| 200         | 2.31                    |
| 220         | 2.54                    |

[Magnet Transfer function btp.qno20-60](https://edms.cern.ch/ui/file/2213106/2/2019_MagneticMeasurementReport_PXMQNCUNWP_EDMS_2213106.pdf)

| Current [A] | Integrated Gradient [T] |
|-------------|-------------------------|
| 5           | 0.075                   |
| 10          | 0.153                   |
| 25          | 0.386                   |
| 50          | 0.774                   |
| 75          | 1.162                   |
| 100         | 1.550                   |
| 125         | 1.936                   |
| 150         | 2.324                   |
| 200         | 3.094                   |
| 250         | 3.858                   |
| 300         | 4.612                   |
| 350         | 5.326                   |
| 377         | 5.681                   |
| 400         | 5.971                   |

These are the same number used in LSA except for the first quadrupole in the line btp.qn010

Initial values

* kbtpqno10 = 0.0000000000e+00;
* lm = 6.4000000000e-01;
* kbtpqno20 = 6.9653295476e-01;
* kbtpqno30 = -6.8247426697e-01;
* kbtpqno35 = 7.7401592074e-01;
* kbtpqno50 = 2.5075692540e-01;
* kbtpqno55 = -4.4720119166e-01;
* kbtpqno60 = 4.7146123748e-01;
* anglesmh42 = -5.5000000000e-02;

[Source code: quad_scan_btp.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/EliottBranch/ps_injection/bt3btp_lhcindiv/stitched/jmad/quad_scan_btp.ipynb)

![](https://codimd.web.cern.ch/uploads/upload_5bc03b9128bcdc2c3a287cb2e8085a6e.png)

## MD6543

https://asm.cern.ch/md-planning/injectors-requests?mode=b&query=eliott

Create an environment:

* **Open a terminal**: Left click -> Xterm -> Local Xterm
* **Go to a working folder**: cd /user/cpsop/EliottFolder
* Here you can for example **git clone** a folder
* Open pycharm at the location of the folder you want to work with
* In the pycharm terminal **create a venv**:
    * source /acc/local/share/python/acc-py/base/pro/setup.sh
	* Click bottom right to select the environment (add interpreter)
	    * Existing environment /user/cpsop/EliottFolder/btp_venv/bin/python/
	* Create a venv:
        * acc-py venv /tmp/f6x-t8-venv
        * source /tmp/f6x-t8-venv/bin/activate

	* (acc-py venv /user/cpsop/EliottFolder/btp_venv/bin/activate)

Pip install the packages needed into the venv and then run the script in interactive mode:

* pip install pybt


acc-py is used to pip install cern libraries [acc-py](https://acc-py-repo.cern.ch/repository/vr-py-releases/simple/)

[PS Logbook entry for MD6543](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3444178)

[Emittance measurement on MD2 for Eliott Johnson](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3444294)
|     |     | |
| --- | --- | --- |
|![](https://codimd.web.cern.ch/uploads/upload_b516310c9d4ed09a5df05095ced57b35.png)| ![](https://codimd.web.cern.ch/uploads/upload_6ba366be3bc0f510e285b66964ffcc1d.png) | ![](https://codimd.web.cern.ch/uploads/upload_ecbb3756f80069e1c22bdc4098d60fda.png) |


Two measurements of 20 currents and 60 data points:

* QNO60 **Horizontal** : scan_2022_03_09_13_13
* QNO60 **Vertical** : scan_2022_03_09_14_37

[Source code: analysis_MD6543.ipynb](https://gitlab.cern.ch/mfraser/btp-quad-scan/-/blob/debug/scanning-script/analysis_MD6543.ipynb)

**Mean position**

|     |     |
| --- | --- |
|  ![](https://codimd.web.cern.ch/uploads/upload_d25b45bd6e392cec43af7185507f905b.png)   |   ![](https://codimd.web.cern.ch/uploads/upload_65ab776dcac666d2a96beecfc7d0f483.png)  |

**Sigma**

|     |     |
| --- | --- |
|  ![](https://codimd.web.cern.ch/uploads/upload_18537042101b5fd6d3d4db3151f96725.png)   |  ![](https://codimd.web.cern.ch/uploads/upload_8bc2074c50a07fa5c197f131117086b1.png) |

[Source code: quad_scan_btp.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/EliottBranch/ps_injection/bt3btp_lhcindiv/stitched/jmad/quad_scan_btp.ipynb)

![](https://codimd.web.cern.ch/uploads/upload_ee340ba4806e67fe2a936d48fc1efc8d.png)

Fit the 8 parameters, took 19 m

![](https://codimd.web.cern.ch/uploads/upload_b7b49f88ee6015402e1afec6212f103b.png)


![](https://codimd.web.cern.ch/uploads/upload_5c85a7d58cc3532b259edff5f3266d4d.png)


Why does the beam with +500 Hz doesn't follow MADX ?
The beam at this region isn't a gaussian anymore.

Probably losses, need to check BLMs

|     |     |
| --- | --- |
| ![](https://codimd.web.cern.ch/uploads/upload_a202fc856416ac9f5f8b963bf9c56732.png) |  ![](https://codimd.web.cern.ch/uploads/upload_e06748e963f6169e856823081253e098.png) |




**Horizontal**
|   -500 Hz  |  +0 Hz   |  +500 Hz   |
| --- | --- | --- |
| ![](https://codimd.web.cern.ch/uploads/upload_ff442148c36d80e66d2cd554c3bf0ba4.gif) | ![](https://codimd.web.cern.ch/uploads/upload_77adb4d56f21ce8d632b5fdf73429548.gif) |![](https://codimd.web.cern.ch/uploads/upload_b16ed5a8e33ee0ed7eab0cca639a4034.gif)
 |


**Vertical**
|   -500 Hz  |  +0 Hz   |  +500 Hz   |
| --- | --- | --- |
| ![](https://codimd.web.cern.ch/uploads/upload_73aa179c7e6745ac80f66c8fe9dff70c.gif) | ![](https://codimd.web.cern.ch/uploads/upload_581e086e8962bf28143e66ce3e3b4374.gif)  | ![](https://codimd.web.cern.ch/uploads/upload_bf8d264e348c009ba59ea69c6cd77a79.gif)  |

### QNO55 and QNO60 **Vertical**: scan_2022_03_09_15_28

|     |     |
| --- | --- |
| ![](https://codimd.web.cern.ch/uploads/upload_54e997320b5f4f638ea751eee2beb165.png) |  ![](https://codimd.web.cern.ch/uploads/upload_f56f77171261fba99bb448786ccf9648.png)   |

|     |     |     |
| --- | --- | --- |
|  ![](https://codimd.web.cern.ch/uploads/upload_610e82e03cdccc3782c7896ebec68d0e.gif)   | ![](https://codimd.web.cern.ch/uploads/upload_7a6f67395704f6eab9a55405845075f8.gif)   |  ![](https://codimd.web.cern.ch/uploads/upload_55eabbde1b98a049fde57cae13ac9588.gif)   |


![](https://codimd.web.cern.ch/uploads/upload_ea2ad3ae3241ad95bb737a28c1d24323.png)


### Initial beam parameters by fitting to data

[Source code: quad_scan_btp_fit_data.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/EliottBranch/ps_injection/bt3btp_lhcindiv/stitched/jmad/quad_scan_btp_fit_data.ipynb)

| betx0     | bety0      | alfx0      | alfy0       | dx0        | dy0 | dpx0       | dpy0 |
|-----------|------------|------------|-------------|------------|-----|------------|------|
| 5.6660354 | 4.24254748 | 0.09511546 | -0.08277992 | 0.04560857 | 0.0 | 0.09806506 | 0.0  |

![](https://codimd.web.cern.ch/uploads/upload_290f17718e37d3f04bcffd99fac7101e.png)




## Quadrupole scan with filters MD7505

- QFN01 scan 400-730 [A] -> [0.317, 0.537]

- QFN01 scan 100-730 [A]-> [0.08, 0.537]

Multiple quad scan:

QF01 [400,700] -> [0.317, 0.537]
QD02 [0,480] -> [0, 0.2]
QFN03 [0,420] -> [0, 0.21]

QF01 [700,400] -> [0.537, 0.317]
QD02 [0,480] -> [0, 0.2]
QFN03 [0,420] -> [0, 0.21]


QF01 [400,700] -> [0.317, 0.537]
QD02 [480,200]  -> [0.2, 0.086]
QFN03 [420,200] -> [0.21, 0.11]

High resolution of a minimum in the vertical plane
QF01 [500,400]-> [0.40, 0.32]
QD02 [320,480] -> [0.14, 0.2]
QFN03 [290,420] -> [0.15, 0.21]


![](https://codimd.web.cern.ch/uploads/upload_b50add6510c680f03e51be9d50516a8f.png)
![](https://codimd.web.cern.ch/uploads/upload_f79e74b3409ed1a9bc4467de623dfaca.png)
![](https://codimd.web.cern.ch/uploads/upload_f716f330ea75498f1d980627011bc890.png)
![](https://codimd.web.cern.ch/uploads/upload_df101ae23e21c331f56031a1cbf0d104.png)
![](https://codimd.web.cern.ch/uploads/upload_dec5a113055997f79c314957ed108e88.png)
![](https://codimd.web.cern.ch/uploads/upload_b37bcf1dfd1026b9f08b8216d65e61d5.png)
![](https://codimd.web.cern.ch/uploads/upload_05002148226bee0946c07fd1466d8460.png)
![](https://codimd.web.cern.ch/uploads/upload_4f8bfc03b23f99de2877fe9508e3027e.png)
![](https://codimd.web.cern.ch/uploads/upload_385b84b561d7baa972a108156b66202b.png)
![](https://codimd.web.cern.ch/uploads/upload_2e5dba9300c554dc9a5b06a38a3bf81f.png)
![](https://codimd.web.cern.ch/uploads/upload_d17f28b78d98d3ec39a2abd38f086531.png)

5th July 2022
![](https://codimd.web.cern.ch/uploads/upload_49da1fc9b2d71062a85cf9db22b4fcca.png)
![](https://codimd.web.cern.ch/uploads/upload_2ecfb37f035cb1dbbac2a07116d1b71a.png)
![](https://codimd.web.cern.ch/uploads/upload_ee551941ed22f5bbb8c806c2c5f8c15e.png)

## Optimisation with Pybobqa

With all parameters free
![](https://codimd.web.cern.ch/uploads/upload_3fdd22cac216ada87def635fcb5fa688.png)

With Dispersion set constant and values taken from codilog
![](https://codimd.web.cern.ch/uploads/upload_0666088528f37d2e6c6ad3184637dfd9.png)

With optimising on H then V. The convergence is much faster.
![](https://codimd.web.cern.ch/uploads/upload_bd9340d73cd545da84a5e7dc9fd35887.png)

Optimising on more measurement
![](https://codimd.web.cern.ch/uploads/upload_fc746644b4fba4937bb743fce0c73301.png)

kfn01_list = np.linspace(0.317,0.537,25)
kdn02_list = np.linspace(0,0.2,25)
kfn03_list = np.linspace(0,0.21,25)
![](https://codimd.web.cern.ch/uploads/upload_283f7ca4e565f72f7266953051fa3424.png)

![](https://codimd.web.cern.ch/uploads/upload_0b4bc0f90610eac99e254610703cc1f9.png)

MWPC

![](https://codimd.web.cern.ch/uploads/upload_3434e18ee004b2c700da8792c88196c3.png)


![](https://codimd.web.cern.ch/uploads/upload_72324a73477c79b7d4933904db7569ea.png)

![](https://codimd.web.cern.ch/uploads/upload_db93fb102a52f42cbd2e61747f562f93.png)

BPM01
![](https://codimd.web.cern.ch/uploads/upload_1195a0640cadc1c849a4ab22da80a555.png)


![](https://codimd.web.cern.ch/uploads/upload_0be186c2e28cc9e9b313ebb07259648c.png)

![](https://codimd.web.cern.ch/uploads/upload_dfe5dec72ebda4cdae8fba32f78d5242.png)






# Radial steering for Dispersion measurement
To untangle the dispersion from the optimiser, a dispersion measurement has been tried out: [[Dispersion measurement]].

