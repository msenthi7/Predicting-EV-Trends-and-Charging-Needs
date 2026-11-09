# Watt's Next? Predicting EV Range and Mapping Adoption in Washington State

An end-to-end data science project on Washington State electric vehicle registrations, covering data cleaning, exploratory analysis, hypothesis testing, predictive modeling and geospatial mapping.

**Team:** Abhishek Rithik Origanti and Matheshwara Annamalai Senthilkumar

All code and outputs are in [`Tutorial.ipynb`](Tutorial.ipynb).

## Main result

A tuned Random Forest raised held-out R² for electric range prediction from **0.776** with a linear baseline to **0.918**, using only model year and manufacturer as features.

## Data

The source is the Washington electric vehicle population dataset from Kaggle (`Electric_Vehicle_Population_Data-2.csv`). The CSV is not stored in this repository.

| Step | Rows | Columns |
| --- | ---: | ---: |
| Raw data | 216,772 | 17 |
| Dropped 6 columns not used in the analysis | 216,772 | 11 |
| Removed 124,101 rows with a range of 0 and 19 with no range | 92,652 | 11 |
| Dropped remaining rows with missing values | 92,645 | 11 |

Electric range was then min-max scaled to 0–1, so the error values in the notebook are on that scale.

## Exploratory findings

Within the 92,645 cleaned records:

- **Geography:** King County has 44,618 registrations, about 48% of the total. Snohomish County is next with 9,636. Seattle is the top city with 15,347.
- **Manufacturers:** Tesla leads with 25,296 vehicles, followed by Nissan with 10,455 and Chevrolet with 9,756.
- **Models:** The Tesla Model 3 (13,726) and Nissan Leaf (10,455) are the most common.
- **Incentive eligibility:** 76.4% of vehicles are eligible for Clean Alternative Fuel Vehicle (CAFV) status (70,823 eligible, 21,822 not eligible).

## Hypothesis tests

| Question | Test | Statistic | p-value |
| --- | --- | --- | --- |
| Does electric range differ between battery EVs and plug-in hybrids? | t-test | t = 477.954 | < 0.001 |
| Is county associated with vehicle type? | Chi-square | χ² = 1031.238, df = 154 | < 0.001 |

## Models

| Target | Model | Features | Train/val/test | Test result |
| --- | --- | --- | --- | --- |
| Electric range | Linear Regression | Model Year, Make | 60/20/20 | R² = 0.776 (5-fold CV mean 0.775) |
| Electric range | Random Forest with GridSearchCV | Model Year, Make | 80/20 train/test | **R² = 0.918** |
| CAFV eligibility | Logistic Regression | Electric Range, Model Year | 60/20/20 | Accuracy = 99.86% |
| CAFV eligibility | Logistic Regression with SMOTE | Electric Range, Model Year | 80/10/10 | Accuracy = 98.05% |
| Battery EV vs plug-in hybrid | Logistic Regression with SMOTE | Electric Range, Model Year | 60/20/20 | Accuracy = 98.42% (5-fold CV mean 98.43%) |

SMOTE was applied to the training data only. In the Random Forest, manufacturer had an importance of about 0.6 and model year about 0.4.

### How to read these results

- **Electric range:** The split was random, so the same manufacturer and model year combinations appear in both training and test data. The R² shows how well the model captures range across known combinations. It does not show how well it would forecast future vehicles.
- **CAFV eligibility:** Eligibility depends on battery range, and range is an input feature. The high accuracy mostly reflects that rule, so this model is a consistency check and not evidence of hard predictive skill.
- **Vehicle type:** Battery EVs and plug-in hybrids differ sharply in electric range, which makes this an easy classification task.

## Geospatial analysis

Vehicle coordinates were parsed from the `Vehicle Location` field and mapped as interactive Folium heatmaps. Registered EVs are most concentrated around Seattle, Bellevue and Tacoma, with lower density in rural areas and in central and eastern Washington.

The data contains no charger locations, so the maps show where EVs are registered. They do not measure where charging capacity is missing, and that would need charging station data.

## Limitations

- Rows with a range of 0 were removed. The dataset's eligibility field includes the label "Eligibility unknown as battery range has not been determined", and no unknown-eligibility rows remain after filtering, so vehicles without a recorded range are not represented.
- The data is primarily Washington State registrations and may not generalize elsewhere.
- Models use only two features each.

## Run it yourself

The notebook was last run on Python 3.10.

```bash
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn statsmodels scipy plotly geopandas shapely folium jupyter
```

Download the dataset from Kaggle, then update the two hard-coded `pd.read_csv` paths in the notebook: one under "Importing Libraries and Datasets" for the raw CSV, and one under "Exploratory Data Analysis" for the generated `cleaned.csv`.

```bash
jupyter notebook Tutorial.ipynb
```
