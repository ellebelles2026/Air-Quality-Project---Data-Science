# Air-Quality-Project---Data-Science

# **Hacking Hooters: Seasonal Variations in Urban Air Pollution: An Analysis of Air Quality Data**
###      **Investigating the Relationship Between Seasonal Changes, Nitrogen Oxides, and Other Air Pollutants.**

**Group members:** Ella S., Vy H., Amy N, Jayden M., Ibodat S., & Bahiyah W

- Seasonal variations: Changes in air quality across different seasons.
- Air pollution: The concentration and relationships of different air pollutants.




### Team Roles
| Member | Role | Responsibilities |
|---|---|---|
| Ella S | Visualizer | Designs and creates graphs, charts, dashboards, and visual layouts to clearly present data and findings |
| Vy H | Context Expert | Researches the background, domain knowledge, and real-world relevance to explain why the project matters and what the data signifies |
| Amy N | Project Manager | Schedules meetings, tracks deadlines and progress, organizes the team's workflow, and leads presentations |
| Jayden M | Coder 1 | Writes, tests, and executes the programming code required to clean, process, or model the data |
| Ibodat S | Writer | Drafts, edits, and finalizes the written reports, summaries, documentation, and abstracts |
| Bahiyah W | Analyst | Examines the data, runs statistical tests or data models, and interprets the findings to draw logical conclusions |

Everyone makes the visualizations for their own part and reviews the whole notebook before submission.






You are probably all familiar with urban air pollution concerns, especially during colder months. What you may not know is that comprehensive air quality data for Italian cities from 2004–2005 is available for public analysis.

In this project, we will:
* Explore air quality and meteorological data for Italian urban monitoring stations spanning 2004–2005
* Make data visualizations
* Formulate a hypothesis
* Test the hypothesis using simulation

<h1 style="color: #dc2626;">Introduction to the Dataset</h1>

***The Air Quality dataset** is publicly available through the UCI Machine Learning Repository.* <br> 

It contains measurements collected using a chemical multisensor device installed near road level in a significantly polluted urban area in Italy. 

<h2 style="color: #16a34a;">Dataset Information</h2>

| Category | Information |
|---|---|
| Dataset Name | Air Quality |
| Data Source | UCI Machine Learning Repository |
| Location | Urban area in Italy |
| Collection Period | March 2004 – February 2005 |
| Number of Observations | 9,358 |
| Frequency | Hourly measurements |
| Environment | Urban area significantly affected by air pollution |
| Main Purpose | Monitoring air pollution and environmental conditions |

<h2 style="color: #16a34a;">Dataset Variables</h2>

| Variable | Description | Unit |
|---|---|---|
| Date | Date of measurement | Date |
| Time | Time of measurement | Time |
| CO(GT) | Carbon monoxide concentration | mg/m³ |
| NMHC(GT) | Non-methane hydrocarbons concentration | µg/m³ |
| C6H6(GT) | Benzene concentration | µg/m³ |
| NOx(GT) | Nitrogen oxides concentration | ppb |
| NO2(GT) | Nitrogen dioxide concentration | µg/m³ |
| T | Temperature | °C |
| RH | Relative humidity | % |
| AH | Absolute humidity | — |
| PT08.S1–PT08.S5 | Responses from five chemical sensors | Sensor readings |

<h2 style="color: #16a34a;">Variable of Interest</h2>

| Variable | Description |
|---|---|
| NOx(GT) | Nitrogen oxides concentration |
| Unit | Parts per billion (ppb) |
| Summer | June – August |
| Winter | December – February |
| Research Goal | Compare average NOx concentrations between summer and winter |

<h1 style="color: #dc2626;">Background Research</h1>
<h2 style="color: #16a34a;">What Is NOx?</h2>

NOx stands for **nitrogen oxides**, a group of reactive gases primarily consisting of:
- *Nitric oxide (NO).*
- *Nitrogen dioxide (NO2).*

These pollutants are mainly produced through fuel combustion, including emissions from motor vehicles, power plants, and industrial activities.

NOx is important because it contributes to atmospheric chemical reactions and the formation of other pollutants, including ground-level ozone and fine particulate matter.

According to the U.S. Environmental Protection Agency (EPA), exposure to nitrogen oxides is associated with adverse respiratory health effects.

Therefore, studying NOx concentrations is important for understanding urban air pollution and its potential environmental and health impacts.
<h2 style="color: #16a34a;">How Do Seasons Affect Air Pollution?</h2>

Seasonal changes can **influence the concentration of air pollutants in the atmosphere**.

During winter, NOx concentrations may increase due to several environmental and human-related factors.

**For example**:

1. *Reduced sunlight*: Lower solar radiation during winter can reduce photochemical reactions that transform NO2 in the atmosphere.
2. *Atmospheric conditions*: Changes in atmospheric mixing and boundary layer height can influence how easily pollutants disperse.
3. *Human activities*: Traffic and fuel combustion contribute to nitrogen oxide emissions throughout the year. 

During summer, stronger sunlight and increased photochemical activity can influence the transformation of nitrogen oxides and their atmospheric concentrations.

However, seasonal patterns are not necessarily identical across different cities because local emissions, weather conditions, and geographical characteristics also matter.
<h2 style="color: #16a34a;">Previous Scientific Research</h2>

**Voiculescu et al. (2020).**

**Title:** *Role of Meteorological Parameters in the Diurnal and Seasonal Variation of NO2 in a Romanian Urban Environment.*

The researchers investigated seasonal and daily variations in nitrogen dioxide concentrations in an urban environment in Braila, Romania.

Their study analyzed air quality measurements collected between 2009 and 2014.

**Important findings:**

- NO2 concentrations were generally higher during winter.
- Summer generally showed lower NO2 concentrations.
- Traffic contributed significantly to urban NO2 pollution.
- Seasonal meteorological conditions influenced pollutant concentrations and dispersion.

The researchers suggested that reduced photochemical activity during winter and seasonal atmospheric conditions could contribute to higher winter NO2 concentrations.

These findings provide scientific background for investigating whether NOx concentrations differ between summer and winter in our dataset.

An important distinction is that this previous study investigated NO2, whereas our project investigates total NOx. Therefore, its findings provide supporting background rather than direct proof of our hypothesis.

<h1 style="color: #dc2626;">Research Question and Hypothesis</h1>

<h2 style="color: #16a34a;">Research Question</h2>

**Does the average NOx concentration differ significantly between summer and winter?** 

<h2 style="color: #16a34a;">Variables</h2>

| Variable | Description |
|---|---|
| Independent variable | Season (Summer / Winter) |
| Dependent variable | NOx concentration |
| Measurement unit | Parts per billion (ppb) |
| Population of interest | NOx concentrations during summer and winter in the study period |

<h2 style="color: #16a34a;">Hypotheses</h2>

**Null Hypothesis (H₀):**
There is no significant difference in average NOx concentrations between summer and winter.

$$
H_0: \mu_{\text{summer}} = \mu_{\text{winter}}
$$

**Alternative Hypothesis (H₁):**
There is a significant difference in average NOx concentrations between summer and winter.

$$
H_1:\mu_{\text{summer}} = mu_{\text{winter}}
$$

<h2 style="color: #16a34a;">Expected Outcome</h2>

Based on previous scientific research, we expect that **winter may have higher NOx concentrations than summer**.

However, this is an expectation based on previous research, not a confirmed result from our dataset.

<h1 style="color: #dc2626;">Analysis Plan</h1>

<h2 style="color: #16a34a;">Seasonal Classification</h2>

| Season | Months |
|---|---|
| Spring | March, April, May |
| Summer | June, July, August |
| Fall | September, October, November |
| Winter | December, January, February |

For our statistical analysis, we only compare summer and winter.

<h2 style="color: #16a34a;">Data Cleaning</h2>

**Before analyzing the data, we will:**

1. Load the dataset.
2. Identify missing values.
3. Replace -200 with NaN because -200 represents missing data.
4. Remove unnecessary empty columns.
5. Convert the Date and Time columns into datetime format.
6. Create a season column.

<h2 style="color: #16a34a;">Statistical Unit</h2>

The original dataset contains hourly observations.

However, consecutive hourly measurements may be correlated because air pollution levels can remain similar over short periods.

To reduce the influence of hourly dependence, we will calculate **daily average NOx concentrations**.

Each day will then contribute one observation to the summer or winter group.

*This does not completely eliminate time-series dependence, so we will acknowledge it as a limitation.*

<h2 style="color: #16a34a;">Statistical Test</h2>

We will use: **Welch’s Independent Two-Sample t-test.**

**Why?**

- We are comparing two independent groups: summer and winter.
- We want to compare their average NOx concentrations.
- Welch’s t-test does not require the two groups to have equal variances.

**Significance level:**

$$
\alpha=0.05
$$

**Decision rule:**

- If p-value < 0.05: Reject H₀.
- If p-value ≥ 0.05: Fail to reject H₀.

We will also calculate a 95% confidence interval for the difference in means.
