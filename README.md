## Purpose
As a group we decided to make models that would analyze and predict if someone would default on their home loan given past credit history. The dataset we found is from 2018 and shows credit default risk. It has data on applications, the loan amount, gender, age, family status, income, occupation, and more. It does not give us the interest rate, personally identifiable information, or attributes on the home. It also shows us loans that were approved or not approved, as well as the loan amount asked for versus what was actually granted. The two techniques we are going to compare are gradient boosting and logistic regression.

### Dataset: `https://www.kaggle.com/c/home-credit-default-risk`

## Features to be used
- `AMT_INCOME_TOTAL`
  - Income the client has to make the payments.
- `AMT_CREDIT`
  - Size of this loan.
- `ANNUITY_TO_INCOME`
  - Annuity divided by income. The raw annuity moved almost in lockstep with the loan size.
- `NAME_CONTRACT_TYPE`
  - Cash loans and revolving loans are paid back on different terms.
- `DAYS_BIRTH`
  - Age at application. Stored as days before the application, so we flip the sign.
- `CODE_GENDER`
  - Recorded on every application, and default rates differ by it. The 4 rows coded `XNA` are dropped.
- `NAME_FAMILY_STATUS`
  - Married, single, and the other statuses split the household differently. The 2 rows coded `Unknown` are dropped.
- `CNT_CHILDREN`
  - Dependents already claim part of the income.
- `NAME_INCOME_TYPE`
  - Working, pension, commercial associate, and state servant. Unemployed, student, businessman, and maternity leave are folded into `Other`.
- `DAYS_EMPLOYED`
  - Time in the current job, with the sign flipped so it counts days employed.
- `NOT_EMPLOYED`
  - The value 365243 in `DAYS_EMPLOYED` marks people who are not employed, mostly pensioners. Those rows get a 1 here and a 0 in `DAYS_EMPLOYED`.
- `NAME_EDUCATION_TYPE`
  - Highest schooling, filled in for every application.
- `FLAG_OWN_CAR`
  - Owns a car, which is an asset rather than a description of a home.
- `FLAG_OWN_REALTY`
  - Owns a house or flat. This is only the yes/no flag, not building attributes.
- `EXT_SOURCE_2` and `EXT_SOURCE_3`
  - Outside risk scores. `EXT_SOURCE_2` is nearly complete and `EXT_SOURCE_3` is missing on about 20% of rows. We leave out `EXT_SOURCE_1` because it is missing on more than half of applications.
- `BUREAU_N_ACTIVE`
  - How many credit-bureau loans are still open.
- `BUREAU_DAYS_OVERDUE`
  - Longest current bureau delinquency, in days.
- `BUREAU_AMT_OVERDUE`
  - Total amount currently overdue at the credit bureau.
- `BUREAU_AMT_DEBT`
  - Total bureau debt. We skip the bureau credit sum because it tracks this debt.
- `PREV_N_REFUSED`
  - How many earlier Home Credit applications were refused.
- `PREV_AMT_GAP`
  - On earlier loans, the amount asked minus the amount granted. The two raw sums were almost the same number.

## Run instructions