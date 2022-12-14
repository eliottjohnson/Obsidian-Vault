
Displaying a number in scientific notation

``` python
'{:.2e}'.format(0.0002)
```

'2.00e-04'

## Datetime

```python
from datetime import datetime

datetime.fromtimestamp(1666793774.451).strftime('%d-%m-%y')
```

```python
dates = [datetime.fromtimestamp(ts) for ts in timestamp_list]
```

```python
df_xsec["timestamp"] = df_xsec["timestamp"]/1000000000
df_xsec["timestamp"] = [datetime.fromtimestamp(x) for x in df_xsec["timestamp"]]
```

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

### Take sub-array by passing an array of indexes

```python
np.take(numpy_array, list_indexes)
```

## Fourier Transform

``` python
from scipy.fftpack import rfft, rfftfreq
yf = rfft(signal)
xf= rfftfreq(len(blm_signal), time_between_acquisition_in_seconds)

fig, ax = plt.subplots(figsize=(15,7))
ax.plot(xf, np.abs(yf))
ax.set_xlabel("freq [Hz]")
ax.set_ylabel("Amplitude [arb.]")
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

### Filter by multiple conditions

```python
df_mean.where( (df_mean.instrument == instrument) & (df_mean.gain == gain) )
```

### Sort by column
```python
df.sort_values(by=['col1'])
```

### Non-uniform Fourier transform

[Source code: lombscargle_test.ipynb](https://gitlab.cern.ch/tbass/md-8923/-/blob/master/spill_data_bxscal/lombscargle_test.ipynb)
```python
w = np.linspace(1/sampling_period/2/len(signal_np), 1/sampling_period/2, 100000)*2*np.pi # This is in angular frequency w=2*pi*f, the lowest frequency is sampling_frequency/Number_of_FFT_point
pgram = scipy.signal.lombscargle(df.timeArray[bound_min:bound_max], df.BXSCAL_signal[bound_min:bound_max], w)

fig, ax = plt.subplots(tight_layout=True, figsize=(20,5))
ax.plot(w/2/np.pi, pgram) # we convert back to normal frequency
ax.set_xlabel("Frequency [Hz]")
```

#### Find peaks
```
peaks = find_peaks(pgram, height=0.3e6, distance = 100)
```

![[Pasted image 20221104125954.png|800]]

## Plotting

### Second y-axis

```python
fig, ax = plt.subplots()

ax2 = ax.twinx()
ax.plot(df.t, df.signal_1000, color="b", label="Scint")
ax2.plot(df_xsec.t-200, -df_xsec.signal_23_I1, color="r", label="XSEC")

```

#### multiple labels with twinx

``` python
fig.legend(loc="upper right", bbox_to_anchor=(1,1), bbox_transform=ax.transAxes)
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
plt.rcParams['axes.prop_cycle'] = plt.cycler(color=plt.cm.Dark2.colors)
```

### Change ticks size for all plots

```python
# set tick width
import matplotlib as mpl
mpl.rcParams['xtick.major.size'] = 12
mpl.rcParams['xtick.major.width'] = 4
mpl.rcParams['xtick.minor.size'] = 8
mpl.rcParams['xtick.minor.width'] = 2

mpl.rcParams['ytick.major.size'] = 12
mpl.rcParams['ytick.major.width'] = 4
mpl.rcParams['ytick.minor.size'] = 6
mpl.rcParams['ytick.minor.width'] = 2
```

### Plot a square

```python
import matplotlib.patches as patches

# Create a Rectangle patch
rect = patches.Rectangle((50, 100), 40, 30, linewidth=1, edgecolor='r', facecolor='none')

# Add the patch to the Axes
ax.add_patch(rect)
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

### Colors

```python
c1 = plt.cm.Dark2(0)
c2 = plt.cm.Dark2(1)
c3 = plt.cm.Dark2(2)
```

https://matplotlib.org/stable/gallery/color/colormap_reference.html
![[Pasted image 20221110150056.png]]

### Iterate on color
```python
color = iter(cm.rainbow(np.linspace(0, 1, n)))
for i in range(n):
   c = next(color)
   plt.plot(x, y, c=c)
```

### Overwrite the cycling of color 

```python
ax.set_prop_cycle('color',plt.cm.Dark2.colors)
```

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

### Interactive plot

``` python
%matplotlib widget
fig, ax = plt.subplots(figsize=(6, 4))
ax.set_ylim([-4, 4])
ax.grid(True)
 
# generate x values
x = np.linspace(0, 2 * np.pi, 100)

def my_sine(x, w, amp, phi):
    """
    Return a sine for x with angular frequeny w and amplitude amp.
    """
    return amp*np.sin(w * (x-phi))
 

@widgets.interact(w=(0, 10, 1), amp=(0, 4, .1), phi=(0, 2*np.pi+0.01, 0.01))
def update(w = 1.0, amp=1, phi=0):
    """Remove old lines from plot and plot new one"""
    [l.remove() for l in ax.lines]
    ax.plot(x, my_sine(x, w, amp, phi), color='C0')
```

## How to read a pickle file

``` python
import jpype
jpype.startJVM(jpype.getDefaultJVMPath())

import pickle

with open('filename.p', 'rb') as f:
    data = pickle.load(f)
```


``` python
with open('filename.pickle', 'wb') as handle:
    pickle.dump(a, handle, protocol=pickle.HIGHEST_PROTOCOL)
```


## Loop through filenames in a directory

```python
start_path = "/eos/home-e/eljohnso/SWAN_projects/acc-models-tls-eliott-fork/ps_extraction/east-fast-extraction/pickle/"
end_path = ""
mypath = start_path+"/"+end_path

f = []
for (dirpath, dirnames, filenames) in walk(mypath):
    f.extend(filenames)
    break
filenames
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

## NXCALS

See [[MWPC#Simple SWAN python script for NXCALS]]

``` python
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from nxcals.api.extraction.data.builders import *
from scipy.optimize import curve_fit
from datetime import datetime

# build the query and load data into spark dataframe UTC Time
start = "2022-09-28 11:00:00.000"
end = "2022-09-28 17:00:00.000"
df = DevicePropertyDataQuery.builder(spark).system("CMW").startTime(start).endTime(end).entity().parameter("F61.BLM008-ST/Samples").build().toPandas()

df.head(1)

df.selector.unique()

df.loc[df.selector == "CPS.USER.MD4"]
```

## Scipy

``` python
from scipy import stats
res = stats.linregress(x, y)
ax.plot(x, res.intercept + res.slope*x, 'r', label='fitted line')
```

### Integral of a curve

``` python
from scipy.interpolate import InterpolatedUnivariateSpline

f = InterpolatedUnivariateSpline(df.t, -df.signal_23_I1, k=1)
    intensity = f.integral(200,800)
```

## Fit a gaussian

```python
from scipy.optimize import curve_fit

def gaussian_function(x, a, I, mu, sig):
    return a + I / np.sqrt(2 * np.pi * sig ** 2) * np.exp(-(x - mu) ** 2 / 2. / sig ** 2)

def do_gaussian_fit(x,y):
    mu = np.average(x, weights=np.abs(y - np.min(y)))
    sigma = np.sqrt(np.average(x**2, weights=np.abs(y - np.min(y))) - mu**2)
    p0 = [y.min(), (np.max(y) - np.min(y)) * np.sqrt(2 * np.pi * sigma**2), mu, sigma]
    popt, pcov = curve_fit(gaussian_function, x, y, p0=p0, maxfev=1000) # maxfev is the number of tries it does the fit
    return popt, pcov

x = [1,2,3]
y = [1,2,1]

popt, pcov = do_gaussian_fit(x,y)
ax.plot(x, gaussian_function(x, popt[0], popt[1], popt[2], popt[3]))

```
