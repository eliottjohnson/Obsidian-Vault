
Displaying a number in scientific notation

``` python
'{:.2e}'.format(0.0002)
```

'2.00e-04'

## Numpy

### Mask matrices of several dimensions
```python
mat1 = np.array([[1,2],
      [3,4]])
mat2 = np.array([[5,6],
      [7,8]])

print(mat1)
print(mat2)

iy, ix = np.where(mat1 > 2)

print(mat1[iy,ix])
print(mat2[iy,ix])
```

## Pandas Dataframe

### Create a dataframe

```python
d = {'number_of_particle': [], 'number_of_turns': [], 'time': []}
df = pd.DataFrame(data=d)
```

### Concatenate two dataframes

```python
d = {'number_of_particle': [1], 'number_of_turns': [2], 'time': [3]}
df1 = pd.DataFrame(data=d)

d = {'number_of_particle': [4], 'number_of_turns': [5], 'time': [6]}
df2 = pd.DataFrame(data=d)

df = pd.concat([df1,df2])
```

### Fourier transform
``` python
yf = rfft(signal)
xf = rfftfreq(len(blm_signal), time_between_acquisition_in_seconds)

fig, ax = plt.subplots(figsize=(15,7))
ax.plot(xf, np.abs(yf))
ax.set_xlabel("freq [Hz]")
ax.set_ylabel("Amplitude [arb.]")
```


## Plotting

### Second y-axis

```python
fig, ax = plt.subplots()

ax2 = ax.twinx()
ax.plot(df.t, df.signal_1000, color="b", label="Scint")
ax2.plot(df_xsec.t-200, -df_xsec.signal_23_I1, color="r", label="XSEC")

```

### Save a figure

```python
plt.savefig("filename.png", facecolor='white', transparent=False, dpi = 150, bbox_inches='tight')
```

### Plot a line with different colors

```python
T=np.linspace(0,1,np.size(x))
        s = 1 # Segment length
        for i in range(0,len(x)-s,s):
            ax.plot(x[i:i+s+1],px[i:i+s+1],color=(T[i],0.0,1-T[i]), alpha=T[i], lw=2, marker="o", ms = 6*T[i])
            
```

### Change fontsize of all plots

```python
import matplotlib
font = {'family' : 'DejaVu Sans',
        'weight' : 'normal',
        'size'   : 16}

matplotlib.rc('font', **font)
```

### Heatmaps

Using scatter
```python
ax.scatter(df.number_of_particle, df.number_of_turns, c=df.time, cmap="magma", s=30)
```
![[Pasted image 20221012152451.png]]
Using tripcolor
```python
ax.tripcolor(df.number_of_particle, df.number_of_turns, df.time, cmap="magma")
```
![[Pasted image 20221012152459.png]]
Using tricontourf
```python
ax.tricontourf(df.number_of_particle, df.number_of_turns, df.time, cmap="magma")
```

![[Pasted image 20221012152504.png]]


### How to make a gif

```python
from matplotlib.animation import FuncAnimation, PillowWriter
%matplotlib notebook
fig, ax  = plt.subplots(figsize=(10,5), tight_layout=True)

def animate(i):
    ax.clear()
    ax.set_aspect("equal")
    try:
        ax.scatter(df.iloc[i].x, df.iloc[i].y)
    except:
        print("fail")
        pass
    return
    
ani = FuncAnimation(fig, animate, interval=1, blit=True, repeat=False, frames=len(df))
ani.save("gif/ptc_tracking_f61d.gif", dpi=300, writer=PillowWriter(fps=10))
```

## How to read a pickle file

``` python
import jpype
jpype.startJVM(jpype.getDefaultJVMPath())

import pickle

with open('filename.p', 'rb') as f:
    data = pickle.load(f)
```


## Linux
### Terminal commands
Read the size of folder
h for human readable
s for summarize
``` console
ls -sh
```

## Py-BOBYQA

[Py-BOBYQA documentation](https://numericalalgorithmsgroup.github.io/pybobyqa/build/html/index.html)

