## README

This repository contains some of the data used to produce the figures in [Dynamically generated concatenated codes and their phase diagrams](https://arxiv.org/abs/2409.13801) by Grace M. Sommers, David A. Huse, and Michael J. Gullans. For additional data and the code used to generate it, please contact gsommers@princeton.edu.

### depol/

**Data under depolarizing surface noise**

- `opt_surface_{n}.jld2` [Fig. 2]
- `bell_surface_{n}.jld2` [Fig. S4, S5a]
- `rand_surface_{n}.jld2` [Fig. S5b]

Each of these files is a dictionary with two keys:

 - "fail": dictionary with (key, value) pairs where key is $p_x=p_y=p_z=p/3$, and value is average failure probability over time, for independent runs where each population has m elements.
 - "n": population size

### bulk/

**Data under unheralded bit and phase flips, bulk of Bell tree**

- `thresholds.jld2` [Fig. 3a] dictionary of the q-dependent thresholds $p_cx(q)$, $p_cz(q)$.
         e.g. $p_cx(q) =$ thresholds["X"][q][1] $\pm$ thresholds["X"][q][2]
- `fixed_points.jld2` [Fig. 3b] stable and unstable fixed points
- `bulk_{n}.jld2` [Fig. 3c]: dictionary with two keys:
  * "fail": $P_x(q,q,t)$ at even times, $P_z(q,q,t)$ at odd times, in independent runs with 2 populations, averaged over n elements each. So $P_X(q,q,tau) = `data[q]["fail"][:,:,2*tau]`. First dimension is 2 populations per run, second dimension is N independent runs.
  *  "mutual": 1 - mutual information between root and leaves. (i.e., mutual information lost to environment). $I(R:E)=1$ at the noncoding fixed point.
- `Z_400000_p.jld2`, `X_400000_p.jld2`: dictionaries with same keys as `bulk_{n}.jld2`, but now containing data from different surface error rates $p$ at each bulk rate $q$. i.e. `data["fail"][q]` and `data["mutual"][q]` are both dictionaries whose keys are p. Used to determine the thresholds in Fig. 3a, and the rate of exponential convergence in Fig. S7.
- Please contact gsommers@princeton.edu for large data files containing the full distribution of $m_x$, $m_z$ at the coding fixed point [Fig. 4 and Fig. S9].

### dists/

**Conditional code distances, heralded errors in the bulk of the Bell tree**
- `conditional_dists.jld2` [Fig. 8b]: dictionary with mean conditional distance conditioned on survival, $d(q,q,\tau)$ ("means"), and $d_{peak}(q,q,tau)$ ("maxs"). Large data file containing the full distribution, used to prepare Fig. S13, available upon request.
- `dist_scaling_X.jld2`: dictionary with fits to $\lambda(q)$ in $d(q,q,tau) \propto \lambda(q)^\tau$ ("means") and $d_{peak}(q,q,tau)$ ("maxs"). Different fits were performed for integer and half-integer tau, yielding `[[fit, err1], [fit2, err2]]`. The logarithm of the average across fits is plotted in Fig. 8c. 
