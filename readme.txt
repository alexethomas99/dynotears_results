---
Readme
---

Description: Results for DYNOTEARS executions in IEEE submission.
Size: 1.97 GB
Platform: Any modern operating system
Environment: Any modern operating system
Major component description: "results" contains the main results; "timing" contains the results for the timing experiments. See below for folder structure.
Detailed setup instructions: N/A
Detailed run instructions: N/A
Output description: N/A
Contact information: Alex.Thomas@soton.ac.uk

---
File structure
---

This is the structure of the files in this folder. If anything is unclear please feel free to contact me at Alex.Thomas@soton.ac.uk.

Results CSV headers:
number: which run of the optimisation algorithm it was.
iteration: which iteration of DYNOTEARS we're on. This increments every time a new value of (lam_w, lam_a, p) is tried, but there will be many taus.
budget: the number of iterations DYNOTEARS is allowed to run for, always 5000.
true_p: the true model order used to generate the data.
lam_w: value of the \lambda_W L1 hyperparameter.
lam_a: value of the \lambda_A L1 hyperparameter.
tried_p: the model order tried in this DYNOTEARS execution.
w_threshold: the tried threshold.
obj: value of the objective function. Note this is negative so that methods involving maximisation may be used
mse: mean squared error **of the reproduced data** (not the adjacency matrices.)
auc: only for models with the correct guess of p, the AUC of the learned adjacency matrices compared with the adjacency matrices used to generate the data.
n_iter: how many iterations DYNOTEARS actually ran for.

Timing file headers:
part: grid search is run in parallel, with the hyperparameter choices divided into parts. This is which part this was in. Only for grid search.
n_vars: number of variables
true_p: the true model order used to generate the data.
time: time in seconds to evaluate.

File structure:
results
- {method}
-- results
--- {dataset}
---- {number of variables}
----- {true model order}
------ {run}.csv: all DYNOTEARS evaluations for a particular run of the optimisation method.
------ {run}_best.csv: just the results with the value of tau (threshold) that minimises the objective function.

timing
- {method}: for grid, each run is in a separate folder titled grid_{run}.
-- results
--- {dataset}
---- {number of variables}
----- {true model order}
------ {run}.csv: all DYNOTEARS evaluations for a particular run of the optimisation method.
------ {run}_best.csv: just the results with the value of tau (threshold) that minimises the objective function.
--- time_{run}.txt: the clock time recorded for the run.