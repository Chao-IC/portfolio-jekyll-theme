---
layout: post
title: 'An Investigation into Food Hygiene Across Central London Boroughs'
---


## Executive Summary

This project explores the relationship between local affluence and food hygiene standards across Central London boroughs. The analysis reveals that more affluent areas generally exhibit higher hygiene performance. The region’s education and skill level may influence the food hygiene rating, and the living environment could be an indicator to distinguish the region's food hygiene conditions. 

Among the 12,242 food businesses analyzed, 67.2% received a 'Very Good' hygiene rating. Kensington and Chelsea, the City of London, and Greenwich rank as the top three boroughs with the highest average hygiene scores, whereas Newham ranked worst. Furthermore, business types in educational institutions, supermarkets, and healthcare or childcare facilities outperform better than commercialized businesses like mobile caterers, restaurants, and takeaway shops.


## Introduction

When deciding where to eat or shop for food, people commonly turn to platforms like Google Reviews, Tripadvisor, or Yelp for insights into customer experiences, price expectations, and overall satisfaction. However, an equally important yet often overlooked factor is food hygiene, a critical indicator of public health and safety. While this data is publicly available through government websites, it remains largely absent from what platforms we have just mentioned. As a result, the public may remain unfamiliar with how food hygiene is practiced in food establishments in their local area.

To fill this gap, this project examines food hygiene performance across Central London boroughs, with a particular focus on how these outcomes relate to area-level deprivation. To enable this, the project integrates the English Indices of Deprivation, which provide detailed geographical data on factors such as income, employment, education, crime, and living environment at the postcode level. 
    
The aim of this project is to investigate whether a borough's level of affluence influences the hygiene standards of its food establishments. Key research questions include: Which boroughs demonstrate better hygiene performance? Does affluence correlate with food hygiene outcomes? What factors (e.g., deprivation metrics or business type) are associated with higher or lower hygiene ratings? All datasets used in this project are real, publicly available, and geographically granular, making this a robust, data-driven investigation into a public health issue.


## Methods 

This project draws upon two public datasets: the Food Hygiene Ratings dataset from the Food Standards Agency (accessed via food.gov.uk API) and the English Indices of Deprivation (2019) obtained from opendatacommunities.org. The raw hygiene dataset contains 40,302 observations and 10 attributes, covering food businesses’ hygiene ratings, business types, postcodes, and boroughs. The raw deprivation dataset includes 32,690 observations and 28 attributes describing multiple deprivation indicators at the Lower-layer Super Output Area (LSOA) level.

Before merging them, both datasets were cleaned. For example, in the hygiene dataset, non-numeric rating values such as ‘AwaitingInspection’, ‘AwaitingPublication’, and ‘Exempt’ were removed, as these do not reflect actual inspection outcomes. Also, businesses sharing the same postcode were grouped together, and their hygiene ratings were averaged. For each postcode, the most common business type and borough were retained. The cleaned dataset kept only four relevant columns: Postcode, Hygiene Rating, Business Type, and Borough. In the deprivation dataset, three metric types are available: Rank, Score, and Decile. Only scores and Deciles were retained, as Ranks are more ordinal in nature and less interpretable in statistical modeling.

The two datasets were merged using a left join on the Postcode column, ensuring all food hygiene records were preserved even if corresponding deprivation data was missing. This decision was based on the assumption that food hygiene data was the project’s primary focus. After the merge, exploratory data analysis (EDA) was performed using Pandas, Geopandas, Matplotlib, Seaborn, and Statsmodels, in making bar charts, geographical maps, heatmaps, and regressions. 


## Results

Figure 1.  Of the 12,242 food businesses surveyed, 67.2% achieved a ’Very Good’ hygiene rating, while 5% required various degrees of improvement (ratings 0 to 3).

![Distribution of Hygiene Ratings in Central London Boroughs](https://github.com/user-attachments/assets/960d12ed-b276-4169-9085-a4780abfabbc)


Figure 2.  A geographical map of Central London boroughs visualizes the average food hygiene ratings, highlighting spatial variation and inequality by borough.

![Average Food Hygiene Rating by Central London Borough](https://github.com/user-attachments/assets/64f01f97-0cd8-4a10-8621-1f2bc2f07962)


Figure 3.  Across the 14 Central London boroughs, Westminster, Camden, and Southwark host the highest numbers of food businesses, whereas Kensington and Chelsea, the City of London, and Greenwich exhibit the highest average hygiene ratings.

![Hygiene_Rating_Percentage_with_Business_Count](https://github.com/user-attachments/assets/3e79245d-03e5-4c03-9755-307020ac509b)


Figure 4.  Among the 14 identified food business types, establishments in educational institutions, supermarkets, and healthcare or childcare facilities demonstrate better hygiene performance.

![Percentage of Hygiene Ratings per Business Type (Sorted by Rating 5)](https://github.com/user-attachments/assets/82779468-8526-4cca-ab00-87b01f85c37b)


Figure 5.  A linear regression analysis of average deprivation decile versus hygiene rating by borough shows a moderately positive relationship between them, suggesting that less deprived (more affluent) boroughs tend to have higher hygiene ratings.

![Relationship Between Average Deprivation Decile and Hygiene Rating by Borough](https://github.com/user-attachments/assets/c05628e5-8357-411f-bf76-60796fd9a0d1)


Figure 6.  A heatmap visualizing the correlation between the hygiene rating and each deprivation decile, suggesting the highest correlation with a moderately strong relationship between Education and Skills and Hygiene Rating (r = 0.63). This result indicates that boroughs with better education and skill levels tend to have higher food hygiene ratings.

![Correlation between Hygiene Rating and Deprivation Decile Metrics by Borough_2](https://github.com/user-attachments/assets/c331b8e9-a3ba-4bd8-8ebe-21be46ca33ee)


Figure 7.  After a multiple regression analysis, the Living Environment Decile stands out for its distinct contribution in the whole matrix. Even if it's not obvious in stand-alone correlations, better living environments may indirectly support the hygiene performance of local food businesses in the borough.

![OLS Coefficients (with 95% CI)](https://github.com/user-attachments/assets/4ea340fe-803b-4506-80a3-8cafe71e31a1)


## Conclusion

This project investigates food business hygiene ratings across Central London boroughs and explores the relationship between regional affluence and food hygiene conditions. Through data collection, cleaning, and visualization, the analysis utilized tools such as geographic mapping, correlation heatmaps, and regression models to generate meaningful and actionable insights.

Overall, the majority of food businesses (67.2%) achieved a ‘Very Good’ hygiene rating. Educational institutions, supermarkets, and hospitals/childcare facilities tend to outperform mobile caterers, restaurants, and takeaway outlets. Among the boroughs, Kensington and Chelsea, the City of London, and Greenwich had the highest average hygiene ratings. By incorporating deprivation metrics, the analysis found that more affluent areas tend to have better hygiene outcomes. In particular, borough-level education and skill levels showed a notable positive correlation with hygiene ratings, and the living environment emerged as a potential predictor of overall hygiene conditions.

These findings suggest that education and awareness likely play a crucial role in shaping hygiene performance. As a practical implication, local councils may consider targeting food hygiene and safety training programs in areas with lower education and skills scores. This could help promote better compliance among business owners and reduce inequalities in food hygiene standards across boroughs.

For future research, additional variables such as customer reviews, average spending, or ratings from commercial platforms could be integrated. This would open opportunities for predictive modeling to assist food businesses in strategic decisions, including pricing and location planning. Policymakers could also use such data to identify areas needing support and allocate resources more effectively, ensuring consistent hygiene standards across all communities regardless of socioeconomic status.
