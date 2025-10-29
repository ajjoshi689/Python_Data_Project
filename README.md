# The Analysis 

## 1. What are the most demanded skills for the top 3 most popular data roles

To find the most demanded skills for the top 3 data roles. I filtered out those positions by which ones where most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills I should pay attention to depending on the rile I'm targeting.

View my notebook with detalied steps here:
[2_Skill_Demand.iypnb](Project/2_Skills_Demand.ipynb)

### Visualize Data

```python
fig, ax= plt.subplots(len(job_titles), 1)

sns.set_theme(style='ticks')

for i, job_title in enumerate(job_titles):
    df_plot=df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)
    sns.barplot(data=df_plot, x= 'skill_percent', y='job_skills', ax=ax[i], hue='skill_count', palette='dark:b_r')
    ax[i].set_title(job_title)
    ax[i].set_ylabel("")
    ax[i].set_xlabel("")
    ax[i].get_legend().remove()
    ax[i].set_xlim(0,78)

    for n, v in enumerate(df_plot['skill_percent']):
        ax[i].text(v + 1, n, f'{v:.0f}%', va='center')

    if i != len(job_titles) -1:
        ax[i].set_xticks([])

fig.suptitle('Likelihood of Skills Requested in Job Positings', fontsize=15)
fig.tight_layout(h_pad=0.5)

### Results
![Visualization of Top Skills](Project\Images\skill_demand_all_data_roles.png)



