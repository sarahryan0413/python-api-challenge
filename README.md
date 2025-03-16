# Weather Data Analysis: Exploring the Relationship Between Latitude and Climate Variables
## Project Overview 🌍☀️💨
The goal of this project is to analyze the relationship between latitude and various weather conditions, including temperature, humidity, cloudiness, and wind speed. The expectation is that cities closer to the equator will generally be warmer. To test this, I used Python to generate 1,500 random latitude/longitude pairs and mapped them to real-world cities using the Citipy library. Then, I retrieved weather data for those cities using the OpenWeatherMap API.
## Data Collection & Challenges 🔍📊
### Step 1: Initial API Call
Before retrieving data for all 1,500 cities, I first tested a single city (Minneapolis) to explore the API response. I sent a GET request and converted the response to JSON to get a feel for the structure of the data.
### Step 2: Fetching Weather Data
After confirming the API response structure, I wrote a for loop to extract key data points, including:
- Latitude & Longitude
- Maximum Temperature
- Humidity
- Cloud Coverage
- Wind Speed
- Country
- Date
To handle errors (e.g., missing data or failed API requests), I implemented a try-except block to skip any problematic cities.
### Step 3: Data Wrangling & Adjustments
During data collection, I ran into some interesting challenges:
1. Temperature Scale Mix-Up 🥶🔥 - Initially, I didn't realize the API returned temperatures in Kelvin, so my first scatterplots looked completely off. I fixed this by adding units=metric to my API request to convert temperatures to Celsius.
2. Date Mismatch in Scatterplots 📅 - My temperature scatterplot had a lot of negative values, which didn’t match the example plot in the project instructions. I discovered that the example used a fixed date (2024-06-17), while my data was dynamic. To ensure my plot reflects the current date each time it’s opened, I used Python’s datetime module.
3. Odd Temperature Clusters 🏔️ - Some temperatures in the 20°-80° latitude range seemed too cold. After cross-checking real-time weather reports, I confirmed these were accurate—many northern hemisphere cities were experiencing winter, while southern cities remained warmer.
4. Dynamic Regression Line Labels 📈 - I created a function to dynamically annotate my linear regression plots. Initially, the text didn’t appear in some plots because I set the coordinates to (0,0). To fix this, I adjusted the annotation based on the minimum x and y values of each plot.
## Key Findings 🔬📉
### Temperature vs. Latitude 🌡️
- Northern Hemisphere: There is a moderately strong negative correlation (r² = 0.70), meaning temperatures decrease as you move north from the equator. The y-intercept (35.55°C) suggests the temperature at 0° latitude would be quite hot.
- Southern Hemisphere: There is a weaker positive correlation (r² = 0.27), showing a general warming trend closer to the equator. However, the relationship isn’t as strong as in the north.
- Seasonal Impact: Many northern cities are significantly colder than their southern counterparts, which makes sense given the current winter season in the Northern Hemisphere.
### Humidity vs. Latitude 💧
- Northern Hemisphere: Weak positive correlation (r² = 0.18). Surprisingly, humidity increases as you move north, possibly due to seasonal snowstorms adding moisture to the air.
- Southern Hemisphere: No significant relationship (r² = 0.06), suggesting latitude alone doesn’t determine humidity—other factors like local weather systems play a bigger role.
- Equatorial Variability: Humidity levels near 0° latitude range from 0% to 100%, showing that not all equatorial cities are humid.
### Cloudiness vs. Latitude ☁️
- Northern Hemisphere: No strong correlation (r² = 0.03), but an interesting bimodal clustering—many cities either have 0% or 100% cloud coverage, with few in between.
- Southern Hemisphere: Similarly weak correlation (r² = 0.06). However, between latitudes -20 and 0, there’s a noticeable concentration of 100% cloud cover, suggesting potential regional weather patterns.
- Conclusion: Latitude does not predict cloudiness well, and local climate factors seem to have a stronger influence.
### Wind Speed vs. Latitude 🌬️
- Northern Hemisphere: Extremely weak correlation (r² = 0.02), with wind speeds clustering mostly between 0-8 m/s.
- Southern Hemisphere: Slightly stronger correlation (r² = 0.07), but still not significant. High wind speeds are uncommon in both hemispheres.
- Conclusion: Latitude does not strongly influence wind speed, but equatorial regions see slightly higher variation.
## Final Thoughts 💡
This project confirmed that latitude has a significant impact on temperature, with a stronger correlation in the Northern Hemisphere due to the current winter season. However, other factors—like geography, weather patterns, and seasonal conditions—play major roles in humidity, cloudiness, and wind speed. While I found some intriguing patterns, it’s clear that latitude alone isn’t enough to predict most weather variables.  

Future improvements could include:
- Analyzing seasonal trends over multiple months.
- Comparing data for cities at the same latitude but different elevations.
- Exploring the impact of ocean proximity on climate variables.  

Overall, this project was a great opportunity to practice working with APIs, JSON parsing, data visualization, and linear regression. 📊🐍🚀  

📊 Data provided by edX Boot Camps LLC for educational purposes.
