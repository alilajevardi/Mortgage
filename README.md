# Mortgage
The report here presents exploratory data analysis of the HMDA mortgage application dataset along with the machine learning predicting model for loan approval. The dataset can be downloaded from CFPB website at: https://www.consumerfinance.gov/data-research/hmda/historic-data/

After doing basic exploratory analysis, visualization and data cleaning and processing, the most essential features of the dataset are identified that provide information two label classes (mortgage accepted/rejected).

Those features were subsequentely used for the creation of a binary classifier capable of predicting whether an application will be accepted or not, with an accuracy of 73%. The most important features of the dataset are the following, however the description of all label can be found at: https://files.consumerfinance.gov/hmda-historic-data-dictionaries/lar_record_codes.pdf

    loan_amount - Size of the requested loan in thousands of dollars
    msamd - A categorical with no ordering indicating Metropolitan Statistical Area/Metropolitan Division
    state_code - A categorical with no ordering indicating the U.S. state
    country_code - Three-digit FIPS county identifier
    applicant_income - In thousands of dollars
    number_of_owner-occupied_units - Number of dwellings, including individual condominiums, that are lived in by the owner
    minority_population - Number of people that belong in a minority group, a new feature that was created for the purposes of this analysis
    tract_family_income - The tract median family income in dollars, another feature that was created for the purposes of this analysis
