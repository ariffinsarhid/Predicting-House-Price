# Project 2 - Ames Housing Data

---
## Content
 * [Problem Statement](##Problem-Statement)
 * [Executive Summary](##Executive-Summary)
 * [Data Dictionary](##Data-Dictionary)
 * [First Modeling Score](##First-Modeling-Score)
 * [Second Modeling Score on Best 10 Feature](##Second-Modeling-Score-on-Best-10-Feature)
 * [Conclusion](##Conclusion)
 * [Opportunity for Further Study](##Opportunity-For-Further-Study)

## Problem Statement
Star Property Max is a housing agent consultant based in Ames, Iowa to help its customers to buy or sell their property. In recent years, the consultant agency has faced difficulties in helping their client in choosing their dream house as it takes a long time to close a deal. The average time taken to choose a home is 50 days according to [Housing Logic](https://www.houselogic.com/buy/first-time-home-buyer/how-long-does-it-take-buy-house/). There are several factors that determines the price of the house such as Neighborhood, Size, Age and Condition as stated by [OpenDoor](https://www.opendoor.com/w/blog/factors-that-influence-home-value)

This project aims to reduce the time taken for their client to find the right home that is within their budget by considering the factors mentioned by OpenDoor. The project will try to determine if these factors have strong effect on the saleprice of the house, so that the client can focus on these factors when doing house visit thus reducing time. 

## Executive Summary
In order to achieve this, Star Property Max will start by using data which has 2051 records and 81 feature columns. The complete data dictionary can be found [here](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt). The data is will then be cleaned and null values will be imputed by combination of SimpleImputer and by looking at the mean. The 81 feature columns are explored and scrunitize at the first feature selection. This is done by identifying if the feature is related to Neighborhood, Size, Age, or Condition as stated above. In total, 47 features were selected. By doing this, we are able to focus on the features that are more relevant and important to answer the problem statment. The second round of feature selection is done by idenityfing the best coefficient from Linear Regression, Ridge RegressionCV and Lasso Regression CV. 


## Data Dictionary
|Feature Name|Coefficient|Grouping|Variable Type|
|----|----|----|----|
|overall_qual|11010.8208|Condition |Ordinal |
|neighborhood|9535.0051|Neighborhood |Ordinal |
|gr_liv_area|9334.0931|Size |Discrete |
|1st_flr_sf|7426.5488|Size |Continuous |
|kitchen_qual|7075.4782|Condition|Binned, Ordinal|
|exter_qual|5989.0970|Condition |Binned, Ordinal |
|fireplace_qu|5303.8825|Condition|Binned, Ordinal|
|garage_cars|5038.5774 |Size |Discrete|
|garage_area|4893.5038 |Size |Continuous|
|bsmt_exposure|4748.9522| Condition |Binned, Ordinal|
|mas_vnr_area|3708.1953 |Size |Continuous|
|full_bath|3685.7758|Condition |Discrete|
|bsmt_full_bath|3535.7757|Size |Discrete|
|2nd_flr_sf|3413.9419 |Size |Continuous|
|overall_cond|3296.2621 |Condition |Ordinal|
|totrms_abvgrd|2727.9771|Size | Discrete|
|exterior_3rd|2534.5609|Condition |Binned, Ordinal|
|functional|2504.9971|Condition |Binned, Ordinal|
|bsmtfin_sf_merged|2014.8090|Size |Merged, Binned, Ordinal|
|bsmtfin_type_merged|1997.4786|Size |Merged, Binned, Ordinal|
|lot_area|1926.7911|Size |Continuous |
|fireplaces|1907.6319|Size|Discrete |
|bsmt_qual_cond_merged|1899.8693|Size |Binned, Ordinal |
|half_bath|1775.1445|Condition |Discrete |
|year_remod/add|1470.1160|Age |Discrete |
|heating_qc|1296.7204|Condition |Binned, Ordinal|
|utilities|1102.1668 |Condition |Binned, Ordinal |
|bldg_type_2fmCon|905.1757|Condition |Dummify |
|total_bsmt_sf|741.9685|Size |Continuous |
|bldg_type_1Fam|605.2343|Condition |Dummify|
|exter_cond|515.0642|Condition |Binned, Ordinal |
|condition_3|147.4282	|Condition |Condition 1 & Condition 2 merged and binned |
|bldg_type_TwnhsE|13.9126 |Condition |Dummify |
|lot_shape|4.8600 |Size |Binned, Ordinal |
|lot_frontage|-572.9146 |Size |Continuous |
|bedroom_abvgr|-760.2371|Size |Dummify |
|bldg_type_Duplex|-794.5138|Condition |Dummify |
|bsmt_half_bath|-840.9478|Size |Discrete |
|pool_area|-852.7522 |Size |Continuous |
|bldg_type_Twnhs|-1138.3456|Condition |Dummify |
|yr_sold|-1176.8976|Age |Discrete |
|electrical|-1348.1644|Condition |Binned, Ordinal|
|kitchen_abvgr|-1381.5204|Condition |Dummify |
|pool_qc|-1538.6284 |Condition |Binned, Ordinal |
|garage_qual_cond_merged|-1799.6820	|Condition |Merged, Binned, Ordinal |


## First Modeling Score
|Model Used|Train Score|Test Score|RMSE on Test|ALPHA|
|----|----|----|----|----|
|Linear Regression|0.8525513217551397|0.8788893698584481|0.8788893698584481|-|
|Ridge RegressionCV|0.8461943895018165|0.8802359848712134|26472.651337511605|265.6087782946687|
|Lasso RegressionCV|0.8144203639753176|0.9052659439599033|23544.38398369649|335.1602650938841|

From the model score itself, we can see that the Ridge RegressionCV has a better score difference between the train and test score. Therefore, I chose the best 10 features from  RidgeCV to be used for the second modeling run. Based on the coefficient of RidgeCV, the best 10 features are 

|Features|Coefficient|
|---|---|
|overall_qual|11010.8208|
|neighborhood|9535.0051|
|gr_liv_area|9334.0931|
|1st_flr_sf|7426.5488|
|kitchen_qual|7075.4782|
|exter_qual|5989.0970|
|fireplace_qu|5303.8825|
|garage_cars|5038.5774|
|garage_area|4893.5038|
|bsmt_exposure|4748.9522|

## Second Modeling Score on Best 10 Feature
|Model Used|Train Score|Test Score|RMSE on Test|ALPHA|
|----|----|----|----|----|
|Linear Regression|0.8288438307427699|0.8684021198890712|27749.726857600883|-|
|Ridge RegressionCV|0.8278826688469308|0.8659976432107849|28002.092400471854|148.4968262254465|
|Lasso RegressionCV|0.8182223293214362|0.8772051695897305|26805.524402054336|335.1602650938841|

From the model score here, we can tell that RidgeCV has the best score on train and test set. It has the smallest difference of 0.0381149743638541 between the train and test score as compared to the other 2 models. Hence, the feature selection will be from RidgeCV model.

## Conclusion
In conclusion, Star Property Max can use these features of overall_qual, neighborhood, gr_liv_area, 1st_flr_sf, kitchen_qual, exter_qual, fireplace_qu, garage_cars, garage_area, and bsmt_exposure as an identifier in determining the sale price of the house. This can eventually help its customer to reduce their time in selecting their dream home. 

## Opportunity For Further Study
This study does not end here. There are several opportunities for further study which we can look into such as:
* Using other models such as K best neighbour to identify the best features.
* Run the model with all the dataset in place without dropping any features. As this project was to only look at factors of Neighborhood, Size, Age and Condition which can predict the sale price, running the model with all the features in place might give slightly different result. 
* Star Property Max may collect the average time of its customer looking for the house and add it as a feature.
# Project-2-Ames-Data
