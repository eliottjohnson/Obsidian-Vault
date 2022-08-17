# GEODE points

# Beam element positions in Geode

![](https://codimd.web.cern.ch/uploads/upload_ddcaf365b74abf12051337954bb75608.png)


The displacements are using a left-hand rule (vertical out of the page).
![](https://codimd.web.cern.ch/uploads/upload_d088dd3fa34161bedf6f242ecff286f9.png)


### Script to visualize the real positions:
https://gitlab.cern.ch/acc-models/acc-models-tls/-/blob/EliottBranch/ps_extraction/east-fast-extraction/Check%20scripts/geode_absolute_deviation_visualiser.ipynb

![](https://codimd.web.cern.ch/uploads/upload_3da8850d87876714fe0f456137a59ca3.png)
![](https://codimd.web.cern.ch/uploads/upload_b6e9d404ac47e7c4972067f4ff288c94.png)

Angle between SS63 theoretic and MQNL007 real -2.304
Real angle between SS63 and MQNL007 -2.315
Theoretical angle between SS63 and MQNL007 -2.083

Real longitudinal position between SS63 and start of Q74 in MADX ref: 0.4286 m 
Real radial position between SS63 and start of Q74 in MADX ref: 0.26199 m 

### Displacement of Q74
Powerpoint from Camille: https://cernbox.cern.ch/index.php/s/csF6Ayxb99nDnN3
He also explained that sometimes people ask for "**bumped**" or shifted positions. This is often used with dipoles.
In the case of Q74, there was a bump requested (I think for size constraint) of 9.747 mm radially. This can be found in the spread sheet if you do 0.012880 - 0.003133 = 0.009747 mm.
So if you have a large Dr it might be an intentional bump was requested and it's not that the equipement is wrongly placed. You should look at the Dr/bump to get an idea of the imprecision.

![](https://codimd.web.cern.ch/uploads/upload_1faaf6ba769155458e2e16ff1f48e1c1.png)

![](https://codimd.web.cern.ch/uploads/upload_ce776cb86537cd80758edb9717b46b98.png)
![](https://codimd.web.cern.ch/uploads/upload_11f264e2c05afe145aa3dae7dd6c5b32.png)

## Check theoretically versus measured points in GEODE BTP and PS

I use the measured points from GEODE for the BTP and PR accelerators:
![](https://codimd.web.cern.ch/uploads/upload_269863b769e9d1f72d0aaead1a0bd468.png)

I then have to compute the real points using **DEV_LONG_VALUE** and **DEV_RAD_VALUE** and this algorithm.

```
def calc_absolute_deviation(my_dataframe):
    output_dataframe = pd.DataFrame(columns=["name","x", "y", "x_dev_absolute","y_dev_absolute"])
    
    for i in range(len(my_dataframe)):
        if (my_dataframe.X_S[i]-my_dataframe.X_E[i])>=0:
            sign = +1
        else:
            sign = -1
        
        if type(my_dataframe.NAME[i])==str: # Check if we have a name value
            
            # We differentiate between points that have an entrée and sortis points and those who don't
            if (  (my_dataframe.Y_S[i] != my_dataframe.Y_E[i]) & (my_dataframe.X_S[i] != my_dataframe.X_E[i]) & (my_dataframe.X_S[i] != my_dataframe.X_E[i]) ):
                #print(f"{my_dataframe.NAME[i]} has a length")
                angle = (my_dataframe.Y_S[i]-my_dataframe.Y_E[i]) / (my_dataframe.X_S[i] - my_dataframe.X_E[i])
                x_e_dev = my_dataframe.X_E[i]+sign*my_dataframe.DEV_LONG_VALUE_E[i]*np.cos(angle)-sign*my_dataframe.DEV_RAD_VALUE_E[i]*np.sin(angle)
                y_e_dev = my_dataframe.Y_E[i]+sign*my_dataframe.DEV_LONG_VALUE_E[i]*np.sin(angle)+sign*my_dataframe.DEV_RAD_VALUE_E[i]*np.cos(angle)

                x_s_dev = my_dataframe.X_S[i]+sign*my_dataframe.DEV_LONG_VALUE_S[i]*np.cos(angle)-sign*my_dataframe.DEV_RAD_VALUE_S[i]*np.sin(angle)
                y_s_dev = my_dataframe.Y_S[i]+sign*my_dataframe.DEV_LONG_VALUE_S[i]*np.sin(angle)+sign*my_dataframe.DEV_RAD_VALUE_S[i]*np.cos(angle)
                
                output_dataframe = output_dataframe.append({"name": str(my_dataframe.NAME[i])+".E" , "x": my_dataframe.X_E[i], "y": my_dataframe.Y_E[i], "x_dev_absolute": x_e_dev, "y_dev_absolute": y_e_dev}, ignore_index=True)
                output_dataframe = output_dataframe.append({"name": str(my_dataframe.NAME[i])+".S" , "x": my_dataframe.X_S[i], "y": my_dataframe.Y_S[i], "x_dev_absolute": x_s_dev, "y_dev_absolute": y_s_dev}, ignore_index=True)
            else:
                #print(f"{my_dataframe.NAME[i]} doesn't have a length")
                # The angle will be calculated with the point before for elements that do not have a length
                angle = (my_dataframe.Y_E[i]-my_dataframe.Y_S[i-1]) / (my_dataframe.X_E[i] - my_dataframe.X_S[i-1])
                x_dev = my_dataframe.X_E[i]+sign*my_dataframe.DEV_LONG_VALUE_E[i]*np.cos(angle)-sign*my_dataframe.DEV_RAD_VALUE_E[i]*np.sin(angle)
                y_dev = my_dataframe.Y_E[i]+sign*my_dataframe.DEV_LONG_VALUE_E[i]*np.sin(angle)+sign*my_dataframe.DEV_RAD_VALUE_E[i]*np.cos(angle)
                                
                # This time we do not put an .E or .S as the element doesn't have a length
                output_dataframe = output_dataframe.append({"name": str(my_dataframe.NAME[i]) , "x": my_dataframe.X_E[i], "y": my_dataframe.Y_E[i], "x_dev_absolute": x_dev, "y_dev_absolute": y_dev}, ignore_index=True)
       
        else:
            #print ("no name for element: "+str(i))
            pass
    return output_dataframe
```

![](https://codimd.web.cern.ch/uploads/upload_11918b47ec9336ae239ff4a681e4ff3c.png)


Remarks: 
- Some elements have not been measured, they do not have longitudinal or radial deviation. For those points I use the theoretical point.
- The BTP line does not contain element up to SMH42 (contrary to faisceaux points)
- Some element are point like (they do not have a length). For these elements I use as an angle the element and the exit (sortis) point of the previous element.
-- I'm waiting for an answer from Camille to see if that is correct.
![](https://codimd.web.cern.ch/uploads/upload_c6b3c33b9d189ba5ce740081aa749eff.png)
![](https://codimd.web.cern.ch/uploads/upload_eb2677bf5e679b4c91e79ceac859709d.png)


For now, this is how it looks.

[Source code](https://gitlab.cern.ch/eljohnso/btp_stray_elements/-/blob/9731293894a24a07d9da8e87b242b576ab2ecaee/real_vs_theoretical_points.ipynb)

![](https://codimd.web.cern.ch/uploads/upload_b659d14be6535488c2294ebf3f59b480.png)


### Recompute injection tracking with PR measured and BTP measured

I then use these new points with the algorithm previously used to compute the tracking starting point.

```
angle_injection_deg = 5.324
vertical_offset = 0.544328
ang_glob = (-(angle_injection_deg)*np.pi/180, 0.0) # From points_faisceaux_visualizer_real_points
pos_glob = (vertical_offset,  0.0, -np.tan(subtending_angle/2)*(PS_radius) )
```

The angle is slightly larger and offset slightly smaller.

[Source code: points_faisceaux_visualizer_real_points.ipynb](https://gitlab.cern.ch/eljohnso/btp_stray_elements/-/blob/4d0caffcb638694112160f1861858d148266cf39/points_faisceaux_visualizer_real_points.ipynb)

![](https://codimd.web.cern.ch/uploads/upload_4fe2e67d4d917acfe38be9c23c0c84a1.png)

![](https://codimd.web.cern.ch/uploads/upload_d6153a4b977bb86a557503aa5b36a18b.png)

With these starting values I get a slightly worse slope (-0.0251 vs -0.022) compared to the measurements.

Conclusion: either I've made a mistake calculating the real points (to be confirmed by Camille) either...

![](https://codimd.web.cern.ch/uploads/upload_4c9a420225d53e78d97952e5353cf0cb.png)

## Discussion on Real points from GEODE with Camille Vandeuvre
14.01.2022

To calculate the orientation of each elements you need to take the Points faisceaux.

![](https://codimd.web.cern.ch/uploads/upload_56677ead12098c6eef6da6930ecb8255.png)

In the filters, select Système: Z (CCS)
![](https://codimd.web.cern.ch/uploads/upload_bc907c03731607e548122827d5a3ccf3.png)

Some elements that are point-like such as BTPSTART will not have a length, longueur or 1-10 $\mu m$
![](https://codimd.web.cern.ch/uploads/upload_b796b32800c85c0c1ca842bb3def342e.png)

**Each point** in MADX has a **direction attached** with three angles, THETA, PHI and PSI.
![](https://codimd.web.cern.ch/uploads/upload_084ca39d8dc62fbe75c852bef901de4a.png)

These three MADX angles are converted in GEODE in **Gisement**, **Pente** and **Tilt**.

* **Gisement**: 
    * the angle in the x,y plane (the plane if you view the PS from above) from the y to the direction of the point.
    * Units are in **grad**/gon where one turn $2\pi$ is 400 [gon].
    * The angle is clockwise from y pointing to the top.

![](https://codimd.web.cern.ch/uploads/upload_61e95a89ea4ccbe9d847c16350223e44.png)


Remark: good idea to check using gisement and an element that has two points (a length) to see if I get the same angle (and not +- 200 [gon] inverse direction)
    
* **Tilt**: Roll like a plane.

* **Pente**: pitch up or down. 

* **1/2 déflection**: in MADX is 1/2 ANGLE. When you have an bending magnet it applies a deflection to the beam.


### To calculate real points

First download the **faisceaux points** to get the **gisement** in csv format.

![](https://codimd.web.cern.ch/uploads/upload_06a3c8489e35776d59be9cb8f9699837.png)

![](https://codimd.web.cern.ch/uploads/upload_22f26064e4e0bddc4502eb97fbb3e2f1.png)


Then download the **Ecarts faisceaux**

![](https://codimd.web.cern.ch/uploads/upload_72aa07a771047d0b0194111c0f474e0a.png)

![](https://codimd.web.cern.ch/uploads/upload_370e847299f37c3d72ce1dd7b6b44658.png)

* **Ecart en tilt** again is the roll in an airplane. (Do not confuse it with a rotation forward/backwards)

* **Ecart longitudinal**: displacement along the beam axis

* **Ecart vertical**: along the z-axis

* **Ecart radial**: 


Perfectly aligned magnet with beam inside and marker (alésage) on top.
![](https://codimd.web.cern.ch/uploads/upload_1c6a4e53aecf5a1500d0da77ac5327f2.png)

In this case, l'écart alésage radial is large. L'écart roll is large. L'écart faisceaux is zero.
Remark: if the element is a dipole with a large écart roll this would be bad and induce component in the up/down beam direction.
![](https://codimd.web.cern.ch/uploads/upload_b9a1caecaf05b60e7278d2594ae31843.png)

In this case, l'écart alésage radial is zero because it's vertically aligned with the beam. L'écart in roll is large. L'écart faisceaux will not be zero.
![](https://codimd.web.cern.ch/uploads/upload_1b85ebd80765276da7306d35b970557f.png)

Ecarts faisceaux are calculated from the ecarts alésage.

![](https://codimd.web.cern.ch/uploads/upload_1e1cbfd5d652caabf9ded75e93eb0aee.png)


### My algorithm in python

[Source code: algorithm_real_points.ipynb](https://gitlab.cern.ch/eljohnso/btp_stray_elements/-/blob/master/algorithm_real_points.ipynb)

I merge two dataframes with the gisement and the écarts


![](https://codimd.web.cern.ch/uploads/upload_82507251760329fde3a072a6baaeef95.png)


I then use this algorithm (basically the first quadrant of the image):

```
btp_merged["dx_rad"] = -btp_merged["Valeur R (m)"]*np.cos(btp_merged["Gisement (rad)"])
btp_merged["dy_rad"] = btp_merged["Valeur R (m)"]*np.sin(btp_merged["Gisement (rad)"])

btp_merged["dx_long"] = btp_merged["Valeur L (m)"]*np.sin(btp_merged["Gisement (rad)"])
btp_merged["dy_long"] = btp_merged["Valeur L (m)"]*np.cos(btp_merged["Gisement (rad)"])

btp_merged["dx"] = np.add( btp_merged["dx_rad"] , btp_merged["dx_long"] )
btp_merged["dy"] = np.add( btp_merged["dy_rad"] , btp_merged["dy_long"] )

btp_merged["X réel CCS (m)"] = np.add(btp_merged["X (m)"], btp_merged["dx"])
btp_merged["Y réel CCS (m)"] = np.add(btp_merged["Y (m)"], btp_merged["dy"])
btp_merged["Z réel CCS (m)"] = np.add(btp_merged["Z (m)"], btp_merged["Valeur V (m)"])
```

You could also use this algorithm which gives the same results and has much more lines.

![](https://codimd.web.cern.ch/uploads/upload_c53cf6f4924473293be9fb819c0950ac.png)



which I have compared with what Camille found on [his excel sheet](https://cernbox.cern.ch/index.php/s/CuT1D1jUjGTgy7d) and I have +-63$\mu m$ difference.



## Q74 F61 and bump explanation

Bump 9mm is because of a size issue. Otherwise the quadrupole doesn't fit.

It is **not** where it's supposed to be in MADX.

The idea of a **bump** is that physicists ask the survey team to displace some element from the nominal beam line. Typical example are in the SPS: they run the pilot beam a first team and notice that some magnets have defects or aren't at the correct spot. They then ask to displace the affected quadrupole at a certain bump position (let's say +1 mm). The survey team goes in the tunnel, moves the quadrupole and remeasures the position. A second pilot beam is sent and observe the effect of a displaced quadrupole.
Now the survey team has to log theses **voluntary displacements** otherwise next time they measure they'll think there was a big error in the positioning. The voluntary displacements are alteration of the theoretically position.

![](https://codimd.web.cern.ch/uploads/upload_6bee5ea2364e02d3479df588da25a6e8.png)

![](https://codimd.web.cern.ch/uploads/upload_242b6bf34950113586b44f0cd3f416cd.png)

Thus, the MQNCL.007 is displaced with regards to the MADX position and a dipolar component is expected.

The survey team now has a **bumped theoretical** position which is the new theoretical position where the survey team wishes to position the element as best as possible.
There is always two écarts, the one with respect to the theoretical position and the one with respect to the bumped theoertical position.
The écart bumped should be zero.

![](https://codimd.web.cern.ch/uploads/upload_26f4f524f0a66dc4552141945a084797.png)

Remark: Most of the displacements (écarts) aren't done at the same date. When you have different dates (6 months to ~years) in measurements you should be careful. Relative measurements from the same date are very well know but not if there is a large temporal difference. The responsible for the PS complex is Pierre who knows at what date elements were measured and if you can compare measurements from different dates.

Remark: Dilatation of the PS Ring during operation and Winter/Summer. This could lead to extraction problems. Camille suspects that during operation the operator should see these issues.

Regarding the drawing PR-F61 position reelle. They took the écart from the PS and F61 and calculated these positions.
The 3D modeled isn't change, the real points are only found in GEODE.

### Mail from Daniel del Alamo 17.01.2022

```
Le modèle 3D de l’octant 6 : ST0712033_02
Le modèle 3D de la ligne F61 : ST1087633_01
Le drawing de la Ligne F61 : PSZVCF610063
Le modèle 3D du quadrupôle : ST1083466_01
Le drawing du quadrupôle : PSZHMQAD0001
```

How to look for drawings in CDD



[Direct Drawing Retrieval](https://edms5.cern.ch/cdd/plsql/c4w.retrieval_home_2?cookie=2704340)

To have all main unit drawings
![](https://codimd.web.cern.ch/uploads/upload_6af929360bcdb1d55fae2c85ddecf927.png)

[CDD Folder with all magnet units in the PS](https://edms5.cern.ch/cdd/plsql/c4w_folders.display_contents?cookie=2705347&p_folder_id=97574)

![](https://codimd.web.cern.ch/uploads/upload_bbb759d4844f323fafbd263b62fb8f3f.png)


![](https://codimd.web.cern.ch/uploads/upload_cbb0f8abfee29bacf2eae8f9a2ab9cd1.png)



[Layout F61 new ea 10](https://cernbox.cern.ch/index.php/s/U5x7OUuOD0Z1mjZ)

![](https://codimd.web.cern.ch/uploads/upload_ad0f91f8e7feb1bdc0198f83b654c82d.png)

![](https://codimd.web.cern.ch/uploads/upload_37897471266e57ee5edcac9deee2ee9a.png)

[List of parts](https://plm.cern.ch/prod/Client/?StartItem=CERN_CDN_TreeNavigator&RootNode=ST_Item:2714651ABDB952D7AEB7B1670D912154)

![](https://codimd.web.cern.ch/uploads/upload_aad48895dc1c4ea2647407fd83011012.png)


[Ens. Aimant Q74](https://cernbox.cern.ch/index.php/s/cwkrAgaHzPgqjmN)

![](https://codimd.web.cern.ch/uploads/upload_526889bc70b2b2e7e973e67260de11a6.png)

[Q74 3D model viewer](https://csviewer.web.cern.ch/document?CDD=false&documentNumber=ST1083466_01&documentVersion=a.03)
![](https://codimd.web.cern.ch/uploads/upload_9a87a496cb24b8ae7c103e6b79a0599b.png)

### SmarTeam

[Smarteam website](https://plm.cern.ch/prod/Client/?StartItem=CERN_CDN_TreeNavigator&RootNode=ST_Document:9245992AD5D4FB2CEFEC36143D6E026A)

![](https://codimd.web.cern.ch/uploads/upload_dc5dc3f1c7bcc629997be1e16f9ceb1e.png)

![](https://codimd.web.cern.ch/uploads/upload_14713857f54446484ee9b445ae3ed4dc.png)

![](https://codimd.web.cern.ch/uploads/upload_d2e27441fe20ad2f08c72e75b9d8b54c.png)

![](https://codimd.web.cern.ch/uploads/upload_301ca956ef4e8e5a1b2b4230e04c19b4.png)

[Full model of East Area](https://plm.cern.ch/prod/Client/?StartItem=CERN_CDN_TreeNavigator&RootNode=ST_Document:9245992AD5D4FB2CEFEC36143D6E026A)

Doc. Number: ST1087633_01

![](https://codimd.web.cern.ch/uploads/upload_86eadb9786c7e52e3860c317204c0d89.png)
