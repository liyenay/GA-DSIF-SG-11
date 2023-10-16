
# Project 2 - HDB resale pricing analysis

by Liyena Putri Yusoff


## Background

The Singapore Housing Development Board (HDB) is a government agency founded in 1960. Its mission is to provide affordable and quality public housing to Singapore residents, ensuring access to comfortable and secure homes for all citizens, contributing to a better quality of life, and fostering community well-being. The first batch of HDB flats in Singapore was completed in February 1960.


## Problem Statement

Public houses are meant to be affordable, however certain housing areas seem to be cheaper than others despite having the same amenities and accessiblities around them. While keeping the houses affordable, our goal is to use data to determine the amenities and facilities that cause the highest change in price for a more efficient allocation of state resources in bringing up the appeal of seemingly undervalued units.

## Summary
This is a supervised learning project involving regression models. Metrics scores such as the RMSE and R2 scores are used as evaluation. The best performing model that was found is the RidgeCV giving a RMSE train score of 36641.033 and RMSE test score of 36461.758. The top features that we have found contributing to the resale prices are: `floor_area_sqm`, `hdb_age`, and `mrt_nearest_distance`.

### Notebooks
* [Data_Cleaning_EDA.ipynb](Data_Cleaning_EDA.ipynb)
* [Pre_Processing_Modeling.ipynb](Pre_Processing_Modeling.ipynb)

### Datasets
The [`train.csv`](notebooks/datasets/train.csv) and [`test.csv`](notebooks/datasets/test.csv) consist of data from 2012 to 2021.

### Key Features

|Feature|Type|Description|
|---|---|---|
|Tranc_YearMonth|object|train|Year and month of the resale transaction, e.g. 2015-02|
|flat_type|object|Type of the resale flat unit, e.g. 3 ROOM|
|flat_model|object|HDB model of the resale flat, e.g. Multi Generation|
|hdb_age|integer|number of years from lease_commence_date to present year|
|mid_storey|integer|median value of storey_range|
|floor_area_sqm|float|floor area of the resale flat unit in square metres|
|commercial|object|train|boolean value if resale flat has commercial units in the same block|
|market_hawker|object|train|boolean value if resale flat has a market or hawker units in the same block|
|max_floor_lvl|integer|train|highest floor of the resale flat|
|mall_nearest_distance|float|distance (in metres) to the nearest mall|
|mrt_nearest_distance|float|distance (in metres) to the nearest MRT station|
|pri_sch_name|object|name of the nearest primary school|
|pri_sch_nearest_distance|float|distance (in metres) to the nearest primary school|
|sec_sch_name|object|name of the nearest secondary school|

### Key Data Cleaning Steps
1. Dropping unnecessary columns
2. Imputation of null values to 0 or mean values
3. Assigned numeric values to binary categorical columns

### Illustrations

[Barchart of amenities by towns and 4-room resale prices by towns](notebooks/images/amenities_town_4room_price.png)

[Top 30 features affecting HDB resale prices.](notebooks/images/top_30_coeff.png)

### Pre-processing and Modelling
* Feature-engineered features: `food_mark_stalls`, `mrt_pri_dist`,` mar_haw_pavi`, `comm_pavi`, `mscp_pavi`, `comm_mscp`
* Standard scaled the numeric features
* Get-dummy on categorical columns

The models include:
* Linear Regression
* LassoCV
* RidgeCV

### Evaluation of Models
* Root Mean Square Error (RMSE)
* R2 score

| Model       |Alpha value| R2 Score (Train) | R2 Score (Test) | RMSE (Train) | RMSE (Test) | Remarks         |
|-------------|-----------|------------------|-----------------|--------------|-------------|-----------------|
| Linear Regression     |  -  |  0.9091      |0.9094           | 36650.501    | 36476.541   | Good fit        |
| LassoCV               |  2  |  0.9091      |0.9095           | 36641.732     | 36465.649   | Good fit        |
| RidgeCV               |  5  |  0.9091      |0.9094           | 36641.033    | 36461.758   | Good fit        |

## Conclusion

The resale prices are benchmarked based on the floor area of each type of unit. Through the model, certain areas such as Woodlands, Choa Chu Kang and Sembawang have prices lower than those in other regions, despite having the amenities and schools close to the HDB blocks. It also seems that people prefer living in taller HDB flats and near the MRT stations for easy transaportation. 


## Recommendations

As most towns would already have their own MRT station, one way to improve the desireability of the houses is to have easy accessibility from the blocks to the MRT stations. This could be done by increasing the frequency of feeder buses to the mrt station and improving the infrastructure around the blocks to the nearest bus stop or MRT stations such as walkways or PCN (Park Connector Networks). 

## Limitations

The housing prices could also be affected by other factors such as the number of buses available in the district or the distance from the block to the nearest expressway, the nearest distance to a community centre (CC) and the activities held at the CCs, which could be better features to use as analysis. 

We could also analyse the availability of feeder buses for intra-town commute as well as inter-town buses to explore how the assessibility between these regions and places affect the desirability of the resale unit on the block.