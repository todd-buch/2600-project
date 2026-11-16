## Purpose
As a group we decided to make models that would analyze and predict if someone would default on their home loan given past credit history. The dataset we found is from 2018 and shows credit default risk. It has data on applications, the loan amount, gender, age, family status, income, occupation, and more. It does not give us the interest rate, personally identifiable information, or attributes on the home. It also shows us loans that were approved or not approved, as well as the loan amount asked for versus what was actually granted. The two techniques we are going to compare are gradient boosting and logistic regression.

### Dataset: `https://www.kaggle.com/c/home-credit-default-risk`

## Features to be used

- `AMT_INCOME_TOTAL`
  - Income the client has to make the payments.
- `AMT_CREDIT`
  - Size of this loan.
- `AMT_ANNUITY`
  - Scheduled payment, so we can see the burden against income.
- `NAME_CONTRACT_TYPE`
  - Cash loans and revolving loans are paid back on different terms.
- `DAYS_BIRTH`
  - Age at application. Stored as days before the application, so we flip the sign.
- `CODE_GENDER`
  - Recorded on every application, and default rates differ by it.
- `NAME_FAMILY_STATUS`
  - Married, single, and the other statuses split the household differently.
- `CNT_CHILDREN`
  - Dependents already claim part of the income.
- `NAME_INCOME_TYPE`
  - Working, pension, and the rarer types are not the same kind of income.
- `OCCUPATION_TYPE`
  - Job category. 31% missing, which we keep as its own level.
- `DAYS_EMPLOYED`
  - Time in the current job. A sentinel value (365243) marks people who are not employed, mostly pensioners.
- `NAME_EDUCATION_TYPE`
  - Highest schooling, filled in for every application.
- `FLAG_OWN_CAR`
  - Owns a car, which is an asset rather than a description of a home.
- `FLAG_OWN_REALTY`
  - Owns a house or flat. This is only the yes/no flag, not building attributes.
- `EXT_SOURCE_2` and `EXT_SOURCE_3`
  - Outside risk scores. `EXT_SOURCE_2` is nearly complete and `EXT_SOURCE_3` is missing on about 20% of rows. We leave out `EXT_SOURCE_1` because it is missing on more than half of applications.
- Bureau `CREDIT_ACTIVE`, `CREDIT_DAY_OVERDUE`, and `AMT_CREDIT_SUM_OVERDUE`
  - Past-due and still-open credit bureau loans are direct payment trouble.
- Bureau `AMT_CREDIT_SUM` and `AMT_CREDIT_SUM_DEBT`
  - How much outside credit and debt the client already has. Debt is missing on 15% of bureau rows.
- Previous `NAME_CONTRACT_STATUS`
  - How many earlier Home Credit applications were approved, refused, canceled, or left as an unused offer.
- Previous `AMT_APPLICATION` and `AMT_CREDIT`
  - What the client asked for on earlier loans versus what was actually granted.

## Run instructions