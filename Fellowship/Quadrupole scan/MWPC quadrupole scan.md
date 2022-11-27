Information on how to open the [[MWPC]]

## High energy

Raw data
![[quad_scan_focal_mwpc_no_screen_in.gif|925]]
Centroid substraction
![[quad_scan_focal_mwpc_no_screen_in_with_mean_substraction.gif|925]]

Beam following
![[quad_scan_focal_mwpc_no_screen_in_with_beam_following.gif|925]]

## Low energy

### QDN7
Simulation show that for a minimum in the vertical plane, scanning QDN7 from **-0.04 to -0.1** will show a minimum

```ad-example
title: Code
collapse: closed

``` python
%matplotlib inline
fig, ax = plt.subplots(1,7, tight_layout=True, figsize=(20,3))

optics_name = "fitted_params_focal_mwpc_constrained"

k_list = np.linspace(0.04,0.1,25)

for i in range(len(k_list)):

    madx.input("kQFN1 = "+str(optics_file.loc[optics_file.name == optics_name].qfn01)+";")
    madx.input("kQDN2 = "+str(-optics_file.loc[optics_file.name == optics_name].qdn02)+";")
    madx.input("kQFN3 = "+str(optics_file.loc[optics_file.name == optics_name].qfn03)+";")
    madx.input("kQDN4 = "+str(-optics_file.loc[optics_file.name == optics_name].qdn04)+";")
    madx.input("kQFN5 = "+str(optics_file.loc[optics_file.name == optics_name].qfn05)+";")
    madx.input("kQDN6 = "+str(-optics_file.loc[optics_file.name == optics_name].qdn06)+";")
    madx.input("kQDN7 = "+str(-k_list[i])+";")
    madx.input("kQFN8 = "+str(optics_file.loc[optics_file.name == optics_name].qfn08)+";")

    twiss_f61 = madx.twiss(betx=betx0, bety=bety0, alfx=alfx0, alfy=alfy0, Dx=Dx0, Dy=Dy0, Dpx=Dpx0, Dpy=Dpy0).dframe()

    j=0
    for observation_point in ["t08.btv020", "t08.btv035", "t08.bpm073","t08.bpm080","t08.bpm085","t08.bpm092","t08.xwcm103"]:
    
        sigH = beam_size(twiss_f61['betx'][observation_point], twiss_f61['dx'][observation_point], ex, sige, 1)
        sigV = beam_size(twiss_f61['bety'][observation_point], twiss_f61['dy'][observation_point], ey, sige, 1)

        ax[j].set_title(observation_point)
        ax[j].scatter(-k_list[i], sigH, color="b", s=3)
        ax[j].scatter(-k_list[i], sigV, color="r", s=3)
        ax[j].set_ylim(0, 0.02)
        ax[j].set_ylabel("beam size [m]")
        ax[j].set_xlabel("K []")
        j+=1
	```
```


![[Pasted image 20221026101627.png]]


### QDN8
Simulation show that for a minimum in the vertical plane, scanning QFN8 from **0.07 to 0.08** will show a minimum

```ad-example
title: Code
collapse: closed

	``` python
	%matplotlib inline
	fig, ax = plt.subplots(1,7, tight_layout=True, figsize=(20,3))
	
	optics_name = "fitted_params_focal_mwpc_constrained"
	
	k_list = np.linspace(0.07,0.08,25)
	
	for i in range(len(k_list)):
	
	    madx.input("kQFN1 = "+str(optics_file.loc[optics_file.name == optics_name].qfn01)+";")
	    madx.input("kQDN2 = "+str(-optics_file.loc[optics_file.name == optics_name].qdn02)+";")
	    madx.input("kQFN3 = "+str(optics_file.loc[optics_file.name == optics_name].qfn03)+";")
	    madx.input("kQDN4 = "+str(-optics_file.loc[optics_file.name == optics_name].qdn04)+";")
	    madx.input("kQFN5 = "+str(optics_file.loc[optics_file.name == optics_name].qfn05)+";")
	    madx.input("kQDN6 = "+str(-optics_file.loc[optics_file.name == optics_name].qdn06)+";")
	    madx.input("kQDN7 = "+str(-optics_file.loc[optics_file.name == optics_name].qdn07)+";")
	    madx.input("kQFN8 = "+str(k_list[i])+";")
	
	    twiss_f61 = madx.twiss(betx=betx0, bety=bety0, alfx=alfx0, alfy=alfy0, Dx=Dx0, Dy=Dy0, Dpx=Dpx0, Dpy=Dpy0).dframe()
	
	    j=0
	    for observation_point in ["t08.btv020", "t08.btv035", "t08.bpm073","t08.bpm080","t08.bpm085","t08.bpm092","t08.xwcm103"]:
	    
	        sigH = beam_size(twiss_f61['betx'][observation_point], twiss_f61['dx'][observation_point], ex, sige, 1)
	        sigV = beam_size(twiss_f61['bety'][observation_point], twiss_f61['dy'][observation_point], ey, sige, 1)
	
	        ax[j].set_title(observation_point)
	        ax[j].scatter(k_list[i], sigH, color="b", s=3)
	        ax[j].scatter(k_list[i], sigV, color="r", s=3)
	        ax[j].set_ylim(0, 0.02)
	        ax[j].set_ylabel("beam size [m]")
	        ax[j].set_xlabel("K []")
	        j+=1
	```
```

![[Pasted image 20221026101936.png]]


# CHIMERA Quadrupole scan 27 Nov 2022

Quadrupole scan with the 1 GeV Pb ion beam

## QFN08

### at quad_scan_t8_ion_data/quad_scan_t8_ion_2022_11_27_13h10m52

![[Pasted image 20221127133603.png|875]]

### at 14h12m06s

With vertical correctors removed


## QDN07

### at 13h25m51s -0.04 - 0.0

![[Pasted image 20221127133612.png|850]]

### at 13h32m52s -0.0 to -0.06

At 13:43 I **remove the vertical correctors** to centre the beam vertically on the MWPC

### at 13h45m29s

![[Pasted image 20221127135307.png|825]]

### at 13h56m20

-0.06 to -0.03

![[Pasted image 20221127141539.png]]

## QDN05

### at 14h26m21s
