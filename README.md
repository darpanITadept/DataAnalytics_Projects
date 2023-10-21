# Tableau Visualization

You can access the Tableau visualization of this dataset by following this [Tableau Viz Link](<https://public.tableau.com/app/profile/darpan.choudhary/viz/LondonBikeRide_Dashboard/Dashboard1?publish=yes>).

#### Key Dashboard Features

- **Rental Trends**: Visualize the trends in bike rentals over time, allowing you to identify patterns and fluctuations.

- **Weather Impact**: Analyze how weather conditions affect bike rental counts with easy-to-read charts and graphs.

- **Seasonal Variations**: Discover the impact of seasons on bike rentals, helping you understand the popularity of bike usage in different seasons.

### Dashboard Images

Here are some images of the Tableau visualization dashboard:

![Dashboard Image 1](<insert_image_1_link_here>)
![Dashboard Image 2](<insert_image_2_link_here>)
![Dashboard Image 3](<insert_image_3_link_here>)

## Project Readme

This project involves working with a dataset containing information about bike rentals in London. The dataset has been cleaned and transformed to make it more user-friendly, with columns renamed and some values mapped to their corresponding descriptions. The project code is provided below. 

### Project Code

```python
import pandas as pd

# Load the dataset
bikes = pd.read_csv("london_merged.csv")

# Display dataset information
bikes.info()

# Get the shape of the dataset
bikes.shape

# Display the dataset
bikes

# Count the unique values in the 'weather_code' column
bikes.weather_code.value_counts()

# Count the unique values in the 'season' column
bikes.season.value_counts()

# Specifying the column names that we want to use
new_cols_dict = {
    'timestamp': 'time',
    'cnt': 'count',
    't1': 'temp_real_C',
    't2': 'temp_feels_like_C',
    'hum': 'humidity_percent',
    'wind_speed': 'wind_speed_kph',
    'weather_code': 'weather',
    'is_holiday': 'is_holiday',
    'is_weekend': 'is_weekend',
    'season': 'season'
}

# Renaming the columns to the specified column names
bikes.rename(new_cols_dict, axis=1, inplace=True)

# Changing the humidity values to percentage (i.e., a value between 0 and 1)
bikes.humidity_percent = bikes.humidity_percent / 100

# Creating a season dictionary to map integers 0-3 to the actual written values
season_dict = {
    '0.0': 'spring',
    '1.0': 'summer',
    '2.0': 'autumn',
    '3.0': 'winter'
}

# Creating a weather dictionary to map the integers to the actual written values
weather_dict = {
    '1.0': 'Clear',
    '2.0': 'Scattered clouds',
    '3.0': 'Broken clouds',
    '4.0': 'Cloudy',
    '7.0': 'Rain',
    '10.0': 'Rain with thunderstorm',
    '26.0': 'Snowfall'
}

# Changing the 'season' column data type to string
bikes.season = bikes.season.astype('str')

# Mapping the values 0-3 to the actual written seasons
bikes.season = bikes.season.map(season_dict)

# Changing the 'weather' column data type to string
bikes.weather = bikes.weather.astype('str')

# Mapping the values to the actual written weathers
bikes.weather = bikes.weather.map(weather_dict)

# Display the first few rows of the cleaned dataset
bikes.head()

# Save the cleaned dataset to an Excel file
bikes.to_excel('london_bikes_final.xlsx', sheet_name='Data')
```

### Tableau Visualization

Explore the dataset through a Tableau visualization that provides insightful and interactive visualizations of the data. Follow the provided [Tableau Viz Link](<insert_link_here>) to access the visualization.



Feel free to explore the dataset and the visualization. If you have any questions or need further assistance, please don't hesitate to reach out.

Happy analyzing!