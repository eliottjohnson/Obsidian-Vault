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