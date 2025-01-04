English | [한국어](README.ko.md)

# HealthCasting: A Health Alert System Paired with Search Trends

> A project on the theme of Exploratory Data Analysis, developed as part of *(KDT) ROS2 and AI-based Autonomous Robot Developer Training Program, 8th Cohort*.


<!--more-->

## Project Overview

- **Duration**: 2024.12.12 ~ 2025.01.03 (3 weeks)
- **Role**: Project lead and trend data owner
- **Goal**: Build a preventive health alert system based on search trends

> This is a fictional scenario, unrelated to real facts.

We are a team within the Health & Medical Data Promotion Division of the Advanced Medical Support Bureau, Ministry of Health and Welfare, tasked with analyzing data to prepare for the upcoming 53rd Health Day (April 7, 2025) and the April Health Month / Health Week (7th–13th) events.

By jointly analyzing weather data, disease occurrence statistics, and search trends,
we predict the likelihood of a specific disease (e.g., gastroenteritis) breaking out,
and propose a health forecasting system that can deliver an early warning to the public.

### Tech Stack
- **Language**: Python 3.10
- **Libraries**: Selenium, BeautifulSoup, pytrends, Pandas, Numpy, Matplotlib
- **Database**: MySQL, Amazon RDS, SQLAlchemy
- **Collaboration Tools**: Git, Slack, Jira, Confluence, Notion


### Team 4, overflowing with passion — **overflow**

| Role | Name (GitHub ID) | Summary of Responsibilities |
|------|------------------|----------------------------------------------------------|
| Team Lead | Yeonwoo Gim ([@mumallaeng](https://github.com/mumallaeng)) | - Standardized the project file structure and consolidated DB-related functions<br>- Collected Google Trends data and analyzed disease trend changes |
| Member | Kyuhwan Kim ([@kimsnake](https://github.com/kimsnake)) | - Collected and cleaned gastroenteritis patient counts from the healthcare data portal<br>- Analyzed disease occurrence statistics by age group and derived insights |
| Member | Serin Park ([@selnimon](https://github.com/selnimon)) | - Collected Naver Trends data<br>- Analyzed and visualized trend changes |
| Member | Sangyun Lee ([@sangyun1729](https://github.com/sangyun1729)) | - Collected daily regional weather data (temperature, humidity, diurnal range) from the Korea Meteorological Administration<br>- Analyzed correlations between weather variables and disease occurrence |

---


### Analysis Goals

- **Analyze the correlation between weather conditions and disease occurrence**
- **Examine the similarity between search trends and actual disease occurrence statistics**
- **Explore the feasibility of designing a climate-based disease alert system**

Determining whether a disease is trending based on weather conditions:

- Analyze the relationship between weather conditions and disease-related keywords
- Check whether an increase in searches for keywords (food poisoning, pharyngitis, etc.) correlates with an actual increase in disease occurrence: compare search trends for those keywords against disease data
- Combine weather data, disease occurrence data, and search trends to flag which disease to watch out for based on weather conditions
- Enable advance public notice of which diseases to watch for as weather changes


---

### Project Process

1. Project planning and topic definition
2. Data collection and cleaning
3. Correlation analysis and visualization
4. Disease trend analysis by age group and time period
5. Draft alert model and forecast derivation

---

### Data Used

| Category | Source | Details |
|----------|------|-----------|
| Weather data | KMA Weather Data Open Portal | Daily temperature, humidity, and diurnal range by region |
| Air quality data | AirKorea | PM10, PM2.5, and other particulate matter concentrations |
| Disease statistics | Health and Medical Big Data Open System | Gastroenteritis patient counts by age group |
| Search trends | Naver DataLab / Google Trends | Monthly search volume for disease-related keywords |

---



### Project Structure

**Data collection (data_collect/)**
- **Google Trends**: Collect disease-related search trends using pytrends
- **Naver Trends**: Collect domestic search trends via the Naver DataLab API
- **Weather data**: Scrape KMA data using Selenium

**Database upload (database_upload/)**
- Systematically store the collected data in a MySQL database
- Manage weather data, air quality data, and search trend data in an integrated way
- Modularize DB connection and query functions (db_function.py)

**Data analysis (data_analysis/)**
- **Gastroenteritis analysis**: Analyze the correlation between weather variables and gastroenteritis occurrence
- **Food poisoning analysis**: Analyze the correlation between diurnal temperature range and food-poisoning-related infectious diseases
- **Frostbite analysis**: Analyze frostbite occurrence patterns in low-temperature environments
- **Correlation analysis**: Comprehensive analysis of the relationship between various weather variables and disease occurrence

---

**Key Reference Links**

- [KMA Weather Data Portal](https://data.kma.go.kr/)
- [AirKorea Air Quality Information](https://www.airkorea.or.kr/)
- [Naver DataLab](https://datalab.naver.com/)
- [Health and Medical Big Data Open System](https://www.data.go.kr/)

---

## Results and Materials



### 1. Gastroenteritis Analysis Results

<img width="1600" height="637" alt="1-1 Gastroenteritis patient count vs search trend analysis" src="https://github.com/user-attachments/assets/9b4eed84-c5e7-473e-a8a5-07df32e9ab24" name="trend_chart"/>

#### Correlation between search trends and actual patient counts
- The pattern of change in **Naver search trends** closely matches the actual change in gastroenteritis patient counts
  - The timing of rises and falls coincide, confirming its potential as a predictive indicator
- **Google search trends** also show a similar pattern to patient counts, though somewhat less consistent than Naver
- This validates the feasibility of an early-warning system based on search trend data

<br/><br/><br/>

#### Correlation between weather variables and gastroenteritis occurrence

<img width="1477" height="1600" alt="3-1 Correlation between weather data and gastroenteritis patients" src="https://github.com/user-attachments/assets/06abce50-732d-44b2-a35c-a5a610a28f58" />

<img width="1600" height="638" alt="3-2 Weather data and gastroenteritis patients" src="https://github.com/user-attachments/assets/053d2930-5f72-4bf7-a9f7-33ff3c18158a" />

- **Diurnal temperature range (-0.66)**: A negative correlation — patient counts increase as the diurnal range narrows
- **Minimum humidity (0.50)**: A positive correlation — patient counts increase as minimum humidity rises
- A surge in patient counts is observed when temperature and humidity **reach extreme (inflection) points**
- Both the hot, humid summer environment and winter environmental changes affect gastroenteritis occurrence

<br/><br/><br/>

#### Gastroenteritis occurrence pattern by age group

<img width="1600" height="635" alt="2-2 Patient analysis by age group" src="https://github.com/user-attachments/assets/16627e84-49b1-4141-ae32-4af2cfce32ad" />

- Gastroenteritis patient counts are overwhelmingly high in the **0–9 age group**
- Occurrence rate tends to decrease as age increases
- **January 2024**: Highest patient count in the last 5 years (708,131)
- **March 2020**: Lowest patient count in the last 5 years (287,005, presumably due to COVID-19)
- By season, patient counts rise sharply in **summer (July–August)** and **winter (January)**

<br/><br/><br/>

### 2. Food-Poisoning-Related Infectious Disease Analysis

#### Correlation between Naver trends and patient counts

<img alt="1-2 Gastroenteritis patient count vs Naver search trend" src="https://github.com/user-attachments/assets/c22c2811-1040-4e06-afeb-3dde54a6daf9" />

- Food poisoning search trends show a seasonal pattern similar to actual patient counts
- Both search volume and patient counts spike simultaneously in summer (June–August)

<br/><br/><br/>

#### Correlation with diurnal temperature range

<img alt="3-4 Gastroenteritis diurnal range" src="https://github.com/user-attachments/assets/4f37baac-5724-4cea-8f6e-10edd5573673" />

- Analyzed the pattern between diurnal temperature range and food poisoning occurrence based on Seoul-region data
- Patient counts tend to rise in **spring (April–May)** and autumn, when the diurnal range is large
- In summer, patient counts rise due to high temperatures even when the diurnal range is small

<br/><br/><br/>

### 3. Conclusion

- Children aged 0–9 are the most vulnerable to gastroenteritis
- Weather variables (diurnal range, humidity, etc.) have a meaningful effect on disease occurrence
- Naver search trends are better suited than Google's for predicting domestic disease occurrence


---

### 4. Forecast and Proposal

#### HealthCasting Alert System

1. **Early warning based on search trends**
   - Monitor Naver search trends in real time to predict disease outbreaks one month in advance
   - Issue a public health advisory when a specific threshold is exceeded

2. **Risk assessment based on weather conditions**
   - Calculate disease occurrence risk using weather variables such as diurnal range and humidity
   - An early-warning system linked with KMA forecast data

3. **Age-tailored alerts**
   - Focused management of gastroenteritis for the 0–9 age group
   - Differentiated alerts for diseases that specific age groups are vulnerable to

4. **2025 Outlook**
   - Based on historical data pattern analysis, a gastroenteritis resurgence is likely in January 2025
   - Preparation needed for gastroenteritis and food poisoning in summer (July–August)
   - Potential for a public health campaign tied to Health Day (April 7) events
