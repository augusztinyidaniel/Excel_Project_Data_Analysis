# Excel Salary Dashboard

![Animated GIF of the Dashboard](..\0_Resources\Images\Excel_Data_Analytics_Salary_Project.gif)

## Introduction

This dashboard was created to take a look into the world of data job postings and aims at helping workers and job seekers investigate salaries for their current or desired jobs and ensure they are being adequately compensated.

The source of the data are the resources given for the Excel for Data Analytics course created by Luke Barousse and Kelly Adams, which provides foundation in analyzing data using Excel. This data contains detailed information on job titles, salaries, locations, and essential skills that are presented here.

## Dashboard File

The finished and full dashboard can be found here: [1_Salary_Dashboard.xlsx](1_Salary_Dashboard.xlsx)

Also, a simplified version (without the map chart) can be accessed and even tried out online here: [Online dashboard](https://onedrive.live.com/:x:/g/personal/196C2966E105EA5F/Ea0estueQqNIk_X3YM_EXF4BmvNji0d8xWzLdvdX5O-c0A?resid=196C2966E105EA5F!sdbb21ead429e48a393f5f760cfc45c5e&ithint=file%2Cxlsx&e=2kdO1f&migratedtospo=true&redeem=aHR0cHM6Ly8xZHJ2Lm1zL3gvYy8xOTZjMjk2NmUxMDVlYTVmL0VhMGVzdHVlUXFOSWtfWDNZTV9FWEY0Qm12TmppMGQ4eFd6TGR2ZFg1Ty1jMEE_ZT0ya2RPMWY)

## Excel Skills Used

The creation of this dashboard required the following skills in Excel:

- Charts
- Formulas and Functions
- Data Validation

## Data Jobs Dataset

The dataset used for this project contains real-world data science job information from 2023. The dataset is available via the Excel for Data Analytics course, which provides a foundation for analyzing data using Excel. It includes detailed information on:

- Job titles
- Salaries
- Locations
- Skills

## Dashboard Elements

### Charts

#### Data Jobs and Schedule Types - Bar Chart

![Bar chart of median yearly salaries by job title](..\0_Resources\Images\salaries_bar_chart.png)

![Bar chart of median yearly salaries by schedule type](..\0_Resources\Images\schedule_type_bar_chart.png)

For the best visual comparison, horizontal bar charts have been used to visualize the median yearly salaries of data jobs broken down by job titles and schedule types.

The data is sorted by descending salary for better readability, the layout has been optimized and the salary values formatted for clarity.

This enables quick identification of salary trends, noting that Senior roles and Engineers are higher-paying than Analyst roles.

#### Country Median Salaries - Map Chart

![Animated GIF of a map chart of median yearly salaries](..\0_Resources\Images\map_chart.gif)

The map chart feature has been chosen to plot median salaries globally. The color-coded map visually differentiates salary levels across regions each country with available data. This provides an easy and immediate understanding of geographic salary trends and highlights high/low salary regions.

### Formulas and Functions

Note: in my analysis I used the Hungarian version of Excel in order for me to get familiar with both the English version (from the course video) and the Hungarian version (in practice) of the functions used.

The functions showcased here are taken from my project in their original form, but in the details I provide the English version of all the functions used.

#### Median Salary by Job Titles

```
=MEDIÁN(
  HA(
    (jobs[job_title_short]=A2)*
    (jobs[salary_year_avg]<>0)*
    (jobs[job_country]=country)*
    (SZÁM(SZÖVEG.KERES(type;jobs[job_schedule_type])));
    jobs[salary_year_avg]
  )
)
```
| Hungarian        | English      |
|------------------|--------------|
| `MEDIÁN()`       | `MEDIAN()`   |
| `SZÁM()`         | `ISNUMBER()` |
| `SZÖVEG.KERES()` | `SEARCH()`   |

- **Multi-Criteria Filtering**: Checks job title, country, schedule type, and excludes blank salaries.

- **Array Formula**: Utilizes `MEDIAN()` function with nested `IF()` function to analyze an array.

- **Tailored Insights**: Provides specific salary information for job titles, regions, and schedule types.

- **Formula Purpose**: This formula populates the table below, returning the median salary based on job title, country, and type specified.

**Background table**

![The table that works behind the horizontal bar chart of median salary by titles and the Median Salary KPI card](..\0_Resources\Images\title_background_table.png)

**Dashboard Implementation**

![The horizontal bar chart of median salary by titles and the Median Salary KPI card](..\0_Resources\Images\title_dashboard.png)

#### Count of Job Schedule Type

```
=SZŰRŐ(J2#;NEM(SZÁM(SZÖVEG.KERES("and";J2#)))*(J2#<>0))
```
| Hungarian        | English      |
|------------------|--------------|
| `SZŰRŐ()`        | `FILTER()`   |
| `NEM()`          | `NOT()`      |
| `SZÁM()`         | `ISNUMBER()` |
| `SZÖVEG.KERES()` | `SEARCH()`   |

- **Unique List Generation**: This Excel formula employs the `FILTER()` function to exclude entries containing "and" or commas, and omit zero values.

- **Formula Purpose**: This formula populates the table below, which gives us a list of unique job schedule types.

**Background table**

![The table that works behind the horizontal bar chart of median salary by schedule types and the Job Count KPI card](..\0_Resources\Images\type_background_table.png)

**Dashboard Implementation**

![The horizontal bar chart of median salary by schedule types and the Job Count KPI card](..\0_Resources\Images\type_dashboard.png)

### Data Validation

#### Filtered List

- Enhanced Data Validation: Implementing the filtered list as a data validation rule under the Job Title, Country, and Type option in the Data tab ensures:

  - User input is restricted to predefined, validated schedule types
  - Incorrect or inconsistent entries are prevented
  - Overall usability of the dashboard is enhanced

## Conclusion

I created this dashboard to showcase my skills in the use of Excel as a tool for data analysis and to take a look into salary trends across various data-related job titles and to understand how location and job type influence salaries. Utilizing data from the Excel for Data Analytics course, this dashboard may assist its users to make more informed decisions about their career paths.