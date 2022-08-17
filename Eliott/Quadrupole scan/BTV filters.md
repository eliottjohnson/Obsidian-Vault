# BTV filters

[PS logbook event](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3552466)

[BTV video on the deployement of Beam observation TV](https://videos.cern.ch/record/1750709)

**Filters setting:**
* no_filter
* filter_1 0.1
* filter_2 0.01
* filter_3 1/1000 0.001

On nominal slow extraction at 59.7 10^10. Beam is saturated with filter_2 (OD2 1/100) but not with filter_3 (OD3 1/1000).
Use filter_3 for futur measurements.
For a next implementation of filter, a filter between OD2 and OD3 would be better to increase signal to noise ratio.

To see saturation, click on red (+) button. Drag horizontally the window to reveal the Profile Type: Projection
From this you can see if the beam projection has a flat top which means it's saturated or not.

Beam remanence is suppressed with filter_3. Useful to see beam movement during spill.

Cameras are radhard and old cameras have more noise than new ones.

**Camera offset** -> moves the baseline of the noise. Useful to get better fits because it cuts the noise and removes it from the fit calculation. Same can be done in offline analysis.
1.23 ms is the remanence time
filter_3 is a bit to strong so the signal to noise ratio is low. That means you'll have more error when making a fit but this can be corrected by taking statistics

## MD7504 BTV filters characterization in the East Area

The goal of this MD is to benchmark the newly installed filter wheels in F61.BTV012 and
F61D.BTV010.

[PS Logbook event low intensity](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3569551)
[PS Logbook event high intensity](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3570066)

**Procedure:**
• Constant optics.
• Acquire 25 shots per filter.
1 filter = 25*30 sec = 12.5 min
One wheel = 4*12.5 = 50 min
Two wheels ~= 2h

* Scale intensity to the dump to see if filter wheels scale with intensity
    * Go to three turn but one cycle skip every cycle so as not to trigger RP

**Image processing:**
1) Apply gaussian blur or other technique using (https://scipy-lectures.org/packages/scikit-image/index.html)
2) Make fit on whole image to extract $\mu_{0}$ and $\sigma_{0}$
3) Center Mask on $\mu_{0}$ of size multiple of $\sigma_{0}$ (maybe 5)
4) compute $\mu$ and $\sigma$

**Measurement:**
* BTV image
* Intensity
* Septum strength ?
* Bramp ?
* Spill intensity on spill detector ?


4 filters installed

**Analysis:**
* Gaussian distribution of the spread in beam size shot by shot (in H and V)
* Comparison in measured beam size using different filters
* Is filter 4 too low too noisy at low intensity?
* Difference in beam size with constrained window (mask) during projection

* Use gaussian blur and **mask** for image processing

**Plots:**
[Source code: filter_wheel_analysis.ipynb](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/filter_wheel_analysis.ipynb)

![](https://codimd.web.cern.ch/uploads/upload_1b8787b85efd045b5cb82b36a467b029.png)

![](https://codimd.web.cern.ch/uploads/upload_a13d277c6ad1a9d3ef6edf969719f238.png)
![](https://codimd.web.cern.ch/uploads/upload_593a142da30079db1deac109ef93e531.png)


* Is the intensity linked to $\sigma_{H}$ and $\mu_{H}$
    * Plot of CPS intensity vs $\sigma_{H}$
    
    |     |     |
    | --- | --- |
    | ![](https://codimd.web.cern.ch/uploads/upload_36004f801d51c73287b4799baece6057.png) | ![](https://codimd.web.cern.ch/uploads/upload_f181c94537915073c44dfcd734726dc8.png)
    |  ![](https://codimd.web.cern.ch/uploads/upload_970ee8835cd8f8b77560295b1924cd4c.png) |  ![](https://codimd.web.cern.ch/uploads/upload_61819d2b3ae5fa89e5f6f689a84d5b91.png)

    * Do the same for other filters
   
* Remanenscence influences beam size because if you have movement you'll see old beam and it makes the beam wider
    * Plot of beam size vs acq. for each filter setting
    * Beam size during the spill

![](https://codimd.web.cern.ch/uploads/upload_3364c7792a04e4ef32cbd82e2d74ed26.png)
![](https://codimd.web.cern.ch/uploads/upload_f88c6b2ec304f866ae2a2329b0e42e68.png)


    
* Can I link intensity of CPS to intensity on BTV if not saturated
    * Plot of CPS intensity vs Area under projection (sum of projection ?)
    * 
    ![](https://codimd.web.cern.ch/uploads/upload_a8626383fa901267580bd6303bf7d07e.png)


* Saturation detector/alarm
    * Can I find a good way to tell if the beam saturates or not
    * Simple way: count the number of max pixel count
        * Plot of # pixels that saturate vs intensity
        * /!\ max pixel count changes depending on the image processing (gaussian blur or median filter)

        ![](https://codimd.web.cern.ch/uploads/upload_5b392c26e7b25669e43fe011a3b2f627.png)
        * The problem is we don't know at what intensity filter_3 will start to saturate, we need to find an indicator of signal to noise.

From this plot we learn that with filter_3 we never saturate up to at least $40\cdot10^{10}$ intensity.
We also see a linear trend of increasing saturation with intensity. filter_2 for example doesn't saturate at low intensity.

* During a quad scan, the beam size will get very small and thus risks to saturate:
    * Need to change optics and see if saturates

* We want high Signal to Noise Ratio (SNR)
    * Maybe a good way would be sum(pixels acquisition)/sum(pixel background)
    * One way we can quantizie if we have signal is the max height of the fitted gaussian gaussian_maxH and gaussian_maxV
    * Signal = gaussian_maxH + gaussian_maxV
    ![](https://codimd.web.cern.ch/uploads/upload_2baded9c27188e3b7e2d0f658a369973.png)
    * We see that if the Signal is under 7500, the BTV doesn't saturate so it seems to be a good indicator. I'm not sure if this hold with different beam sizes.
    ![](https://codimd.web.cern.ch/uploads/upload_1bb36dc7417e8103114a7cc77bc23752.png)
    ![](https://codimd.web.cern.ch/uploads/upload_840de46ca831bc0fe1e36f40ae4d768a.png)
    * From the plot of Signal vs intensity we see that filter_3 shouldn't saturate at $60\cdot10^{10}$ which is the nominal intensity for East.



* Plot of Beam size vs Intensity


|  |  |
| -------- | -------- |
| ![](https://codimd.web.cern.ch/uploads/upload_501a05ad8a74f760c9988748774c8943.png)     | ![](https://codimd.web.cern.ch/uploads/upload_7edbbb3f0c272b8c6d9a043702fa5c0d.png)     | 


We see that the beam size doesn't change with intensity. This is good if we saturate we know we can go lower in intensity or if we have too much noise, we can go higher in intensity.
![](https://codimd.web.cern.ch/uploads/upload_0ce555d6d33d04d4578d5c8b957eb296.png)

The beam size increase during the spill even with filter_3

## Integral under curve
![](https://codimd.web.cern.ch/uploads/upload_2289d370079b77a64455b07cb9ecff78.png)


* Measure if the fit is good with pcov (covariance matrix)
    * Plot pcov as a function of filter

![](https://codimd.web.cern.ch/uploads/upload_1a2a85c8688cb164e99ebfa8574f6727.png)
![](https://codimd.web.cern.ch/uploads/upload_55af59d8ec080ab686ec3f103c1d7246.png)

* Do we find the same beam size we two unsatured filters/beams

### Error on fit
![](https://codimd.web.cern.ch/uploads/upload_03cdf6804beebc2f470d9815507d6a9a.png)
![](https://codimd.web.cern.ch/uploads/upload_b00ddd17e8bc2f95162d55c056c68e53.png)

#### Local conclusion:
    * The higher the filter, the less acurate the fit
    * Beam that saturate have a rising error, it's more and more difficult to make a fit
    * With the third filter (unsatured) the fit gets better because you have more SNR

![](https://codimd.web.cern.ch/uploads/upload_88b0df53231f1527bc1a74ac8b364768.png)
![](https://codimd.web.cern.ch/uploads/upload_b4913535b81f5b84a3cef1975d98c5c9.png)

Increasing the intensity increase linearly the signal
![](https://codimd.web.cern.ch/uploads/upload_4bf0da16bc4a25e7d9e85d5143afe6ae.png)

![](https://codimd.web.cern.ch/uploads/upload_08cb62f61c99f95385b0dba1303cc657.png)


Note:
* Doesn't have to be gaussian in H but has to in V
* BTV images are logged
* Vertical beam size should grow with intensity

## Summary

BTV measurement done at the East Area Dump at 4 different intensities

Image processing is done by:
1) Passing the Raw image through a median filter
2) Fitting a gaussian to those measurement (many unfittable projections)
3) Finding the median parameters to find a suitable mask
4) Fitting again on the masked image

![](https://codimd.web.cern.ch/uploads/upload_9ad7ea11f77807e6b9965ceff666d46a.png)
![](https://codimd.web.cern.ch/uploads/upload_c04d39d9d9f6447876145cf778d9c509.png)
![](https://codimd.web.cern.ch/uploads/upload_c5daf74ed1ca700210a65e9a83a5a29a.png)

We learned that beam size is constant with intensity which means if we saturate we can lower intensity or if we don't have enough signal we can raise intensity

|     |     |
| --- | --- |
| ![](https://codimd.web.cern.ch/uploads/upload_dd2f6fcf1815a47f123c4fc629bd14df.png)  |  ![](https://codimd.web.cern.ch/uploads/upload_fa7f9c8443392568f6cb59fc2e62352e.png) |

Saturation happens everytime will no filter and OD1, OD2 saturate $>10\cdot10^{10}$ protons.
![](https://codimd.web.cern.ch/uploads/upload_93134201ce4a784aea5242490aa011f3.png)

Signal increase linearly with intensity
![](https://codimd.web.cern.ch/uploads/upload_e92f56eefee447e63496dc8a22dd0015.png)
![](https://codimd.web.cern.ch/uploads/upload_fc702e46bd811ea67a75d9ae58af5122.png)


Gaussian fit become better (i.e. the error become smaller) with more signal and worse with saturation. The lower attenuation ofthe filter, the less acurate the fit is. Beam that saturate have a rising error as it is more and more difficult to make a fit. With the third filter (unsatured) the fit gets better because there is a better signal to noise ratio.
![](https://codimd.web.cern.ch/uploads/upload_290702299c7bc2c9141b70cac03cbe02.png)
### Time dependant optics and sweep

Saturation increase the beam size. The Beam size isn't constant during the spill in the horizontal plane. There is a sweep in the horizontal plane.

|     |     |
| --- | --- |
|   ![](https://codimd.web.cern.ch/uploads/upload_95c0593ec42e0339f39dd1ab98b0bf79.png)  | ![](https://codimd.web.cern.ch/uploads/upload_1eb5be811224a613b6baa03ba00679e2.png)    |
|![](https://codimd.web.cern.ch/uploads/upload_b150a9f257374a1ffef2bc7db268e634.png) |![](https://codimd.web.cern.ch/uploads/upload_87d0b8b07966fa1039a3a715d6fd0fbf.png) |



## Image processing

https://scipy-lectures.org/packages/scikit-image/index.html
https://scikit-image.org/docs/stable/auto_examples/

![](https://codimd.web.cern.ch/uploads/upload_54bde69012bc6f898563701b87cf1cb9.png)
![](https://codimd.web.cern.ch/uploads/upload_44b6053ba2cf29e10d17809ade4e62cb.png)
![](https://codimd.web.cern.ch/uploads/upload_8c8d2ea86d163d6195ada056bb76fad3.png)
![](https://codimd.web.cern.ch/uploads/upload_1810908d1772ac4a9f6c20c378e5767a.png)
![](https://codimd.web.cern.ch/uploads/upload_c4d497522380648fcbe9bc26ac1143c9.png)

![](https://codimd.web.cern.ch/uploads/upload_9b15fa84b0189be6de25d160e7a4730e.png)

from scipy.signal import savgol_filter
Hy = loaded_pickle[1][btv_name+"/Acquisition"][0]["projDataSet1"][2]
Hx = loaded_pickle[1][btv_name+"/Acquisition"][0]["projPositionSet1"][2]
fig, ax = plt.subplots(figsize=(20,10))
ax.plot(Hx, Hy, label = f"H", alpha=0.5)
Hy_filtered = savgol_filter(Hy, 31, 2)
ax.plot(Hx, Hy_filtered, 'b') 

![](https://codimd.web.cern.ch/uploads/upload_9087b40da8245bde1e224e3c7de2ffe6.png)


![](https://codimd.web.cern.ch/uploads/upload_b02a1f2e8b21da1554b862273534a6df.png)

median filter -> mask
![](https://codimd.web.cern.ch/uploads/upload_cfd79169d748e39720608b0bbec68734.png)

These measurements were used in the [[Nominal beam size at East dump wall]] prediction.