# First-Data-Cleaning-


Worldwide Travel Cities – Climate & Ratings (Cleaned Dataset)

This project processes and transforms data from the [Worldwide Travel Cities Ratings and Climate dataset on Kaggle](https://www.kaggle.com/datasets/furkanima/worldwide-travel-cities-ratings-and-climate), preparing it for further analysis and modeling.

Dataset Cleaning & Transformation

The notebook script performs the following actions:

1. Data Load:
   - Reads the CSV file containing city-level travel metadata and climate summaries.

2. ID Simplification:
   - Replaces UUID strings in the `id` column with unique integer identifiers for simplicity.

3. Column Pruning:
   - Removes columns not needed for modeling:
     - `short_description`
     - `longitude`
     - `latitude`

4. Climate Aggregation:
   - Parses the `avg_temp_monthly` JSON string containing 12 months of temperatures.
   - Calculates the **annual average temperature** and stores it in a new column `avg_temp`.

5. Trip Duration Simplification:
   - Parses the JSON-formatted `ideal_durations` list.
   - Selects the **longest travel duration** based on a custom ranking:
     ```
     Day trip < Short trip < Weekend < One week < Long trip
     ```

6. Final Export:
   - Outputs a cleaned CSV file named `cleaned_dataset.csv`.

Files

- `your_script_name.py` — Python script performing the transformations
- `cleaned_dataset.csv` — Cleaned dataset with simplified fields
- `README.md` — Documentation (this file)

New Columns Summary

| Column           | Description                               |
|------------------|-------------------------------------------|
| `id`             | Unique numeric ID per city                |
| `avg_temp`       | Annual average temperature in °C          |
| `ideal_durations`| Single most suitable duration per city    |
