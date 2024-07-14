
# Airbnb Listing Analysis in Python

Data Scientist Portfolio Project: Airbnb Listing Analysis in Python

You've just been hired as a Performance Analyst for AirBnB, a platform that
allows individuals to rent out their homes for travellers

As AirBnB has grown in popularity, it has increasingly become the focus of
regulations designed to limit the number of properties listed in each city.
You've been asked to analyze Paris listings, with a focus on pricing. Leadership
wants a visual summary of factors affecting pricing and whether regulations
adopted in 2015 impacted listings in the Paris Market

1. Explore and profile the data to correct any quality issues
2. Prepare and reformat the data for visualization
3. Visualize the data and identify key insights and recommendations.

1. OBJECTIVE 1: PROFILE & QA THE DATA :



Import/Open the Listings.csv file

Cast any date columns as a datetime format

Filter the data down to rows where the city is Paris, and keep only the columns
'host_since', 'neighbourhood', 'city', 'accommodates', and 'price' in your table

QA the Paris listings data: check for missing values, and calculate the minimum, maximum,
and average for each numeric field


OBJECTIVE 2: PREPARE FOR VISUALIZATION :

Create a table named paris_listings_neighbourhood, that groups Paris listings by
`neighbourhood' and calculates the mean price for each neighborhood sorted from lowest
to highest average price

Then, create a table named paris_listings_accomodations. This table should be filtered down
to the most expensive neighborhood in Paris, grouped by the 'accommodations' column, and
contain the mean price for each value of 'accommodates' sorted from lowest to highest
average price

Finally, create a table called paris_listings_over_time, which is grouped by the year of the
'host_since' column. Calculate a count of rows, representing total number of new hosts,
and the average price for each year

OBJECTIVE 3: VISUALIZE THE DATA:

Create a horizontal bar chart of the average price by neighborhood in Paris. Make sure to
add a title and change axis labels as needed.

Create a horizontal bar chart of the average price by 'accommodates' in Paris' most
expensive neighborhood. Make sure to add a title and change axis labels as needed.

Create two line charts: one of the count of new hosts over time, and one for average
price, make sure to set the y-axis limit to O, add a title, and change axis labels as needed.

Based on your findings, what insights do you have about the impact of the 2015
regulations on new hosts and prices?

Challenge: Create a dual axis line chart that contains both new hosts and average price
ovor timo
1. import pandas as pd

Air = pd.read_csv("C:\\Users\\ismail\\Downloads\\Airbnb\\Listings.csv",encoding="ISO-8859-1", low_memory=False, parse_dates=["host_since"])

2.Air.head()

![Air Head](https://github.com/user-attachments/assets/70db6913-ea9f-49f9-8a86-d27f22769462)

3.Air.info()
4.Air["host_since"] = pd.to_datetime(Air["host_since"])

Air.info()

5.Air["host_since"] = pd.to_datetime(Air["host_since"])

Air.info()

6.Paris_Air.isna().sum()

7.Paris_Air.describe()

8.Paris_Air.query("accommodates == 0").count()

9. Paris_Air_neighbourhood = (Paris_Air.groupby("neighbourhood")
                           .agg({"price": "mean"})
                           .sort_values("price"))
Paris_Air_neighbourhood.tail()

10. Paris_Air_accommodates = (
    Paris_Air.query("neighbourhood == 'Elysee'")
             .groupby("accommodates")
             .agg({"price": "mean"})
             .sort_values("price")
)

Paris_Air_accommodates.tail()

11. import seaborn as sns
(Paris_Air_neighbourhood.plot
                       .barh(
                        title="Average Air Price by Paris Neighbourhood",
                         xlabel ="Price Per Night(Euros)",
                         ylabel= "Neighbourhood",
                         legend = None
                       ))
sns.despine()

![import sea](https://github.com/user-attachments/assets/0dc559bb-4d1e-42a9-b3a0-c0dc9616a65c)

12. import seaborn as sns
(Paris_Air_accommodates.plot
                       .barh(
                        title="Average Air Price by accommodates Number",
                         xlabel ="Price Per Night(Euros)",
                         ylabel= "Accommodation Capacity",
                         legend = None
                       ))
sns.despine()
![Avg price](https://github.com/user-attachments/assets/326f6c37-2612-460a-a5ed-f0b060de2b29)

13. import matplotlib.pyplot as plt
import seaborn as sns


fig, ax = plt.subplots()


ax.bar(
    Paris_Air_over_time.index,
    Paris_Air_over_time["neighbourhood"],
    color="pink"
)

ax.set_ylabel("New Hots")
ax.set_title("New Airbnb Hots in Paris Over Time")
sns.despine()
plt.show()

![BARR](https://github.com/user-attachments/assets/410a2397-f4f9-4ca9-a487-8829c8a1a12e)

