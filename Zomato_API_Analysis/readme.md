# INFO 7374 Data Analysis Using Python - Final Project
# Zomato API Analysis

![zomato](https://cloud.githubusercontent.com/assets/25044358/25308325/704e8e28-277f-11e7-91fd-521b74d145bf.jpg)
## Zomato Analysis:
Zomato API Analysis is one of the most useful analysis for foodies who want to taste the best cuisines of every part of the world which lies in their budget. This analysis is also for those who want to find the value for money restaurants in various parts of the country for the cuisines. Additionally, this analysis caters the needs of people who are striving to get the best cuisine of the country and which locality of that country serves that cuisines with maximum number of restaurants.:hotsprings:
### For more information on Zomato API and Zomato API key
•	Visit : [https://developers.zomato.com/api#headline1](https://developers.zomato.com/api#headline1)<br>
•	Data Collection: [https://developers.zomato.com/documentation]( https://developers.zomato.com/documentation)
## Data

### Fetching the data: 
•	Data has been collected from the Zomato API in the form of .json files(raw data) 
using the url=[https://developers.zomato.com/api/v2.1/search?entity_id=1&entity_type=city&start=1&count=20](https://developers.zomato.com/api/v2.1/search?entity_id=1&entity_type=city&start=1&count=20)<br>
•	Raw data can be seen [here](https://github.com/MehtaShruti/mehta_shruti_spring17/tree/master/Zomato_API_Analysis/Raw_Data)

### Data Collection:
Data collected can be seen as a raw .json file [here](https://github.com/MehtaShruti/mehta_shruti_spring17/blob/master/Zomato_API_Analysis/Raw_Data/file1.json)


### Data Processing :
 Data Processing has been done on the following categories: [Processed_Data](https://github.com/MehtaShruti/mehta_shruti_spring17/tree/master/Zomato_API_Analysis/Processed_Data)
1.	Currency
2.	City
3.	Location
4.	Rating Text

### Data Storage:
 
The collected data has been stored in the Comma Separated Value file [Zomato.csv](https://github.com/MehtaShruti/mehta_shruti_spring17/blob/master/Zomato_API_Analysis/csv/zomato.csv). Each restaurant in the dataset is uniquely identified by its Restaurant Id. Every Restaurant contains the following variables:
 
•	**Restaurant Id:** Unique id of every restaurant across various cities of the world<br>
•	**Restaurant Name:** Name of the restaurant<br>
•	**Country Code:** Country in which restaurant is located<br>
•	**City:** City in which restaurant is located<br>
•	**Address:** Address of the restaurant<br>
•	**Locality:** Location in the city<br>
•	**Locality Verbose:** Detailed description of the locality<br>
•	**Longitude:** Longitude coordinate of the restaurant's location<br>
•	**Latitude:** Latitude coordinate of the restaurant's location<br>
•	**Cuisines:** Cuisines offered by the restaurant<br>
•	**Average Cost for two:** Cost for two people in different currencies :couple: <br>
•	**Currency:** Currency of the country<br>
•	**Has Table booking:** yes/no<br>
•	**Has Online delivery:** yes/ no<br>
•	**Is delivering:** yes/ no<br>
•	**Switch to order menu:** yes/no<br>
•	**Price range:** range of price of food<br>
•	**Aggregate Rating:** Average rating out of 5<br>
•	**Rating color:** depending upon the average rating color<br>
•	**Rating text:** text on the basis of rating of rating<br>
•	**Votes:** Number of ratings casted by people<br>
*******************************************************************************************

# Analysis Performed: 

## Analysis I:  highest and lowest rated restaurants in the city (India and U.S.A)

### Objective:

To evaluate the Highest Rated and Lowest Rated Restaurant of the City in all the countries. Graph plotted only for countries with maximum restaurants (India and U.S.A)

### Approach:

Using pandas, grouping 'Country' and 'City', the aggregate rating is calculated and then the top and least rated restaurants are found for every city in that country

### Steps: 

1.	The file(zomato.csv) is read for the input to the data frame.
2.	The data is grouped by Country Code and City and reverse sorted to evaluate to the highest rated and lowest rated restaurants of all the countries.
3.	Merge the two data frames with highest rated and lowest rated restaurants in the city.
4.	Filter the data for two countries India and U.S.A.
5.	Plot the graph for two countries depicting all the cities in two countries with the highest and lowest rated restaurant with the location.


### Deliverables:

•	csv: **Analysis1.csv** <br>
[Download here]( https://github.com/MehtaShruti/mehta_shruti_spring17/blob/master/Zomato_API_Analysis/csv/Analysis1.csv)<br> 

<img width="1280" alt="analysis1" src="https://cloud.githubusercontent.com/assets/25044358/25308264/97792932-277e-11e7-9afd-5035a708ce78.png">

•	Grouped Bar Chart1: **Restaurants rating in India**<br>
[Download here]( https://github.com/MehtaShruti/mehta_shruti_spring17/blob/master/Zomato_API_Analysis/img/Analysis1.1_graph.png)<br>

<img width="735" alt="analysis1 1_graph" src="https://cloud.githubusercontent.com/assets/25044358/25308262/9759e90a-277e-11e7-822a-2d9a4569f7fa.png">


•	Grouped Bar Chart2: **Restaurants rating in U.S.A**<br>
[Download here]( https://github.com/MehtaShruti/mehta_shruti_spring17/blob/master/Zomato_API_Analysis/img/Analysis1.2_graph.png)<br>

<img width="715" alt="analysis1 2_graph" src="https://cloud.githubusercontent.com/assets/25044358/25308263/9778cd0c-277e-11e7-8ad4-d350a0a0d422.png">

### Conclusion: 

:thumbsup: From the analysis above (graphs and csv), we can easily determine the highest and lowest rated restaurant :hotel: of every city in the United States :us: and India, depending upon which we may plan to choose our restaurant for the location we are at. :smile:

*******************************************************************************************

## Analysis II: Populr cuisine of a country with location where it is served and number of restaurants serving that cuisine in that location

### Objective:

To evaluate the most popular cuisine of the world sold in a country and which locality in that country has most number of outlets selling that cuisine. Graph plotted only for the best cuisine of the country and the location where this cuisine is most popular with the count of places selling that cuisine.

### Approach:

Using pandas, splitting the multiple cuisines and stacking them up with the location, melting them with locality, grouping the locality and then country code and then reverse sorting the count of restaurants in the country with their names.

### Steps:

1.	The file(zomato.csv) is read for the input to the data frame.<br>
2.	DataFrame is filtered for all not null values for cuisines.<br>
3.	Series Cuisines is splitted by ‘,’ for separate different cuisine values as a new dataframe.<br>
4.	Concatenate the dataframe Zomato with cuisines.<br>
5.	For every locality stack the cuisines(all cuisines displayed row wise than columns).<br>
6.	Melt the cuisine values for every row.<br>
7.	The rows are grouped by Locality Verbose and sorted by reverse count and store it in a dataframe ‘loc’.<br>
8.	Merge zomato and loc dataframe on Locality Verbose.<br>
9.	Group by the dataframe in step 8 on ‘Country Code’.<br>
10. Reverse Sort  the data on the basis of the Number of restaurants in the city for that cuisines.<br>
11. Plot the graph for the most popular cuisines of the world and which location in that country they are most popular and how many restaurants in that location are selling them.<br>
12. Horizontal Bar graph 2 represents the most popular cuisines of the India and which location in India they are most popular and how many restaurants in that location are selling them.<br>



### Deliverables:

•	csv: **Analysis2.csv**<br>
[Download here]( https://github.com/MehtaShruti/mehta_shruti_spring17/blob/master/Zomato_API_Analysis/csv/Analysis2.csv)<br>

<img width="1280" alt="analysis2" src="https://cloud.githubusercontent.com/assets/25044358/25308266/977c4ed2-277e-11e7-8d21-85739a267da5.png">

•	Bar Chart1: **Popular cuisines rating in the World**<br>
[Download here]( https://github.com/MehtaShruti/mehta_shruti_spring17/blob/master/Zomato_API_Analysis/img/Analysis2.1_graph.png)<br>

<img width="741" alt="analysis2 1_graph" src="https://cloud.githubusercontent.com/assets/25044358/25308265/977a173e-277e-11e7-9e8c-fba61d5c7574.png">

•	Bar Chart 2:  **Popular cuisines rating in India**<br>
[Download here]( https://github.com/MehtaShruti/mehta_shruti_spring17/blob/master/Zomato_API_Analysis/img/Analysis2.2_graph.png)<br>


<img width="722" alt="analysis2 2_graph" src="https://cloud.githubusercontent.com/assets/25044358/25308268/978e1482-277e-11e7-903c-4477d84e6960.png">

### Conclusion: 

:thumbsup: From the analysis above (graphs and csv), we can easily determine the cuisine we want to try and check which country is famous for that cuisine and which part of that country that world famous cuisine and how many restaurants in that location are serving that cuisine. This analysis will help us choosing the best location in that country for the most famous cuisine.
:poultry_leg: :stew: :fries: :pizza: 
*******************************************************************************************

## Analysis III: Value for money restaurants of U.S.A for the best cuisines

### Objective:

To evaluate the value for money restaurants in the U.S.A  for the best cuisines served in the cities of U.S.A(value for money refers to the restaurants with highest rating and lowest cost)

### Approach:

Using pandas, splitting the multiple cuisines and stacking them up with the location, melting them with locality, grouping the locality and then country code and then forward sorting the average cost for two and reverse sorting the rating in the country with the names of the restaurants

### Steps:

1. The file(zomato.csv) is read for the input to the data frame.<br>
2. DataFrame is filtered for all not null values for cuisines.<br>
3. Series Cuisines is splitted by ‘,’ for separate different cuisine values as a new dataframe.<br>
4. Concatenate the dataframe Zomato with cuisines.<br>
5. For every locality stack the cuisines(all cuisines displayed row wise than columns).<br>
6. Melt the cuisine values for every row.<br>
7. The rows are grouped by Locality Verbose and sorted by reverse count and store it in a dataframe ‘loc’.<br>
8. Merge zomato and loc dataframe on Locality Verbose.<br>
9. Filter the data on the country code of USA.<br>
10. Group by on City, Cuisines, Locality Verbose and sort on the basis of Average Cost for two.<br>
11. Check if rating greater than 4.5 and Average cost is less than 40$ than value for money restaurants for a particular cuisine.<br>

### Deliverables:

•	csv: **Analysis3.csv** <br>
[Download here]( https://github.com/MehtaShruti/mehta_shruti_spring17/blob/master/Zomato_API_Analysis/csv/Analysis3.csv)<br>

<img width="1280" alt="analysis3" src="https://cloud.githubusercontent.com/assets/25044358/25308270/97953e38-277e-11e7-9392-6215ac9a9d72.png">

•	 Basemap: **Value for money restaurants in the U.S.A**<br>
[Download here]( https://github.com/MehtaShruti/mehta_shruti_spring17/blob/master/Zomato_API_Analysis/img/Analysis3_graph.png)<br>


<img width="511" alt="analysis3_graph" src="https://cloud.githubusercontent.com/assets/25044358/25308269/979484e8-277e-11e7-99fb-4fa7cb2360cc.png">

### Conclusion: 

:thumbsup: 
From the analysis above (graphs and csv), we can easily determine the value for money restaurants of the United States :us: We definitely want to pay less and get the best quality food with best services, this analysis helps us determining the best value for money restaurant of U.S.A with the location.
************************************************************************************************************************************************************************************************
