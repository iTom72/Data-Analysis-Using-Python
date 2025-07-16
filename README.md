# The Analysis

### 1. What are the most demanded skills for the top 3 most popular Data Jobs?
to find the most demanded skills for the top 3 popular data roles, i first filtered out those positions by which ones were the most popular, and then i got the top 5 skills for each one of the top 3 roles, this query highlights the most popular job titles in data roles with thier associated top skills, showing which skills to pay attention to depending on the role i'm prefering more

 View my notebook with detailed steps here:
 [2_Skills_Count.ipynb](2_Skills_Count.ipynb)

### Visualize Data

```python
fig, ax = plt.subplots(len(top_3_jobs), 1)

for i, job_title in enumerate(top_3_jobs):
    csv_plot = csv_skills_perc[csv_skills_perc['job_title_short'] == job_title].head(5)
    sns.barplot(
        data=csv_plot,
        x='skills_percentage',
        y='job_skills',
        ax=ax[i],
        hue='skills_percentage',
        palette='flare',
        legend=False,
    )
```

### Results
![Visulaization of Top Skills for Data Roles](Images/skill_demand_all_data_roles.png)

### Insights

- Python is highly sought after in Data Science and Data Engineering roles, appearing in 72% of Data Science job postings and 65% of Data Engineering job postings.
- sql is highly requested in both Data Analyst and Data Engineering roles with over half of job postings.
- Data Engineering require more  specialized technical skills (aws, azure, spark) unlike Data Analyst and Data Science roles who are requiering more general data analyst and management rools such as Excel and Tableau.

## 2. How are in-demand skills trending for Data Analyst in the US?

### Visualize Data

```python
csv_plot = csv_DA_perc.copy()
ax = sns.lineplot(data=csv_plot, dashes=False, palette='tab10')
ax.yaxis.set_major_formatter(FuncFormatter(lambda x, _: f'{int(x)}%'))
plt.title('Trending Top 5 Data Analyst Skills in the US')
plt.xlabel('2023')
plt.ylabel('Likelihood in Jos Postings')
sns.despine()
plt.legend().remove()

for i in range(5):
    if i == 2:
        plt.text(11.1, csv_plot.iloc[-1, i], csv_plot.columns[i], color='green')
    elif i == 3:
         plt.text(11.1, csv_plot.iloc[-1, i]+1.6, csv_plot.columns[i], va='bottom', ha='left', color='red')
    else:
        plt.text(11.1, csv_plot.iloc[-1, i], csv_plot.columns[i])
        

plt.tight_layout()
plt.show()
```

### Results:
![Trending skills for DA in US](Images/trending_for_data_analyst_skills.png)

### Insights:
- SQl remains the most demanded skill throughout the year.
- Excel is significantly increas in demand by the end of the year, same for Python.
- Both Python and Tableau show relative demand thoughout the year.