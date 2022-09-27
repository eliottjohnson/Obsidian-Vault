# PTC_TRACK simple example

``` python
init_dist = [[3e-3,0,3e-3,0],
             [6e-3,0,6e-3,0],
             [9e-3,0,9e-3,0],
            ]

ptc_output = []
try:
    madx.ptc_create_universe()
    madx.ptc_create_layout(model=2, method=6, exact=True, NST=10)
	madx.ptc_observe(place="f61.btv010")
    with madx.batch():
        for particle in init_dist:
            madx.ptc_start(x=particle[0], px=particle[1], y=particle[2], py=particle[3])
        madx.ptc_track(icase=4, element_by_element=True, dump=False, onetable=True, recloss=True,
                            maxaper=[0.1])
        madx.ptc_track_end()
    ptc_output = madx.table.trackone
    ptc_output = ptc_output.dframe()

except RuntimeError or IndexError:  # If magnets overlap or twiss incomputable
    print('MAD-X Error occurred, re-spawning MAD-X process')
    ptc_output = {}
```
