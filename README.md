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
Python and SQL are a versatile skills, highly demanded across all three roles, so I would recommend to start learning it :)