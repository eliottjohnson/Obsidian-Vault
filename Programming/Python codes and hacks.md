# Python codes and hacks


Mask matrices of several dimensions
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

## Concatenate two dataframes

```python
d = {'number_of_particle': [1], 'number_of_turns': [2], 'time': [3]}
df1 = pd.DataFrame(data=d)

d = {'number_of_particle': [4], 'number_of_turns': [5], 'time': [6]}
df2 = pd.DataFrame(data=d)

df = pd.concat([df1,df2])
```

## Plotting

## Save a figure

```python
plt.savefig("filename.png", facecolor='white', transparent=False, dpi = 150, bbox_inches='tight')
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