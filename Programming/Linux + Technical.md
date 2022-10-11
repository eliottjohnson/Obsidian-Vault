### Show the tempfile in MAD-X
```python
with open('tempfile', 'r') as f:
    lines = f.readlines()
    for ele in lines:
        print('{}'.format(ele))
```
