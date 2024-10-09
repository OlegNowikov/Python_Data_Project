# The Analysis
## 1. What are the most demanded skills for the top 3 most popular data roles?
To find the most demanded skills for the top 3 most popular data roles in Baltics and Poland. I filtered out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills I should pay attention to depending on the role I'm targeting.
View my notebook with detailed steps here:
[2_Skill_Demand.ipynb](https://github.com/OlegNowikov/Python_Data_Project/blob/main/3_Project/2_Skill_Demand.ipynb)
### Visualize Data
```Python
fig, ax = plt.subplots(len(job_titles), 1)
for i, job_title in enumerate(job_titles):
    df_plot = df_skills_count[df_skills_count['job_title_short']==job_title].head(5)
    df_plot.plot(kind='barh',x='job_skills', y='skill_count', ax=ax[i], title=job_title)
    ax[i].invert_yaxis()
    ax[i].set_ylabel('')
    ax[i].legend().set_visible(False)
fig.suptitle('Counts of Top Skills in Job Postings', fontsize = 14)
fig.tight_layout(h_pad=0.5)
plt.show()
```
### Results

![Visualization of Top Skills for Data roles](3_Project\Images\bp_skill_demand_all_roles.png)

### Insights
-Python and SQL are a versatile skills, highly demanded across all three roles, so I would recommend to start learning it :)

## 2. How are in-demand skills trending for Data Analysts in Baltics and Poland?
```python

from matplotlib.ticker import PercentFormatter
df_plot = df_DA_PLBAL_prc.iloc[:,:5]
sns.lineplot(data=df_plot, dashes=False, palette='tab10')
ax = plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter(decimals=0))
for i in range(5):
    plt.text(11.2, df_plot.iloc[-1, i], df_plot.columns[i])
plt.show()

```
### Results

![Trending Top Skills for Data Analysts in the Baltics and Poland](3_Project\Images\Skills_in_demand_2023.png)
*Graph visualizing the trending top skills for data analyst in the Baltics and Poland in 2023.*

### Insights

- SQL remains the most consistently demanded skill throughout the year and shows a gradual increase in demand.
- Excel and Power Bi show relatively stable demand throughout the year, shows upward trend towards the year's end.

## 3. How well do jobs and skills pay for Data Analysts?
### Salary Analysis for Data jobs
```Python
sns.boxplot(data=df_PLBAL_top6, x='salary_year_avg', y='job_title_short', order=job_order)
ticks_x = plt.FuncFormatter(lambda x, position: f'€{int(x/1100)}K')
plt.gca().xaxis.set_major_formatter(ticks_x)
plt.show()

```
![Salary Distributions of Data Jobs in the Baltics and Poland](3_Project\Images\Salary_by_job.png)*Box plot visualizing the salary distributions for the top 6 data job titles.*

#### Insights
- Top 3 (Senior Data Scientis, Data Engineer, Data Scientist) jobs have almost the same interquartile range for salary.
- For top 3 jobs salary is more than 50% bigger than Data Analyst.

### Highest Paid & Most Demanded Skills for Data Analysts
```Python

fig, ax = plt.subplots(2 , 1)
# Top 10 Highest Paid Skills for Data Analysts
sns.barplot(data=df_DA_top_pay, x='median', y=df_DA_top_pay.index, ax=ax[0], hue='median', palette='dark:b_r', legend=False)
# Top 10 Most In-Demand Skills for Data Analysts
sns.barplot(data=df_DA_top_skills, x='median', y=df_DA_top_skills.index, ax=ax[1], hue='median', palette='light:b', legend=False)
plt.show()


```
#### Insights
- The top graph shows specialized technical skills like 'mongo', 'aws', 'hadoop' are associated with higher salaries, suggesting that advanced technical proficiency can increase earning potential.
- The bottom graph shows that foundational skills like 'SQL', 'Power Bi', 'Excel', 'Python' are the most In-Demand, even though they may not offer the highest salaries. This demonstrates tre importance of core skills in data analysis roles.