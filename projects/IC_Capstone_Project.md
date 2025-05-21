---
layout: post
title: 'An Investigation into Food Hygiene Across Central London Boroughs'
---


## Executive Summary

This project explores the relationship between local affluence and food hygiene standards across Central London boroughs. The analysis reveals that more affluent areas generally exhibit higher hygiene performance. The region’s education and skill level may influence the food hygiene rating, and the living environment could be an indicator to distinguish the region's food hygiene conditions. 

Among the 12,242 food businesses analyzed, 67.2% received a 'Very Good' hygiene rating. Kensington and Chelsea, the City of London, and Greenwich rank as the top three boroughs with the highest average hygiene scores. Furthermore, business types in educational institutions, supermarkets, and healthcare or childcare facilities outperform more than commercialized businesses like mobile caterers, restaurants, and takeaway shops.


## Introduction

When choosing where to eat or shop for food, consumers often rely on platforms like Google Reviews, Tripadvisor, or Yelp, which offer user ratings, cost information, and customer feedback. However, an equally important yet often overlooked factor is food hygiene, a critical indicator of public health and safety. While this data is publicly available through government websites, it remains absent from mainstream commercial review apps. As a result, the public may lack knowledge of how food hygiene is performed in their living environment.

To fill this gap, this project focuses on food hygiene inspection performance within Central London boroughs. In order to gain a deep understanding of how they correlate with other factors, this project incorporates English Indices of Deprivation as geographical data, which covers multiple measurements at the postcode level, including Income, Employment and Skills, Crime Decile, Living Environment, etc. 
    
The aim of this project is to investigate whether a borough's level of affluence influences the hygiene standards of its food establishments. Key research questions include: Which boroughs demonstrate better hygiene performance? Does affluence correlate with food hygiene outcomes? What factors (e.g., deprivation metrics or business type) are associated with higher or lower hygiene ratings? All datasets used in this project are real, publicly available, and geographically granular, making this a robust, data-driven investigation into a public health issue.


## Methods 

This project draws upon two public datasets: the Food Hygiene Ratings dataset from the Food Standards Agency (accessed via food.gov.uk API) and the English Indices of Deprivation (2019) obtained from opendatacommunities.org. The raw hygiene dataset contains 40,302 observations and 10 attributes, covering food businesses’ hygiene ratings, business types, postcodes, and boroughs. The raw deprivation dataset includes 32,690 observations and 28 attributes describing multiple deprivation indicators at the Lower-layer Super Output Area (LSOA) level.

Before merging, both datasets were cleaned for preparation. For example, in the hygiene dataset, non-numeric rating values such as ‘AwaitingInspection’, ‘AwaitingPublication’, and ‘Exempt’ were removed, as these do not reflect actual inspection outcomes. Also, businesses sharing the same postcode were grouped together, and their hygiene ratings were averaged. For each postcode, the most common business type and borough were retained. The cleaned dataset kept only four relevant columns: Postcode, Hygiene Rating, Business Type, and Borough.

In the deprivation dataset, only postcodes present in the cleaned hygiene dataset were extracted to ensure consistency during the merge. Of the three metric types available, Rank, Score, and Decile, only Scores and Deciles were retained, as Ranks are more ordinal in nature and less interpretable in statistical modeling.

The two datasets were merged using a left join on the Postcode column, ensuring all food hygiene records were preserved even if corresponding deprivation data was missing. This decision was based on the assumption that food hygiene data was the project’s primary focus.

After the merge, exploratory data analysis (EDA) was performed using Pandas, Geopandas, Matplotlib, Seaborn, and Statsmodels, in making bar charts, geographical maps, heatmaps, and regressions. 


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

![Correlation between Hygiene Rating and Deprivation Decile Metrics by Borough](https://github.com/user-attachments/assets/5c4a997b-ee24-4823-b154-f7d1f8917816)


Figure 7.  After a multiple regression analysis, the Living Environment Decile stands out for its distinct contribution in the whole matrix. Even if it's not obvious in stand-alone correlations, better living environments may indirectly support the hygiene performance of local food businesses in the borough.

![OLS Coefficients (with 95% CI)](https://github.com/user-attachments/assets/4ea340fe-803b-4506-80a3-8cafe71e31a1)


## Conclusion

This project investigates food business hygiene ratings across Central London boroughs and explores the relationship between regional affluence and food hygiene conditions. It practiced data collection, wrangling, and visualization for the exploratory analysis by using various data analytics tools like geographical mappings, heatmaps, and regressions.

In general, most food businesses (67.2%) retain a ‘very good’ rating. Education institutes, supermarket retailers, and hospitals/childcare exhibit better than mobile caterers, restaurants, and takeaway shops. Kensington and Chelsea, City and London, and Greenwich have the highest average food hygiene rating. By leveraging the deprivation data, this investigation reveals that the more affluent boroughs tend to have higher food hygiene performance. Living environment could be a strong factor to predict the general food hygiene conditions of a borough, and education and skill level in a borough have a notable correlation with food hygiene rating.

By integrating meaningful insights from this project, education level and awareness in a borough likely play a critical role in improving local food businesses’ hygiene standards. As a practical implication, local councils may consider investing in food hygiene and safety training for local food businesses, particularly in areas with lower education and skills levels, to strengthen compliance awareness of business owners, balancing hygiene inequality between boroughs.

For future research, this project could add additional attributes regarding the food business’s average spending, reviews, or public rating in commercial apps. In doing so, it would be beneficial for building models for food enterprises to predict price, select location, and generate managerial decisions. Also, policymakers could generate insights to find problems, prioritize resources, and ensure that all boroughs, regardless of affluence, maintain high food hygiene and safety standards.

