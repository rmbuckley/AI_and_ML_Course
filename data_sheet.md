## Motivation

- The dataset was exported from Vital Eneri’s VitalView Building control analytics system for the purpose of trailing a machine learning solution to automatically assign datapoint category based on datapoint name. 
- This was created by the VitalView development team at Vital Energi.
 
## Composition

- The dataset is comprised of documents relating to BMS datapoints currently integrated and running within Vital Energi’s VitalView system, this includes contract name, building name, datapoint name, system type, and datapoint category.
- There are 72 datapoint categories with a total of 4,130 records.  There is a large imbalance between the number of samples in each category.  The majority category has 1,280 samples and minority category has 3 samples.
- There is no confidential data included as the dataset has already been anonymised and missing data removed. 

## Collection process

- The data was manually exported from Vital Energi’s VitalView BMS analytics system. 
- This is a sample of a larger working dataset.  Specific projects have been selected from which all datapoints have been exported to try to ensure a good range of common datapoint types are present.
- The projects from which this data has been exported range from 2019 to 2022.

## Preprocessing/cleaning/labelling

- The data has been anonymised and cleaned.  This have involved removing all customer and contract specific names, replacing them with general contract numbers, and removing and NaN values.
- All generic sensor types have also been removed as the goal is to predict actual sensor types not those given generic analogue or digital naming as the data type is not known.
- The raw data contains confidential information so has not been provided with this code. 
 
## Uses

- This particular dataset is specific to the VitalView system and similar BMS analytics systems.  However, the processes used to create a custom dictionary and binary vector tokenizer could be re-purposed for any text classification problem where the predictors are not normal words, i.e. shorthand, acronyms, symbols etc.  
- The dataset has a large imbalance in sample numbers between categories. Several approaches can be used to account for this such as used in the attached code, however it is recommended that further samples for the minority categories be exported from VitalView prior to further modelling.

## Distribution

- This dataset has not been distributed to any further parties and there is no plan to do so 
- This dataset is anonymised and not subject to any copyright  or intellectual property etc.

## Maintenance

- This dataset is not maintained

