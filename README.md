Exp 6 : Perform Data Analysis and Representation on a Map Using Various Map Datasets with Mouse Rollover Effect, User Interaction

AIM:
To analyze data and represent it on a map, using various geographical datasets. Implement interactive visualizations with mouse rollover effects for better user engagement and understanding.

EQUIPMENTS REQUIRED:
Python
Libraries: folium, pandas, geopandas
Dataset URL: World Cities Dataset

ALGORITHM:
Load the dataset containing city information (latitude, longitude, and population) using pandas.
Visualize the data on a map using folium.
Add markers for each city on the map, displaying information when the user hovers over a city (mouse rollover effect).
Allow user interaction, such as zooming and panning on the map.
Customize the markers with popup information and use different colors for different city populations.

Program:

# Step 1: Import required libraries
import folium
import pandas as pd

# Step 2: Load dataset from URL (world cities dataset with latitudes, longitudes, and population)
url = "https://raw.githubusercontent.com/plotly/datasets/master/2014_world_gdp_with_codes.csv"
df = pd.read_csv(url)

# Step 3: View the first few records of the dataset
print("First few records of the dataset:")
print(df.head())

# Step 4: Create a folium map centered around the world
world_map = folium.Map(location=[20, 0], zoom_start=2)

# Step 5: Loop through each city in the dataset and add a marker to the map
for idx, row in df.iterrows():
    latitude = row['Lat']
    longitude = row['Lon']
    city = row['Country']
    gdp = row['GDP (BILLIONS)']

    # Step 6: Create a marker with popup info (City name and GDP)
    folium.CircleMarker(
        location=[latitude, longitude],
        radius=7,
        color='blue',
        fill=True,
        fill_color='blue',
        fill_opacity=0.7,
        popup=f"City: {city}<br>GDP: {gdp} Billion USD"
    ).add_to(world_map)

# Step 7: Save the map as an HTML file and display it
world_map.save("world_map.html")
print("Map has been saved as 'world_map.html'. You can open it in a browser to view the interactive map.")

EXPECTED OUTPUT:
Dataset Overview:
View the first few records of the dataset printed in the console.

Interactive Map:
A map is generated and saved as an HTML file, displaying all the cities with markers (circle markers).
Each marker is interactive: when you hover over or click on a marker, it will show a popup with the city name and its GDP (in billions).

Mouse Rollover Effect:
The mouse rollover effect is applied, showing information about the city (name and GDP) when hovering over the markers.

Zoom and Pan:
You can zoom in/out and move the map to explore different regions and cities.

RESULT:
This experiment demonstrates how to use folium to create interactive maps, adding markers for cities, and displaying additional information using popup features. It also showcases how to integrate user interaction like zooming, panning, and mouse rollover effects.
