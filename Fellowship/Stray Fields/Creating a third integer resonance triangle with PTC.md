# Creating a third integer resonance triangle with PTC

[Source code: ptc_track_in_ps](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/EliottBranch/ps_extraction/east-fast-extraction/ptc_track_in_ps.ipynb)

## Gif

This gif follows a single particle during several turns in the PS
![[ptc_tracking_third_integer_resonance.gif|450]]

```ad-example
collapse: closed
title: Code



```python
from matplotlib.animation import FuncAnimation, PillowWriter
%matplotlib notebook
fig, ax  = plt.subplots(figsize=(5,5), tight_layout=True)


particle_number = 16

def animate(i):
    ax.clear()
    turn = i

    global particle_number
    
    ax.scatter(ptc_output[ptc_output.s == my_loc].x, ptc_output[ptc_output.s == my_loc].px, color="gray", alpha=0.5, s=1)
    
    x_list = []
    px_list = []
    try:
        x = ptc_output[(ptc_output.s == my_loc) & (ptc_output.number == particle_number) & (ptc_output.turn < turn) & (ptc_output.turn > turn-10)].x
        px = ptc_output[(ptc_output.s == my_loc) & (ptc_output.number == particle_number) & (ptc_output.turn < turn) & (ptc_output.turn > turn-10)].px

        
        T=np.linspace(0,1,np.size(x))
        s = 1 # Segment length
        for i in range(0,len(x)-s,s):
            ax.plot(x[i:i+s+1],px[i:i+s+1],color=(T[i],0.0,1-T[i]), alpha=T[i], lw=2, marker="o", ms = 6*T[i])
            
    except:
        print("fail")
        pass
    return
    
frames = int(ptc_output[(ptc_output.s == my_loc) & (ptc_output.number == particle_number)].turn.max())
# frames = 10
ani = FuncAnimation(fig, animate, interval=1, blit=True, repeat=False, frames=frames)
ani.save("gif/ptc_tracking_third_integer_resonance.gif", dpi=300, writer=PillowWriter(fps=7))
```
