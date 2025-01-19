# insights-from-airbnb-brstol
doing an analysis for the dataset about bristlon
## For the following analysis, I have downloaded the following data from: https://data.insideairbnb.com/united-kingdom/england/bristol/2024-09-23/data/calendar.csv.gz
``` diff
import pandas as pd
data = pd.read_csv('calendar.csv')
```

## T stands for available, F stand for not available

``` diff
data.available.value_counts()
```
![image](https://github.com/user-attachments/assets/70348499-bf58-4d0c-8200-b0ef49ae1ee5)
