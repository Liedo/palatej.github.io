---
layout: left-menu
title: State space framework
tagline: technical documentation for JDemetra+ using GitHub Pages
description: State space framework
order: 0
---

# State space model

The `general linear gaussian` state-space model can be written in many different ways. The measurement equation and the state equation considered in JD+ 3.0 are presented below.

$$ y_t = Z_t \alpha_t + \epsilon_t,\quad \epsilon_t \sim N\left(0, \sigma^2 H_t\right), t \gt 0 $$

$$ \alpha_{t+1} = T_t \alpha_t + \mu_t, \quad \mu_t \sim N \left(0, \sigma^2 V_t \right), t \ge 0$$

<br>

$y_t$  is the observation at period t, 
$\alpha_t$  is the state vector.
$\epsilon_t, \mu_t$ are assumed to be serially independent at all time points and independent between them at all time points.  

The residuals of the state equation will be modelled as

$$ \mu_t = S_t \xi_t, \quad \xi_t \sim N\left( 0, \sigma^2 I\right) $$

In other words, $V_t=S_t S_t'$

The initial ($\equiv t=0$) conditions of the filter are defined as follows:

$$ \alpha_{0} = a_{0} + B\delta + \mu_{0}, \quad \delta \sim N\left(0, \kappa \sigma^2 I \right),\: \mu_{0} \sim N\left(0,\sigma^2 P_*\right)$$

where  $\kappa$ is arbitrary large. $P_*$ is the variance of the stationary part of the initial state vector and $BB'= P_\infty$
models the diffuse part. 

The definition used in JD+ is quasi-identical to that of Durbin and Koopman[1].

In summary, up to the scaling factor $\sigma^2$, the model is completely defined by the following quantities (possible default values are indicated in brackets):

$$ \mathbf{Z_t}, \mathbf{H_t} [=0] $$

$$ \mathbf{T_t}, \mathbf{V_t} [=S_t S_t'], \mathbf{S_t} [=Cholesky(V)] $$ 

$$ \mathbf{a_{-1}}[=0], \mathbf{P_*} [=0], \mathbf{B} [=0], \mathbf{P_\infty} [=BB'] $$

#### Bibliography

[1] _DURBIN J. AND KOOPMAN S.J._ (2012): "Time Series Analysis by State Space Methods", second edition. Oxford University Press.
