# Model Card

## Model Description

**Input:** BMS datapoint name

**Output:** BMS datapoint type class (i.e. room temperature sensors, system running status, ambient humidity sensor etc.)

**Model Architecture:** Support Vector Machine that uses a custom tokenizer that converts the BMS datapoint name input into binary vectors based on a custom dictionary

## Performance

Evaluated for specific datapoint classes predicted by the model (e.g. room temperature sensor, system enable status, ambient humidity sensor etc.)
Three performance metrics report are:
•	Average accuracy: 87.8%

## Limitations

Performance evaluated on a single dataset exported from Vital Energi’s VitalView system.
•	Dataset contains 4,130 samples with 72 datapoint categories
•	This is an unbalanced dataset with majority class having 1,280 samples and minority class having 3 samples

## Trade-offs

Due to the unbalanced dataset the model tends to overfit classes that have less than 20 samples.

