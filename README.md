# Antenna S11 Parameter Estimation Using Machine Learning

## About this project
This project tries to predict the S11 parameter (in dB) of a microstrip patch antenna. The prediction is based on some geometric parameters of the antenna and the operating frequency.

## Dataset
The dataset is from Kaggle. It was originally generated using Ansys HFSS simulations of 8 different patch antenna designs, with different slot geometry between them. The frequency sweep goes from 1.0 GHz to 3.5 GHz, so the main working frequency (2.4 GHz) is in this range. This frequency is common for Bluetooth and WLAN devices.

The dataset has 1266 rows and these columns:

* **freq_ghz**: operating frequency (GHz)
* **patch_length_mm**: length of the patch (mm)
* **patch_width_mm**: width of the patch (mm)
* **slot_length_mm**: length of the slot (mm)
* **slot_width_mm**: width of the slot (mm)
* **s11_db**: the S11 value (dB), this is the target we want to predict

## What I did
* Loaded the dataset and checked the basic information (shape, columns, statistics).
* Made a plot of S11 vs frequency for each of the 8 designs, to see the antenna response.
* Split the data into training and test sets (80% / 20%).
* Trained 3 models to predict S11:
  * Linear Regression
  * Random Forest
  * XGBoost
* For every model, I checked MSE, R2 score, and did a 5-fold cross validation.
* For Random Forest and XGBoost, I also checked which features are more important.
* At the end, compared the 3 models together.

## Results
* Linear Regression: Test R2 = 0.36, CV Mean R2 = 0.23
* Random Forest: Test R2 = 0.975, CV Mean R2 = 0.923
* XGBoost: Test R2 = 0.94, CV Mean R2 = 0.885

## Conclusion
Linear Regression does not work well here, because the relation between the antenna parameters and S11 is not linear, it is more complex. Random Forest and XGBoost are much better because they can learn non-linear patterns
