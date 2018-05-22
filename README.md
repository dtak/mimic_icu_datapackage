# mimic_icu_datapackage

Public resource for a curated dataset for a supervised time-series machine learning task based on intervention-forecasting in the ICU.

## Contents

We expect data to come from 4 distinct sources. Each data source should have its own .csv file containing the data itself (one row per patient/hour). Each data source also has its own .json file providing metadata of what the columns in the .csv file mean.

Currently, in this repo we provide json metadata only for these sources (we can't share mimic data on the public web).

* Static patient data (demographics, weight-at-admission, etc)
    * [static_patient_data_spec.json](static_patient_data_spec.json)
    * static_patient_data.csv
* Hourly data from bedside sensors
    * [bedside_sensor_hourly_data_spec.json](bedside_sensor_hourly_data_spec.json)
    * bedside_sensor_hourly_data.csv
* Hourly data from lab tests
    * [lab_test_hourly_data_spec.json](lab_test_hourly_data_spec.json)
    * lab_test_hourly_data.csv
* Hourly data of applied interventions (e.g. ventilator, vasopressor)
    * [outcome_hourly_data_spec.json](outcome_hourly_data_spec.json)
    * outcome_hourly_data.csv

NOTES:

For MIMIC data, we use **nurse-validated** vital signs which are preprocessed to a regular hourly interval, as suggested by Marzyeh's past work. For other datasets, we might consider a much finer-scale if data is available at such scales.

Many lab tests are missing (not measured every hour). These should just be marked as `nan` in the .csv file.

## Dataset format

This dataset format (raw data in related .csv files, metadata in .json files) is our attempt to use the **datapackage** format described at https://frictionlessdata.io/data-packages/.

## References

For an example paper using this kind of data, see our AMIA CRI 2017 paper:

```
Predicting intervention onset in the ICU with switching state space models
Marzyeh Ghassemi*, Mike Wu*, Michael C. Hughes*, Peter Szolovits, Finale Doshi-Velez
AMIA CRI 2017
https://www.michaelchughes.com/papers/GhassemiWuHughesEtAl_AMIACRI2017.pdf
```


