# Trend Analysis of COVID-19 Cases Using Open Data 
 
## 1. Topic Selection 
For this mini project under the course *Analysis of Large Datasets*, I chose to explore COVID-19 case trends using global open data. The pandemic has impacted all sectors globally, and analyzing trends in case numbers can help understand outbreak dynamics over time. The project is focused, time-bound, and feasible within the scope of this course, especially since the data is freely available and ready for analysis. 
 
## 2. Problem Definition 
The main objective of this project is to analyze and visualize trends in COVID-19 cases using real-world open data. I aim to uncover how cases evolved over time in selected countries, identify key peaks in infection rates, and explore correlations with other variables like deaths or vaccination rates. This analysis will help interpret patterns and make informed observations about the progression of the pandemic. 
 
## 3. Background Study 
COVID-19 has been widely studied using data analytics to inform public health policies and monitor the virus's spread. Numerous datasets have been published to support these efforts. One of the most popular sources is Our World in Data (OWID), which provides updated, structured COVID-19 data, including confirmed cases, deaths, and vaccinations. 
Trend analysis and time series visualization are core techniques used to monitor pandemics, making them suitable for this project. I utilized Python for its powerful libraries in data processing and visualization. 
 
## 4. Methodology or Approach 
- Python (Pandas, Matplotlib, Seaborn, NumPy) 
- Jupyter Notebook for scripting 
- OWID COVID-19 Dataset (CSV) 
 
**Steps:** 
1. Data Collection from OWID. 
2. Data Cleaning and selection of relevant columns. 
3. Country-specific filtering (Kenya, USA, India). 
4. Trend plotting using line graphs and 7-day moving averages. 
5. Correlation with vaccination and death rates. 
 
### 5. Implementation or Analysis 
**a. Loading and Cleaning Data:** 
```python 
import pandas as pd 
df = pd.read_csv('owid-covid-data.csv') 
df = df[['date', 'location', 'new_cases', 'total_cases', 'new_deaths', 'total_deaths', 'people_vaccinated_per_hundred']] 
df['date'] = pd.to_datetime(df['date']) 
df = df[df['location'] == 'Kenya'] 
``` 
 
**b. Plotting Trends and Moving Average:** 
```python 
df['7_day_avg'] = df['new_cases'].rolling(window=7).mean() 
``` 
**Plot: Daily New Cases with 7-Day Moving Average** 
![Daily New Cases](Screenshots/daily_new_cases.png) 
 
**c. Peak Detection:** 
```python 
peak_day = df[df['new_cases'] == df['new_cases'].max()] 
``` 
 
**d. Case Fatality Rate (CFR) Analysis:** 
```python 
df['CFR'] = (df['total_deaths'] / df['total_cases']) * 100 
``` 
**Plot: Case Fatality Rate (CFR) Over Time** 
![CFR Over Time](Screenshots/cfr_over_time.png) 
 
**e. Vaccination vs. Cases:** 
**Plot: Vaccination vs New Cases** 
![Vaccination vs Cases](Screenshots/vaccination_vs_cases.png) 
 
**Observations:** 
- The Case Fatality Rate (CFR) initially exceeded 5% but declined over time due to better healthcare response and vaccination. 
- Peaks in CFR corresponded to COVID-19 waves, indicating periods of healthcare strain. 
 
### 6. Results and Conclusion 
- Multiple infection waves were observed in Kenya, peaking in mid-2021 and early 2022. 
- The 7-day moving average smoothed erratic daily cases and revealed broader trends. 
- CFR analysis showed higher early fatality rates, declining with improved healthcare and vaccination. 
- Mass vaccination campaigns correlated with a decline in new cases. 
 
**Challenges Encountered** 
- Missing or inconsistent data in early pandemic months required extra cleaning. 
- Comparisons across countries required normalization due to differences in population and testing. 
 
**Future Improvements and Extensions** 
- Expand analysis to multiple countries or regions within Kenya for richer insights. 
- Incorporate forecasting models (ARIMA, Prophet) to predict trends. 
- Develop an interactive dashboard using Streamlit or Flask for real-time updates and dynamic exploration. 
