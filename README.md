# Tmatrix - simple, efficient implementation of Transfer Method for multilayer stacks

## 1. What is the Transfer Method?

It is possible to simulate the propagation of light through multilayered media using the transfer matrix method. Simply, this involves assigning each interface/layer a matrix and then multiplying these terms together.

Let us assume we have a plane wave propagating in the forward direction ($+z$):

$$
\begin{equation*}
E^{+}(z) = E^{+}(0)e^{ik_{z}z}
\end{equation*}
$$

where in this equation $E^{+}(z)$ means the electric field of the wave is propagating to the right and $k_{z}$ is the $z$ componenent of the wavevector of the plane wave, which is equal to

$$
\begin{equation*}
k_{z} = k_{0}ncos(\theta) = \frac{2\pi}{\lambda_{0}}ncos(\theta)
\end{equation*}
$$

where $n$ is the refractive index of the medium, $\theta$ is the angle of incidence and $\theta_{0}$ is the wavelength of the light in a vacuum. 

## Propagation Matrix

We can use matrices to calculate the situation in which waves are propagating both forward (defined as to the right, $+z$) and backwards (defined as to the left, $-z$) through a layer of thickness $d$:

$$
\begin{align*}
E^{+}(d) &= E^{+}(0)e^{ik_{z}d} \\
E^{-}(d) &= E^{-}(0)e^{-ik_{z}d}
\end{align*}
$$

Alternatively we can write this in matrix form as 
```math
\left[ 
    {\begin{array}{cc}
    E^{+}(d) \\
    E^{-}(d) \\
  \end{array} } 
\right]
```
$$
\begin{align*}

  \left[ {\begin{array}{cc}
    E^{+}(d) \\
    E^{-}(d) \\
  \end{array} } \right] = \left[ {\begin{array}{cc}
    e^{ik_{z}d} & 0 \\
    0 & e^{-ik_{z}d} \\
  \end{array} } \right]\left[ {\begin{array}{cc}
    E^{+}(0) \\
    E^{-}(0) \\
  \end{array} } \right]

\end{align*}
$$

Since we want subsequent matrices to be inserted on the right we will invert the form of this matrix equation to

$$
\begin{align*}

  \left[ {\begin{array}{cc}
    E^{+}(0) \\
    E^{-}(0) \\
  \end{array} } \right] = \left[ {\begin{array}{cc}
    e^{-ik_{z}d} & 0 \\
    0 & e^{ik_{z}d} \\
  \end{array} } \right]\left[ {\begin{array}{cc}
    E^{+}(d) \\
    E^{-}(d) \\
  \end{array} } \right]

\end{align*}
$$

Let us now define the **transfer(propagation) matrix**, $T^{(prop)}$ as 

$$
\begin{align*}

  T^{(prop)} = \left[ {\begin{array}{cc}
    e^{-ik_{z}d} & 0 \\
    0 & e^{ik_{z}d} \\
  \end{array} } \right] = \left[ {\begin{array}{cc}
    e^{-ik_{0}dncos(\theta)} & 0 \\
    0 & e^{ik_{0}dncos(\theta)} \\
  \end{array} } \right]

\end{align*}
$$