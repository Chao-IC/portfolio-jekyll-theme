---
layout: post
title: 'Project One'
---
Executive Summary

This project explores the relationship between local affluence and food hygiene standards across Central London boroughs. The analysis reveals that more affluent areas generally exhibit higher hygiene performance. The region’s education and skill level may influence the food hygiene rating, and the living environment could be an indicator to distinguish the region's food hygiene conditions. 
    Among the 12,242 food businesses analyzed, 67.2% received a 'Very Good' hygiene rating. Kensington and Chelsea, the City of London, and Greenwich rank as the top three boroughs with the highest average hygiene scores. Furthermore, business types in educational institutions, supermarkets, and healthcare or childcare facilities outperform more than commercialized businesses like mobile caterers, restaurants, and takeaway shops.


Introduction

When choosing where to eat or shop for food, consumers often rely on platforms like Google Reviews, Tripadvisor, or Yelp, which offer user ratings, cost information, and customer feedback. However, an equally important yet often overlooked factor is food hygiene, a critical indicator of public health and safety. While this data is publicly available through government websites, it remains absent from mainstream commercial review apps. As a result, the public may lack knowledge of how food hygiene is performed in their living environment.
    To fill this gap, this project focuses on food hygiene inspection performance within Central London boroughs. In order to gain a deep understanding of how they correlate with other factors, this project incorporates English Indices of Deprivation as geographical data, which covers multiple measurements at the postcode level, including Income, Employment and Skills, Crime Decile, Living Environment, etc. 
    The aim of this project is to investigate whether a borough's level of affluence influences the hygiene standards of its food establishments. Key research questions include: Which boroughs demonstrate better hygiene performance? Does affluence correlate with food hygiene outcomes? What factors (e.g., deprivation metrics or business type) are associated with higher or lower hygiene ratings? All datasets used in this project are real, publicly available, and geographically granular, making this a robust, data-driven investigation into a public health issue.


Methods 

This project draws upon two public datasets: the Food Hygiene Ratings dataset from the Food Standards Agency (accessed via food.gov.uk API) and the English Indices of Deprivation (2019) obtained from opendatacommunities.org. The raw hygiene dataset contains 40,302 observations and 10 attributes, covering food businesses’ hygiene ratings, business types, postcodes, and boroughs. The raw deprivation dataset includes 32,690 observations and 28 attributes describing multiple deprivation indicators at the Lower-layer Super Output Area (LSOA) level.
    Before merging, both datasets were cleaned for preparation. For example, in the hygiene dataset, non-numeric rating values such as ‘AwaitingInspection’, ‘AwaitingPublication’, and ‘Exempt’ were removed, as these do not reflect actual inspection outcomes. Also, businesses sharing the same postcode were grouped together, and their hygiene ratings were averaged. For each postcode, the most common business type and borough were retained. The cleaned dataset kept only four relevant columns: Postcode, Hygiene Rating, Business Type, and Borough.
    In the deprivation dataset, only postcodes present in the cleaned hygiene dataset were extracted to ensure consistency during the merge. Of the three metric types available, Rank, Score, and Decile, only Scores and Deciles were retained, as Ranks are more ordinal in nature and less interpretable in statistical modeling.
    The two datasets were merged using a left join on the Postcode column, ensuring all food hygiene records were preserved even if corresponding deprivation data was missing. This decision was based on the assumption that food hygiene data was the project’s primary focus.
    After the merge, exploratory data analysis (EDA) was performed using Pandas, Geopandas, Matplotlib, Seaborn, and Statsmodels, in making bar charts, geographical maps, heatmaps, and regressions. 


Results

Figure 1.  Of the 12,242 food businesses surveyed, 67.2% achieved a ’Very Good’ hygiene rating, while 5% required various degrees of improvement (ratings 0 to 3).
![Distribution of Hygiene Ratings in Central London Boroughs](https://github.com/user-attachments/assets/960d12ed-b276-4169-9085-a4780abfabbc)





{% include image.html url="http://www.gratisography.com" image="projects/proj-1/dog.jpg" %}

{% include image.html url="http://www.gratisography.com" image="projects/proj-1/wall.jpg" %}
