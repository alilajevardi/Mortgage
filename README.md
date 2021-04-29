# Mortgage
The report here presents exploratory data analysis of the HMDA mortgage application dataset along with the machine learning predicting model for loan approval. The dataset can be downloaded from CFPB website at: https://www.consumerfinance.gov/data-research/hmda/historic-data/

After doing basic exploratory analysis, visualization and data cleaning and processing, the most essential features of the dataset are identified that provide information two label classes (mortgage accepted/rejected).

Those features were subsequentely used for the creation of a binary classifier capable of predicting whether an application will be accepted or not, with an accuracy of 73%. The most important features of the dataset are the following, however the description of all label can be found at: https://files.consumerfinance.gov/hmda-historic-data-dictionaries/lar_record_codes.pdf

- loan_amount - Size of the requested loan in thousands of dollars
- msamd - A categorical with no ordering indicating Metropolitan Statistical Area/Metropolitan Division
- state_code - A categorical with no ordering indicating the U.S. state
- country_code - Three-digit FIPS county identifier
- applicant_income - In thousands of dollars
- number_of_owner-occupied_units - Number of dwellings, including individual condominiums, that are lived in by the owner
- minority_population - Number of people that belong in a minority group, a new feature that was created for the purposes of this analysis
- tract_family_income - The tract median family income in dollars, another feature that was created for the purposes of this analysis

After initial EDA, it found out that some columns need to be removed due to lack of data and correlation with other columns. Furthermore, we can read on the dataset description that some categorical features include categories that correspond to missing values, e.g. the -1 category of 'msamd' column indicates a missing value. It is important to remove some categories from categorical features to have a consistant datatset.
Regarding the labels that is 'Action_taken' column we have different classes as:

 (1) Loan originated.
 (2) Application approved but not accepted.
 (3) Application denied by financial institution
 (4) Application withdrawn by applicant
 (5) File closed for incompleteness
 (6) Loan purchased by the institution
 (7) Preapproval request denied by financial institution
 (8) Preapproval request approved but not accepted (optional reporting)

with the distribution of

![Pie_chart_1](https://github.com/alilajevardi/Mortgage/blob/main/artifacts/Pie_01.png)



We need to have first three numbers for prediction model and drop other numbers. Then reducing to two lables as 0 (rejected) and 1 (approved) by combining 1 and 2 values in 1 and changing 3 to 0.

![Pie_chart_2](https://github.com/alilajevardi/Mortgage/blob/main/artifacts/Pie_02.png)

With applying above-mentioned changes in features and NaN cleaning, we get:

```text
agency_code                       6944633
loan_type                         6944633
property_type                     6944633
owner_occupancy                   6944633
loan_amount_000s                  6944633
action_taken                      6944633
msamd                             6944633
state_code                        6944633
county_code                       6944633
census_tract_number               6944633
applicant_ethnicity               6944633
applicant_race_1                  6944633
applicant_sex                     6944633
applicant_income_000s             6944633
lien_status                       6944633
population                        6944633
minority_population               6944633
hud_median_family_income          6944633
tract_to_msamd_income             6944633
number_of_owner_occupied_units    6944633
number_of_1_to_4_family_units     6944633

```


As one can see the above pie chart, dataset is not balanced. As below graph shows the nombuer of approved cases are much higher than rejected ones.

![Bar_chart_1](https://github.com/alilajevardi/Mortgage/blob/main/artifacts/Barchart_labels.png)


```text
1.0    0.815335
0.0    0.184665
Name: action_taken, dtype: float64
```

The approval class consists of 81.5% where rejection data filles 18.5% of dataset.

The below histograms of the numerical features demonstrate the distribution of data in diffrent columns.

![Histogram](https://github.com/alilajevardi/Mortgage/blob/main/artifacts/Histogram.png)
