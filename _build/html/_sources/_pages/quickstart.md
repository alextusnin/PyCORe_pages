(quickstart)=
# Quickstart with the single-resonator solver

First, we need to import all the necessary libraries
```python
import matplotlib.pyplot as plt
import numpy as np
import sys,os
PyCore_dir = os.path.dirname('PATH to your PyCORe folder')
sys.path.append(PyCore_dir)
import PyCORe_main as pcm
```

Then, we define the dispersion parameters:
* Number of frequency modes used in the simulations
```python
Num_of_modes = 2**9
mu = np.arange(-Num_of_modes/2,Num_of_modes/2)
```
and the array of comb indexes $\mu$
* Group velocity dispersion $D_2 = -\beta_2*...$ in $2\pi\,\cdot$ Hz
```python
D2 = 4.1e6*2*np.pi
```
that then defines the integrated dispersion profile ($D_\mathrm{int}$)
```python
Dint = 2*np.pi*(mu**2*D2/2)          
```
:::{note}
To take into account higher order dispersion orders, you just need to define $D_3,\, D_4,...$
and redefine $D_\mathrm{int} = D_2 \frac{\mu^2}{2} + D_3 \frac{\mu^3}{3!} + D_4 \frac{\mu^4}{4!} + ...$
:::