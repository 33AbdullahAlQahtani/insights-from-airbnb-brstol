# insights-from-airbnb-brstol
doing an analysis for the dataset about bristol:
* For the following analysis, I have downloaded the following data from: https://data.insideairbnb.com/united-kingdom/england/bristol/2024-09-23/data/calendar.csv.gz
``` diff
import pandas as pd
data = pd.read_csv('calendar.csv')
```
# Now We Need To Put Up Questions for Our Data
Lets give our insights about the data!

# 1 We need to know the number of available and unavailable rooms :white_check_mark:
``` diff
data.available.value_counts()
```
![image](https://github.com/user-attachments/assets/70348499-bf58-4d0c-8200-b0ef49ae1ee5)

T stands for available, F stand for not available

# 2 Purpose: Calculates the percentage of available (t) and unavailable (f) dates.
Explaination: value_counts(normalize = True) gives proportions. Multiplying 100 converts the proportions into percentage

``` diff
availability_percentage = data['available'].value_counts(normalize = True) * 100
availability_percentage
```
![image](https://github.com/user-attachments/assets/c7ee91a2-e1b9-43e8-b95a-3c613055b1c3)

# 3 Let's Count the busiest day :triangular_flag_on_post:

Hint: We will be counting the most unavailable days (given by f)

``` diff
busiest_dates = data[data['available'] == 'f']['date'].value_counts()
print("Busiest Dates are:")
print(busiest_dates.head())
```
![image](https://github.com/user-attachments/assets/a3e5147d-12f0-49b4-94ad-4d137009865c)

# 4 Plot a bar graph to show availability percentage

``` diff
import matplotlib.pyplot as plt
availability_percentage.plot(kind = 'bar', color = ['green', 'red'])
plt.title('Availabilitiy Percentages')
plt.ylabel('Percentage')
plt.xlabel('Available (t/f)')
plt.show()
```
![image](https://github.com/user-attachments/assets/c337aece-9fb4-4b4f-8f29-a53b2bd48437)

# 5 Plotting the busiest day

``` diff
busiest_dates.head(10).plot(kind='bar', color='orange')
plt.title('Top 10 Busiest Dates for Airbnb Bristol')
plt.ylabel('Number of Listings Unavailable')
plt.xlabel('Date')
plt.show()
```
![image](https://github.com/user-attachments/assets/3a149898-27db-4c48-a237-825088972389)


# 6 Download and read listings for Bristol dataset Airbnb's 
We are going to get listings to help us visualize about airbnb locations. Retreirved from: https://data.insideairbnb.com/united-kingdom/england/bristol/2024-09-23/visualisations/listings.csv
``` diff
import pandas as pd
listings = pd.read_csv('listings.csv')
```
![image](https://github.com/user-attachments/assets/00e32f10-e878-4430-8966-d5cd7b2ac23f)

# 7 Listing the columns
We are going to see our dataset columns
``` diff
listings.columns
```
![image](https://github.com/user-attachments/assets/4e8365d9-f901-400c-9e2a-112c13aed1e9)

# 8 Room prices based on their type
Lets combine both columns, room type and prices

``` diff
import matplotlib.pyplot as plt
price_by_room = listings.groupby('room_type')['price'].mean()
print(price_by_room)

# Plot price by room type
price_by_room.plot(kind='bar', color='green')
plt.title('Average Price by Room Type')
plt.ylabel('Average Price')
plt.xlabel('Room Type')
plt.show()
```
![image](https://github.com/user-attachments/assets/9010168e-cad2-4790-b655-ca8fbdc1a4e6)

# :bookmark: 9 Top 10 Neighbourhoods with the most listings
We are going to plot a bar plot that conclude the neighbourhoods with the most listings

``` diff
neighborhood_counts = listings['neighbourhood'].value_counts().head(10)
print("Top 10 Neighborhoods by Listings in Bristol:")
print(neighborhood_counts)

# Plot neighborhoods with most listings
neighborhood_counts.plot(kind='bar', color='lightcoral')
plt.title('Top 10 Neighborhoods by Listings in Bristol')
plt.ylabel('Number of Listings')
plt.xlabel('Neighborhood')
plt.xticks(rotation=90)
plt.show()
```
![image](https://github.com/user-attachments/assets/2b0db1ba-2769-4c2d-ba22-5ac6bcf85e72)

# :art: 10 Geographical Distribution of Listings By Price
We are going to geographically show the distribution of airbnbs in bristol and coloring is based on price.

```diff
import matplotlib.pyplot as plt
import seaborn as sns

plt.figure(figsize=(10, 6))
sns.scatterplot(data=listings, x='longitude', y='latitude', hue='price', palette='viridis', size='price', sizes=(10, 200))
plt.title('Geographical Distribution of Listings in Bristol (Price Colored)')
plt.xlabel('Longitude')
plt.ylabel('Latitude')
plt.show()
```
![image](https://github.com/user-attachments/assets/c7995e95-a25e-4701-aa57-6c7cb05b7843)

# 11 Mapping our Airbnb listings about location density on a real map
We are going to map our airbnb listings based on their density for their given location
``` diff
```

