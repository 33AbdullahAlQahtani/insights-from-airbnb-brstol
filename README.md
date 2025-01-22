# insights-from-airbnb-brstol
doing an analysis for the dataset about bristlon:
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

