# Data dictionary

## Core result tables

- `results/membership/membership_structural_summary.json`: Gaia membership and structural summary.
- `results/outer_structure/bootstrap_control_summary.csv`: matched-control bootstrap summary for the outer angular statistics.
- `results/outer_structure/bootstrap_control_distribution.csv.gz`: bootstrap control distribution for R1 and R2.
- `results/hst_mass_function/hst_mass_function_summary.csv`: HST/MGCS mass-function diagnostic summary.
- `results/hst_mass_function/hst_mass_function_bins.csv`: completeness-corrected mass-function bins.
- `results/winered/winered_crossmatch_summary.csv`: WINERED source-level crossmatch summary.
- `results/phase_space/phase_space_monte_carlo_summary.csv`: phase-space Monte Carlo summary.

## Key column meanings

- `target_R1`: one-sided Rayleigh statistic for outer members.
- `target_R2`: axial statistic using twice the position angle.
- `bootstrap_fp_R1`, `bootstrap_fp_R2`: empirical false-positive rates from matched-control bootstrap samples.
- `valid_mass_n`: number of HST/MGCS crossmatched sources with valid mass assignments.
- `alpha_inner`, `alpha_outer`: fitted mass-function slopes for the radial subsets used by the script.
- `winered_crossmatch_n`: number of WINERED rows cross-matched to the Gaia-selected sample.
- `Rgc_kpc_median`, `vR_kms_median`, `vphi_kms_median`, `vz_kms_median`, `Lz_kpc_kms_median`: median phase-space quantities from the Monte Carlo calculation.
