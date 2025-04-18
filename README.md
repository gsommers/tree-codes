
### depol/

Data under depolarizing surface noise
    * `opt_surface_{n}.jld2` [Fig. 1]
    * `bell_surface_{n}.jld2` [Fig. S4, S5a]
    * `rand_surface_{n}.jld2` [Fig. S5b]

Each of these files is a dictionary with two keys:
    * `fail`: dictionary with (key, value) pairs where key is p_x=p_y=p_z=p/3, and value is average failure probability over time, for independent runs where each population has m elements.
    * `n`: population size

### bulk/

Data under unheralded bit and phase flips, bulk of Bell tree
    * `thresholds.jld2` [Fig. 3a] dictionary of p_cx(q), p_cz(q).
         e.g. p_cx(q) = thresholds["X"][q][1] $\pm$ thresholds["X"][q][2]
    * `fixed_points.jld2` [Fig. 3b] stable and unstable fixed points
    * `bulk_{n}.jld2` [Fig. 3c] Dictionary with two keys:
         - "fail": P_x(q,q,t) at even times, P_z(q,q,t) at odd times, in independent runs with 2 populations, averaged over n elements each. So data[q]["fail"][:,:,2:2:end] is P_X(q,q,tau). First dimension is 2 populations per run, second dimension is N independent runs.
	 - "mutual": 1 - mutual information between root and leaves. (i.e., mutual information lost to environment). =1 at noncoding fixed point.
    * "Z_400000_p.jld2", "X_400000_p.jld2": Dictionaries with same keys as bulk_{n}.jld2. Now data["fail"][q] and data["mutual"][q] are both dictionaries whose keys are p, the surface error rate.
    
    *  "distr_X_q.jld2" distribution of m_x in approximate steady state, at q=0.001, coding phase.
         Please contact gsommers@princeton.edu for other q.

### dists/
Conditional code distances
    * `conditional_dists.jld2` [Fig. 8b, Fig. S13]: dictionary with distribution at each time step ("distr"), mean conditional distance ("means"), and d_peak(q,q,tau) ("maxs")
    - `dist_scaling_X.jld2` [Fig. 8c, S13]: dictionary with fits to d(q,q,tau) \propto t^alpha ("means") and d_peak(q,q,tau) ("maxs"). Different fits were performed for integer and half-integer tau, yielding [[fit1, err1], [fit2, err2]]
