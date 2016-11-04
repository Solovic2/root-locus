# Root Locus (Graphical Tool)

<p align="center">
 <img src="/img/rl.png" alt="Drawing" style="width: 100px;"/>
</p>

This is a fun little weekend project I worked on for my *Modern Control* class. 

It is a python implementation of the Root Locus Design Method. The RL plots the location of the roots of the characteristic equation of the closed-loop transfer function as the gain K is varied from 0 to infinity. 

## Requirements

- Python 2+, 3+
- numpy
- matplotlib
- seaborn (optional)

## How To Use

Enter the coefficients of the numerator and denominator of the open loop transfer function as lists `num = []` and `denum = []`. The denominator must have all coefficients entered (even the terms with 0 coefficients) but it doesn't have to be explicitely written out for the numerator.


Now invoke the `transfer_function` method, compute the roots of the TF using `compute_roots`, and finally plot with `plot_root_locus`.

**Example**

```python
num = [1]
denum = [1, 3, 2, 0]

GH = transfer_function(num, denum)

# create a list of evenly spaced gains
gains = np.linspace(0.0, 10.0, num=500)

roots = compute_roots(GH, gains)
real_vals = np.real(roots)
imag_vals = np.imag(roots)
fig, ax = plot_root_locus(gains, roots)
plt.show()
```

## References   

- [python-control](https://pypi.python.org/pypi/control/0.7.0) - helped me get a sense of how to go about the problem.
- [Bicycle Control Design](https://plot.ly/ipython-notebooks/bicycle-control-design/) - great blog post
