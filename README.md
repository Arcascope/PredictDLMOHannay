# Predict DLMO

The website [predict DLMO](http://www.predictdlmo.com/) was created by Olivia Walch and Philip Cheng to help circadian reseachers convert
their CSV files measuring subjects activity (called actigraphy) into predictions about their circadian state [code available here](https://github.com/ojwalch/predicting_dlmo). The current gold standard for determining circadian phase is to measure the timing of melatonin increase in dim light (Dim light Melatonin Onset). 

This repo will take the house the code for a clone of predict DLMO with either a drop down menu to choose the model used or just use the Hannay Circadian model. The original predict DLMO uses an older mathematical model (St.Hilaire model) to predict the DLMO timing. 

Python code for the Hannay (Single Population Model) can be found in the repo [HCRSimPY](https://github.com/Arcascope/HCRSimPY) specifically the model can be found [here](https://github.com/Arcascope/HCRSimPY/blob/master/HCRSimPY/models/singlepop_model.py). Both of these models are differential equation models meaning that they define how the quantity of interest changes. The Hannay model has two variables

R: The amplitude 
Psi: The phase (an angle in radians [0, 2\pi])

Within the model the DLMO is defined by be when the phase crosses [5\pi/12 or 1.3]. 

## Starting points

* The predict DLMO website uses a technique called RK4 (Fourth order Runge-Kutta) to solve the differential equation. You should use the same technique for the Hannay model.

In the models.js file you can see two differential equation models are defined:

```{javascript}
function clockModel_ForgerSimpler(t, y) 
function clockModel_HilaireNonPhotic(t, y)
```

You will need to make a function of the same form....

```{javascript}
function clockModel_Hannay(t,y)
```

which implemements the equations and parameters as shown the in HCRSimPy 


## Bonus
* Make a dropdown to switch between the models (St.Hilaire / Hannay) so the user can choose which model they want to run
* Once the model runs make a histogram of the DLMO values (where the values are the fractional hours [8:30PM = 20:30 = 20.50 hrs])







