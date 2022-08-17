# Particle distributions

A few ways to create a distribution of particles:

``` python
mu, sigma = 0, 0.01 # mean and standard deviation
s = np.random.normal(mu, sigma, 100)

fig, ax = plt.subplots(figsize=(3,2))

# Plot the histogram and save parameters
count, bins, ignored = ax.hist(s, 40, density=True)
# Plot the fit
ax.plot(bins, 1/(sigma * np.sqrt(2 * np.pi)) *
               np.exp( - (bins - mu)**2 / (2 * sigma**2) ),
         linewidth=2, color='r')
```
![](https://codimd.web.cern.ch/uploads/upload_bbd4c5d8f74bd04f914187e6b61c42cf.png)



[Confidence ellipse code](https://matplotlib.org/stable/gallery/statistics/confidence_ellipse.html)