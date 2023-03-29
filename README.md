# Census Income Analysis

Source: [UCI](https://archive.ics.uci.edu/ml/datasets/adult)

`NULL` are values are ? sign in this dataset.

## Insights (From EDA):

*   In `workclass`, "self-empl-inc" and "Private" are groups that concentrates a lot og high-income data points.
*   *Exec-managerial* and *Prof-specialty* are the `occupation`s gather a great % of people who get > 50k annually.
*   *Husbands* group a huge % of people who earn more than 50k.
*   In `gender`, male people gather a lot of samples of people who make more than 50k.
*   It is find that people with bachelor degrees or higher level education degrees then to more than 50k.
*   The group of **people that were born in US** get a higher % of people who has income above 50k.
*   *White people* has a higher % of people who make more than 50k vs. *minority group of people*.
*   *Married people* get together a huge % of people who earn more than 50k.
*   `Age` distribution are right-skewed. People who make more than 50k has a higher median vs low-income group.
*   There is a gap between low-level income group and high-income group in terms of `capital-gain`.

## Features

*   `age`, discrete numerical.
*   `fnlwgt`, continuous numerical.
*   `ocupation`, categorical. One hot encoding used, dropping first column.
*   `sex`, categorical. One hot encoding used, dropping first column.
*   `workclass`, categorical. One hot encoding used, dropping first column.
*   `education`, ordinal. 'Preschool' <'1st-4th' < '5th-6th' < '7th-8th' < '9th' < '10th' < '11th' < '12th' < 'HS-grad' < 'Prof-school'< 'Assoc-acdm' < 'Assoc-voc' < 'Some-college' < 'Bachelors' < 'Masters' < 'Doctorate'.
*   `education-num`, discrete numerical.
*   `capital-gain`, continuous numerical.
*   `capital-loss`, continuous numerical.
*   `hours-per-week`, discrete numerical.
*   `married`, boolean. If the person is married then 1 else 0.
*   `race_groups`, categorical. Groups white and minority (Black, Asian-Pac-Islander, Amer-Indian-Eskimo, Other). One hot encoding used, dropping first column.
*   `us_native_country`, boolean. If the person was born in US then 1 else 0.

## Target
*   `more_than_50k`, boolean. If the person earns more than 50k then 1 else 0.

## Chosen Model: `RandomForestClassifier`

### Hyperparameters
```{'class_weight': 'balanced', 'criterion': 'gini', 'max_depth': 14, 'min_samples_leaf': 4, 'min_samples_split': 13, 'n_estimators': 360, 'random_state': 42}```

Set parameter `'class_weight'` with value `'balanced'` because is a imbalanced dataset. Another way would be use `imbalanced-learn` to create synthetic samples of the oversampled target label and check classification metrics. This generates better recall metric at the cost of a worse precision metrics for the target label with less appearances in the dataset.

![Confunsion matrix](https://user-images.githubusercontent.com/70084552/228394955-44d37db3-13cb-46ab-bf16-5638c910ca62.png)

### Classification report
|  | precision | recall | f1-score  | support |
|-----------------|-----------------|-----------------|-----------------|-----------------|
|0|0.94|0.81|0.87|5772|
|1|0.59|0.84|0.69|1908|
||||||
|accuracy|||0.82|7680|
|macro avg|0.76|0.82|0.78|7680|
|weighted avg|0.85|0.82|0.82|7680|

### Feature importance score
![image](https://user-images.githubusercontent.com/70084552/228400518-f6c766ce-2986-44ab-b987-0c64b7d10f49.png)
