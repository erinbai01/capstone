## FAVORITA STORE SALES PREDICTION


### Executive Summary

- Favorita is one of the largest supermarket chains in Ecuador, known for its extensive selection of groceries, household items, and other goods. 
- Given past sales data of different categories and stores, predict future daily sales of each category in different stores.
- The project aims to help improve customer experience and control business cost.
- This project focused on fine tuning linear regression. The model is robust but linear regression assumptions are not met so later more advanced models will be used. A simple try on other models showed that Random Forest and Neural Network have the highest R squared scores.


### Demo

#### EDA and Preprocessing:

Define analysis scope

![image](./figures/sprint2/SalesUnitByFamily.png)
![image](./figures/sprint2/SalesUnitByStore.png)
![image](./figures/sprint2/NullValues.png)

Reduce collinearity

![image](./figures/sprint2/XsCollinearity.png)

#### Model Evaluation:


Residual distribution

![image](./figures/sprint2/QQplot.png)

Homoscedasticity 

![image](./figures/sprint2/Homoscedasticity.png)


### Methodology

- Single Table EDA and Cleaning
    - Preliminary data cleaning and EDA to understand the dataset to join the five tables together.
    - In-depth EDA and data cleaning to understand Xs' relationship with y.
- Joint Table EDA and Feature Engineering:
  - Full table EDA and preprocessing for data modeling (after joining the tables together, more null values were created and imputation has to be done).
  - Time series column feature engineering to create features.
- Baseline Modeling (Linear Regression)
- PCA and Grid-search Model Fine Tuning
- Stepwise Model Fine Tuning
- Model Evaluation
- Preliminary Modeling of Advanced Models



### Data Dictionary

#### 1. sales.csv

**store_nbr**: the store at which the products are sold.
**family**: the type of product sold.
**sales**: the total sales for a product family at a particular store on a given date. Fractional values are possible since products can be sold in fractional units (e.g., 1.5 kg of cheese, as opposed to 1 bag of chips).
**onpromotion**: the total number of items in a product family that were being promoted at a store on a given date.

#### 2. stores.csv
Store metadata, including **city, state, type, and cluster**.
cluster is a grouping of similar stores.

#### 3. oil.csv
**Daily oil price**. (Ecuador is an oil-dependent country and it's economical health is highly vulnerable to shocks in oil prices.)

#### 4. holidays_events.csv
Holidays and Events, with metadata
NOTE: Pay special attention to the **transferred** column. A holiday that is transferred officially falls on that calendar day, but was moved to
another date by the government. A transferred day is more like a normal day than a holiday. To find the day that it was actually celebrated, look for the corresponding row where type is Transfer. For example, the holiday Independencia de Guayaquil was transferred from 2012-10-09 to 2012-10-12, which means it was celebrated on 2012-10-12. 

Days that are type **Bridge** are extra days that are added to a holiday (e.g., to extend the break across a long weekend). These are frequently made up by the type **Work Day** which is a day not normally scheduled for work (e.g., Saturday) that is meant to payback the Bridge.

**Additional** holidays are days added a regular calendar holiday, for example, as typically happens around Christmas (making Christmas Eve a holiday).

#### 5. transactions.csv
**transactions**: daily store transactions

#### 6. Additional Notes

Wages in the public sector are paid every two weeks on the 15th and on the last day of the month. Supermarket sales could be affected by this.
A magnitude 7.8 earthquake struck Ecuador on April 16, 2016. People rallied in relief efforts donating water and other first need products which 
greatly affected supermarket sales for several weeks after the earthquake



### Dataset

- https://drive.google.com/drive/folders/1iz1sbEKrBc2eLgTmHnHQM-gkGfXIuOB8?usp=sharing


### Credits & References

- https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html
- https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.probplot.html