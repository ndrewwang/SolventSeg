# Code repository for 'Current-driven solvent segregation in lithium-ion electrolytes'

This repository contains code for the workflow described in the accompanying manuscript. The executable code is in the form of jupyter notebooks and raw experimental data in the form of CSV. A summary of the contents follows:


1. **/trainingset/Ternary_Physicochemical_Training.csv**. This CSV file contains the experimental training dataset measured to link electrolyte (LiPF6:EC:EMC) mass fractions to physicochemical properties across the temperature range. The columns 'ec' represents the approximate solvent ratio of the formulation, 'Temp' gives the temperature that the property was measured at in degrees celsius, 'xLiPF6' is the mass fraction of salt, 'xEC' the mass fraction of EC and 'xEMC' the mass fraction of EMC. The 'd', 'v', and 'k' columns are the properties density in g/cm3, viscosity in cP, and ionic conductivity in mS/cm.

2. **/data/**. This folder contains the experimental raw Hittorf cell electrolyte measurements in CSV file format. For each file name, the first two numbers represent the approximate initial neat EC:EMC solvent mass ratio, and the following three the molarity. For example, 55100 is an initial 5:5 EC:EMC solvent mass ratio electrolyte with approximate 1.00 M LiPF6 molarity. The final number after the underscore is the experiment number. Each data CSV has four columns, 'T', 'd', 'v', 'k' for the temperature in degrees celsius, density in g/cm3, viscosity in cP, and ionic conductivity in mS/cm. There are ten data rows, the top five are the properties of the electrolyte extracted from the anodic Hittorf chamber, while the bottom five are that for the cathodic Hittorf chamber.

3. **ColsolventGPR_CrossValidation.ipynb**. This workbook performs leave-one-out cross validation to evaulate the goodness-of-fit for the Gaussian processes regression model trained to predict ternary compositions from measured electriolyte physicochemical properties.

4. **CosolventGPR_HittorfProcessing.ipynb**. This workbook uses the trained Gaussian processes regression model to predict ternary compositions, given the sets of measured electriolyte physicochemical properties from Hittorf polarization experiments, as summarised in the *data* folder of this repository. Results are also exported to a CSV format in the *results* folder. 

4. **/results/**.  This folder contains the results summary as exported by the above workbook. The CSV for each initial composition and individual Hittorf experiment will give the resulting ternary mass fractions 'xLi', 'xEC', and 'xEMC' from the anodic and cathodic chambers along with the initial composition. The GPR model standard deviation is also provided, along with the cation transference numbers as calculated based on density alone, and one that uses the fraction of Li+ moved given by the GPR model. The results folder also contains the csv table 'LOOCV_DF.csv' which contains the saved outputs from the GPR cross validation test.

5. **Results_Exp_and_GPR_Uncertainties.ipynb** This workbook propagates the uncertainties from experimental repeats and GPR model variance into the final ternary compositions.

6. **Visualising_GPR.ipynb** This workbook visualises the uncertainty between inputs and outputs in the GPR model for composition slices across the training mass fraction range.