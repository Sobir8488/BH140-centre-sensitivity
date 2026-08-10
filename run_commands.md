# Reproduction commands

Use these commands from the root of the extracted package. Update paths if running on Windows.

```bash
python -m pip install -r requirements.txt
python code/01_build_membership_catalog.py --outdir results_BH140_multisurvey_validation
python code/02_threshold_and_control_field_checks.py --outdir results_BH140_multisurvey_validation --download-controls --analyze
python code/03_bootstrap_control_validation.py --outdir results_BH140_multisurvey_validation --download-controls --analyze --bootstrap-iter 10000
python code/04_hst_winered_phase_space_validation.py --outdir results_BH140_multisurvey_validation --analyze --isochrone-csv data/external_derived/isochrone_bh140_mist_v1p2_acswfc_feh_m1p00_logage_10p10.csv --completeness-csv data/external_derived/mgcs_bh140_f814w_artificial_star_completeness.csv
```

The archived results in this package are already generated. Online catalog queries can depend on service availability.
