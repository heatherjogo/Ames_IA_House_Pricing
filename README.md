# Project 2: Ames Housing Data for Predicting Home Value
---

### Contents:

- [Problem Statement](#Problem-Statement)
- [Executive Summary](#Executive-Summary)
- [Data Sources](#Data-Sources)
- [Modeling Data Files](#Modeling-Data-Files)
- [Data Dictionary](#Data-Dictionary)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)

---

### Problem Statement:

As a Realtor in Ames, Iowa, your goal is to help clients sell their homes at a highest price, sell it quickly, and with the least hassle for the homeowner. However, even if a homeowner is ready to sell, sometimes the house itself isn’t. How can data science help listing agents direct their clients toward areas of improvement that will maximize their investment in terms of increased house value?



### Executive Summary

For this analysis, I leveraged the Ames Housing Datasets which were created by the Ames Assessors Office. The data include statistics about roughly 3000 homes which were sold in Ames, Iowa between 2006 and 2010. The datasets, which are split in to training and testing files, contain over 80 features about the houses and properties sold in Ames during this time. Through data cleansing, exploration and analysis, followed by linear regression modeling, I have developed a model that identifies the key drivers of sale price with an eye toward features which the homeown can improve prior to listing their house, in order to increase their selling price. 

A secondary goal of this project was to develop a model to compete in a Kaggle Challenge. To this end, I also created a model that focused on maximizing R2 scores. This model was different from the one developed to identify areas for home and property improvement, so I will detail the differences in the Data Dictionary below. 

### Data Sources
* [`train.csv`](./datasets/train.csv): Ames Housing Data Training Dataset | [data dictionary](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt))
* [`test.csv`](./datasets/test.csv): Ames Housing Data Training Dataset 

### Modeling Data Files
* [`ames_train_transform.csv`](./datasets/ames_train_transform.csv): Ames Housing Data Training Dataset with Transformed fields and new features (see Data Dictionary below)
* [`ames_test_transform.csv`](./datasets/ames_test_transform.csv): Ames Housing Data Testing Dataset with Transformed fields and new features
* submission_#.csv: Kaggle submission files containing Id and Saleprice fields. All files were uploaded to Kaggle for scoring.

### Data Dictionary

|Feature|Type|Model(s) Used In|Description|
|---|---|---|---|
|lot_area|int|Home Value & Kaggle|Lot size in square feet
|lot_frontage|float|Home Value & Kaggle|Linear feet of street connected to property. Assumed to be zero if null.
|overall_qual|int|Home Value & Kaggle|10 point ranking of the overall material and finish of the house. Converted from ordinal to numeric
|overall_cond|int|Home Value & Kaggle|10 point ranking of the overall condition of the house. Converted from ordinal to numeric
|exter_qual2|int|Home Value & Kaggle|5 point ranking of the quality of the material on the exterior. Converted from ordinal to numeric
|exter_cond2|int|Home Value & Kaggle|5 point ranking of the present condition of the material on the exterior. Converted from ordinal to numeric| 
|year_built|int|Home Value & Kaggle|Original construction date
|year_remod/add|int|Home Value & Kaggle|Remodel date (same as construction date if no remodeling or additions)
|home_age|int|Kaggle|Age of house in years, as of 2010
|total_house_sf|float|Home Value & Kaggle|Total square footage of both above ground home and basement
|porch_sf|int|Home Value & Kaggle|Total square footage of any porch or deck feature on the house
|gr_liv_area|int|Home Value & Kaggle|Above ground living area in square feet
|bsmt_sf|float|Home Value & Kaggle|Total basement square footage
|totrms_abvgrd|int|Home Value & Kaggle|Number of rooms excluding bathrooms above ground
|bedroom_abvgrd|int|Home Value & Kaggle|Bedrooms above ground (does not include basement)
|baths|float|Home Value & Kaggle|Total number of baths, in .5 increments, both above ground and in basement
|date_blt_1945-1979|uint|Kaggle|Indicates whether a home was built between the years of 1945 and 1979, inclusive
|date_blt_1980-2010|uint|Kaggle|Indicates whether a home was built between the years of 1980 and 2010, inclusive
|lot_config_Corner|uint|Home Value & Kaggle|Indicates whether a property is on a corner lot
|lot_config_CulDSac|uint|Home Value & Kaggle|Indicates whether a property is in a cul-de-sac
|lot_config_Inside|uint|Home Value & Kaggle|Indicates whether a property is on an inside lot
|lotshape_reg_yn|bool|Kaggle|True if lot shape is regular, False if lot shape is irregular
|zone_FV|uint|Home Value & Kaggle|Indicates if home is zoned as floating villiage residential
|zone_RL|uint|Home Value & Kaggle|Indicates if home is zoned as residential low density
|zone_RM|uint|Home Value & Kaggle|Indicates if home is zoned as residential medium density
|house_type_1Fam|uint|Home Value & Kaggle|Indicates if dwelling type is single-family detached
|house_type_Twnhs|uint|Home Value & Kaggle|Indicates if dwelling type is townhouse
|neighborhood_Edwards|uint|Kaggle|Indicates if home if in Edwards neighborhood
|neighborhood_IDOTRR|uint|Kaggle|Indicates if home if in Iowa DOT and Rail Road neighborhood 
|neighborhood_NAmes|uint|Kaggle|Indicates if home if in North Ames neighborhood
|neighborhood_NoRidge|uint|Home Value & Kaggle|Indicates if home if in Northridge neighborhood 
|neighborhood_NridgHt|uint|Home Value & Kaggle|Indicates if home if in Northridge Heights neighborhood 
|neighborhood_OldTown|uint|Kaggle|Indicates if home if in Old Town neighborhood
|neighborhood_StoreBr|uint|Home Value & Kaggle|Indicates if home if in Stone Brook neighborhood
|remodel_yn|bool|Kaggle|True if home has ever been remodeled or added to, False if not 
|fireplaces|int|Kaggle|Number of fireplaces
|fireplace_yn|bool|Home Value & Kaggle|True if home has 1 or more fireplaces, False if not
|pool_yn|bool|Kaggle|True if home has a pool, False if not
|fence_yn|bool|Kaggle|True if home has a fence, False if not
|railroad_yn|bool|Kaggle|True if home is adjacent or within 200' of a railroad
|garage_cars|float|Kaggle|Size of garage in car capacity
|bsmt_ok_yn|bool|Home Value & Kaggle|True if basement condition is typical or better
|bsmt_usable_yn|bool|Home Value & Kaggle|True if basement finish type is average or above
|bsmt_cond_2|int|Home Value & Kaggle|6 point ranking of basement quality. Converted from ordinal to numeric
|bsmt_qual_2|int|Kaggle|6 point ranking of basement ceiling height. Converted from ordinal to numeric
|house_sf_x_overall_qual|float|Kaggle|Polynomial feature multiplying total house sq footage by quality score
|overall_qual_x_overall_cond|int|Kaggle|Polynomial feature multiplying overall quality and condition scores
|bsmt_sf_x_cond2|float|Kaggle|Polynomial feature multiplying basement sq footage by basement condition score
|bsmt_sf_x_hgt|float|Kaggle|Polynomial feature multiplying basement sq footage by basement quality score
|saleprice|int|Home Value & Kaggle|Actual home sale price in dollars

### Conclusions and Recommendations

The strongest predictors of house value from the Home Value model were Overall Home Quality, Above Ground Square Footage, Total House Square Footage (incl Basement), being located in the Northridge Heights neighborhood, and Exterior Quality of the home. 

The Home Value model had an R2 score of 0.88, meaning about 88% of variations in sale price of an Ames home can be explained by the model 

Realtors should direct homeowners to improve the following features of their homes in order to maximize house value:
* Overall Quality, including the finishes and materials throughout the house
* Exterior Quality, materials on the exterior of the house
* Basement Condition, including decreasing dampness and any structural damage
* Number of Fireplaces
* Above Ground Square Footage
* Basement Square Footage
* Porch or Deck, either add or increase square footage
* Bathrooms, add new or convert a half bath to full bath

For the Kaggle Challenge, the strongest predictors of home sale price were:
* Total house square footage x Overall quality score
* Basement square footage x Basement ceiling height score
* Basement condition
* Overall quality x overall condition of house
* Year built

The Kaggle model had an R2 score of 0.919, meaning about 92% of variation in sale price of an Ames home can be explained by the model. 


---
