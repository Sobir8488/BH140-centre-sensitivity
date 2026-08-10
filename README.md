DOI: 10.5281/zenodo.21869507
# BH 140 Multi-Survey Validation Package v1.0

This repository is a DOI-ready release package supporting a multi-survey validation analysis of the Galactic globular-cluster system BH 140. It contains reproduction scripts, derived data products, matched-control bootstrap products, HST/MGCS artificial-star completeness products, HST mass-function diagnostic products, WINERED source-level crossmatch products, and manuscript-ready summary tables and figures.

## Main supported statements

- The Gaia DR3 anchored membership sample contains 3978 high-probability BH 140 members.
- The outer Gaia-selected population is a control-supported candidate outer tidal structure. In the final matched-control bootstrap validation, the target values are R1 = 0.751873 and R2 = 0.446238, compared against 12 matched Gaia control fields and 120000 bootstrap realizations.
- The HST/MGCS layer includes the recovered BH 140 artificial-star completeness curve and a MIST ACS/WFC isochrone. It provides a completeness-corrected central lower-main-sequence mass-function diagnostic.
- The current HST mass-assigned sample has 187 valid sources, all in the inner radial bin used by the script; therefore this package does not support a radial mass-segregation claim.
- The WINERED layer is cross-matched at the source level to seven Gaia-selected sources and provides spectroscopic validation support.
- The phase-space Monte Carlo summary is included. Full orbit integration is not included in this release.
- The package does not claim a confirmed tidal tail, a new internal radial-velocity dispersion, a metallicity distribution, or a radial mass-segregation detection.

## Directory structure

```text
code/                         Reproduction scripts with neutral file names
data/external_derived/        MIST isochrone and MGCS completeness curve
data/processed/               Membership, crossmatch, and processed validation inputs
data/raw_filtered/            Filtered public-source extracts used for auditability
results/                      Final validation outputs and figures
manuscript_tables/            Small tables intended for paper drafting
provenance/                   Data-source and processing provenance
```

## Minimal reproduction sequence

The scripts were developed for Python 3.12. Install dependencies with:

```bash
python -m pip install -r requirements.txt
```

Then run the analysis stages in order, adjusting paths as needed:

```bash
python code/01_build_membership_catalog.py --outdir results_BH140_multisurvey_validation
python code/02_threshold_and_control_field_checks.py --outdir results_BH140_multisurvey_validation --download-controls --analyze
python code/03_bootstrap_control_validation.py --outdir results_BH140_multisurvey_validation --download-controls --analyze --bootstrap-iter 10000
python code/04_hst_winered_phase_space_validation.py --outdir results_BH140_multisurvey_validation --analyze --isochrone-csv data/external_derived/isochrone_bh140_mist_v1p2_acswfc_feh_m1p00_logage_10p10.csv --completeness-csv data/external_derived/mgcs_bh140_f814w_artificial_star_completeness.csv
```

The archived `results/` directory contains the release outputs used for the associated manuscript. Re-running the scripts may produce small numerical differences where online catalog services update query behavior or where random seeds are changed.

## Important modelling notes

The MIST isochrone included here is a baseline MIST v1.2 ACS/WFC synthetic-photometry isochrone with `[Fe/H] = -1.00`, `log10(age/yr) = 10.10`, and distance modulus for 4.81 kpc. The baseline file was generated with zero extinction offsets in the conversion script. Final astrophysical interpretation should test reddening and age-metallicity sensitivity.

The MGCS artificial-star completeness curve is derived from the BH 140 filtered `phot-io` table. The mass-function result should be used as a central diagnostic layer because the valid mass-assigned sample does not populate the outer radial bin in this release.

## Citation

If this package is used, cite the Zenodo DOI assigned to this release and the original data providers listed in `provenance/data_sources.md`.
