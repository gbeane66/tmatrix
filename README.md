# Tmatrix - simple, efficient implementation of Transfer Method for multilayer stacks

## 1. What is the Transfer Method?

It is possible to simulate the propagation of light through multilayered media using the transfer matrix method. Simply, this involves assigning each interface/layer a matrix and then multiplying these terms together.

Let us assume we have a plane wave propagating in the forward direction (+z):

$$
\begin{equation}
E^{+}(z) = E^{+}(0)e^{ik_{z}z}
\end{equation}
$$