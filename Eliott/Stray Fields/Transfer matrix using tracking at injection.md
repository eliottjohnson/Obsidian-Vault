## Transfer matrix using tracking at injection

Idea is to take the kick_response_BTP_injection_loop.ipynb notebook, launch tracks at different $x_{in}$ and look at the $x_{out}$. Then do the same for $y$, $x'$ and $y'$.

[Source code: kick_response_BTP_injection_loop_transfer_matrix.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/EliottBranch/ps_injection/kick_response_injection_tracking/kick_response_BTP_injection_loop_transfer_matrix.ipynb)

![](https://codimd.web.cern.ch/uploads/upload_d7ea188a06c9ad98a11f650213a2929f.png)

Wide scan (out of vaccum chamber) to see if non-linear.

![](https://codimd.web.cern.ch/uploads/upload_64a9f5bdf9bd348ec9a930e5a399b5ef.png)

![](https://codimd.web.cern.ch/uploads/upload_5711d46da2c5f2f9182be72377365deb.png)

My technique to build a transfer matrix:
[Source code: kick_response_BTP_injection_loop_transfer_matrix.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/c57c6a55f6ad5f466ce992f8fee29120e5dbc87a/ps_injection/kick_response_injection_tracking/kick_response_BTP_injection_loop_transfer_matrix.ipynb)
* I launch 4 different kind of input offset: $x_{in}$, $px_{in}$, $y_{in}$, $py_{in}$.
* I record the the output offset: $x_{out}$, $px_{out}$, $y_{out}$, $py_{out}$.

![](https://codimd.web.cern.ch/uploads/upload_966a72815f63e169a33c86ec34dfecc4.png)


I've added a fit to the transfer matrix points and this is only for the tracking portion (not up to the SEM-grid).

![](https://codimd.web.cern.ch/uploads/upload_fa9381a4bb8e6e624722dbc4a612a26f.png)

if I put all the slopes in a matrix I get this:

```
array([[ 1.13238970e+00,  4.75497673e+00,  0.00000000e+00,
         0.00000000e+00],
       [ 1.00769544e-01,  1.31380884e+00,  2.11758237e-19,
         0.00000000e+00],
       [-1.32358650e-19, -1.51240746e-18,  8.71757704e-01,
         4.12412532e+00],
       [-2.83679450e-19, -4.08844355e-18, -9.00749616e-02,
         7.26157802e-01]])
```

Which is really cool because it's very close to what Ewa and her function find (```tracks.get_transport_matrix(k = k_last, ret = 'mat')```) !
She has the 6x6 matrix but now I have confidence that both matrix are correct.

```
array([[ 1.13060752e+00,  4.73100926e+00,  0.00000000e+00,
         0.00000000e+00, -0.00000000e+00,  1.28430844e-02],
       [ 1.00825480e-01,  1.30665578e+00,  0.00000000e+00,
         0.00000000e+00, -0.00000000e+00,  1.15635272e-02],
       [ 7.90180637e-20, -4.00499449e-19,  8.71461510e-01,
         4.12397871e+00, -0.00000000e+00,  2.39903317e-19],
       [ 3.90509983e-19, -1.02825487e-18, -9.10317236e-02,
         7.16716626e-01, -0.00000000e+00,  7.18893700e-19],
       [-1.31185575e-02, -4.22979055e-02,  0.00000000e+00,
         0.00000000e+00,  1.00000000e+00,  8.81050098e-01],
       [ 4.17230911e-13,  1.78813248e-13,  0.00000000e+00,
         0.00000000e+00, -0.00000000e+00,  1.00000000e+00]])
```

![](https://codimd.web.cern.ch/uploads/upload_302b207cc05024736eed9c679804d122.png)

I can also compare how it compares only in the MU41 and up to the SEM-Grid.

![](https://codimd.web.cern.ch/uploads/upload_c6688b1e0dde013f3734ea195c704e7e.png)

Conclusion: I don't need to do this expensive computational tracking. I can just track the nominal and use Ewa's function. (Altough let's remember it's only valid for the tracking part, not up to the SEM-Grid).

### Evolution of the transport matrix with POPS

[Source code: kick_response_BTP_injection_loop_transfer_matrix_function_of_POPS.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/EliottBranch/ps_injection/kick_response_injection_tracking/kick_response_BTP_injection_loop_transfer_matrix_function_of_POPS.ipynb)

![](https://codimd.web.cern.ch/uploads/upload_2bf5ad9c14b0299f7ac974e8c87bf533.png)

![](https://codimd.web.cern.ch/uploads/upload_5d2d145ecebf952dc02f008f8f8b188c.png)


Conclusion: We see that injection angles are very sensitive to POPS change. Twice as much as x or y offsets. This means that:
* if you increase POPS, a change in angle px will have a big effect on the x offset.
* R21, R22 change the most in positive way that's px_in/x_out, px_in/px_out
* R34, R44 change the most in negative way that's py_in/y_out, py_in/py_out

### Using the transfer matrices in MADX to calculate beam size