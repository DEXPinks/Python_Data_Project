# The Analysis

## 1. What are the most demanded skills for the top 3 most popular roles in data?

In order to find the most demanded skills for the top 3 most popular roles in data, I filtered out the top positions by which ones had the most job postings, then sorted each of those by skills and kept the top 5 for the top 3 most popular positions. This highlights the the most popular job roles, along with their most required skillset. This information can then be used to determine what someone should try to learn based on what job role suits them.

View my notebook with detailed steps here:
[2_Skills_Count.ipynb](3_project\2_Skills_Count.ipynb)

### Visualized Data

```python
for i, job in enumerate(job_title):
    df_plot = df_skills_perc[df_skills_perc['job_title_short']==job].head(5)
    sns.barplot(data=df_plot, x='percent', y='job_skills', hue='percent', palette = 'dark:b_r', ax=ax[i], legend=False)

plt.show()
```

### Results
![Visualization of Top Skills for Top 3 Data Positions](3_project\Images\skill_demand_data_roles.png)

### Insights

- SQL is the most required skill amongst the top 3 most popular positions in our dataset, with it being the most required for Data Analyst and Data Engineer. This shows that if someone wants to get into any of these fields, it is strongly suggested to learn SQL
- Python is also a very highly requested skill to have, especially for Data Scientists where 72% of job postings require it as a skill to have.
- Data Engineers require more specialized skills such as cloud computing platform experience (AWS, Azure, Spark). This is in comparison to both Data Analyst and Data Scientist that require more data analysis tools.


# The Analysis

## 2. How are in-demand skills trending for Data Analyst?

## Visualized Data

```python
df_plot = df_DA_US_percent.iloc[:, :5]
sns.lineplot(data=df_plot, dashes = False, palette='tab10', legend=False)

texts = []
for i in range(5):
    texts.append(plt.text(11.2, df_plot.iloc[-1, i ], df_plot.columns[i]))

ax = plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter(decimals=0))

plt.show()
```

## Results

![Trending Top Skills for Data Analyst in the US](3_project\Images\top_skills_for_data_analyst.png)
*Bar graph visualizing the trend of the top 5 skills for data analyst in the US in 2023.*

## Insights

- Throughout the entire year, SQL remained as the most demanded skill for data analyst postitions, hovering around the 60% mark. Despite the slight decrease in demand throughout the year, it still remains as the most demanded skill by a large margin.
- Python has experienced a large spike in demand in the monthos of October through December in addition to being stable throughout the year. Python, Tableau, and Excel remain as essential skills with no large fluctuations in the graph.
- Despite Power BI's relatively low demand in comparison to the other skills, it also does not fluctuate much, however there is a slight upward trend towards the end of the year possibly indicating the need for it in the future.


# The Analysis

## 3. How well do jobs and skills pay for Data Analysts?

## Visualized Data
```python
sns.boxplot(data=df_US_top, x='salary_year_avg', y='job_title_short', order= df_order)
ax = plt.gca()
ax.xaxis.set_major_formatter(plt.FuncFormatter(lambda x,_: f'${int(x/1000)}K'))
plt.show()
```
## Results

![Salary Distribution of Top 6 Data Jobs in the US](3_project\Images\salary_ranges_for_top_roles.png)
*Box plot showing the top 6 most popular data roles and their salary distribution*

## Insights

- The senior data positions tend to pay significantly higher than their normal positions, highlighting a clear promotional path. The only exception is senior data analyst where if you are a data analyst, it might be worth trying to become a data engineer or data scientist rather than a senior data analyst.
- For both data scientist roles, there are significantly more outliers with greater variances in their box plots. This indicates that in this field, there may be a a higher potential to earn more money in these rare cases and can be something to take into consideration.
- The variances for data scientist also apply to the low end as well. The lower pay for data scientist tends to be similar to the lower end pay for data analyst.

# The Analysis

## 4. What are the most optimal skills to learn for Data Analysts?

### Visualized Data

```python
sns.scatterplot(data=df_plot,
                x='skill_percent',
                y='median_salary',
                hue='technology' )
```

## Results

![Most Optimal Skills for Data Analyst in the US](3_project\Images\optimal_skills.png)

## Insights

- The scatter plot shows that most of the skills categorized as "programming" skills are at the higher end of the median yearly salary, indicating that programming knwoledge is likely to offer a higher salary for data analysts.
- Analyst tools are also highly prevalent in job postings, however they tend to offer lower salaries. Their prevalence however indicates how important these skills can be to data analyst, as they are very commonly found in job postings.
- Database and cloud skills, such as Oracle and SQL server, are not as frequently found. Despite this, they are amongst the highest paying skills for data analysts. This indicates a desire for these high skill jobs and a potential higher salary for jobs that require these skills.