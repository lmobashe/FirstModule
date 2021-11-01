# Kickstarting with Excel

## Overview of Project

### Purpose:

Kickstarter campaigns can be a good way to raise money for a project. We want to find out how to run a successful Kickstarter campaign specifically for funding the production of a play. There are many variables that can contribute to the success of a Kickstarter campaign we looked at the dates campaigns were launched and the funding goal amounts. 

## Analysis and Challenges

The Kickstarter data we analyzed showed campaign information from 20 different countries, our analysis was not country specific, so all country data was analyzed together. A Kickstarter where the money pledged was equal to or higher than the goal funding amount is considered "successful"; conversely, a campaign where the money pledged was less than the goal amount is considered "failed". Campaigns that are actively collecting donations are considered "live" and campaigns that were started but canceled before their Conditional formatting was applied to the outcome’s column in our data set for visual emphasis: "successful" was colored green, "failed" was colored red, "canceled" was colored yellow, and "live" was colored blue. For our analysis looking at the success of campaigns based on date and funding goals "live" campaigns were not included; since they have not concluded these campaigns do not offer any insight into the traits of successful campaigns. 

### Analysis of Outcomes Based on Launch Date

The Kickstarter data included the campaigns' creation dates and end dates as a Unix timestamp. To analyze the success of theater campaigns based on launch date, these unix  timestamps needed to be converted into a readable format using the following formula:

````
```
	=(((J4/60)/60)/24+DATE(1970,1,1)
		-J4 refers to the column holding the unix time stamp for the campaign creation date
```
````

After converting the unix timestamp into readable format the data was inserted into a pivot table filtered by parent category, theater. The table shows the count of campaigns by outcome--"successful," "failed," "canceled," and total campaigns--against launch date by month. I included the percentage of campaigns that were successful and failed by launch month.

![Theater_Outcomes_vs_Launch_Pivot_Table](https://github.com/lmobashe/FirstModule/blob/main/Resources/Theater_Outcomes_vs_Launch_Pivot_Table.png)

The pivot table was visualized as a line graph of campaigns over time, campaign outcome on the y-axis and launch date by month on the x-axis. 

![Theater_Outcomes_vs_Launch](https://github.com/lmobashe/FirstModule/blob/main/Resources/Theater_Outcomes_vs_Launch.png)


### Analysis of Outcomes Based on Goals

To analyze the campaign outcomes based on goal funding amounts we first identified goal ranges to group the Kickstarter campaigns for our analysis; the goal ranges were increments of $5,000. We then counted the number of campaigns for each funding range for each outcome using the following formula:

````
```
	=COUNTIFS(Kickstarter!$D:$D,">=*1000*",Kickstarter!$D:$D,"<=*4999*", Kickstarter!$F:$F,"*Outcome*", Kickstarter!$R:$R, "plays")
		-where 1000 refers to the lowest amount per goal range
		-where 4999 refers to the highest amount per goal range
		-Outcome is replaced by "successful", "failed", and "canceled" for the analysis of each outcome group by fund range
		-$D:$D indicates the column that holds the funding goal data
		-$F:$F indicates the column that holds the campaign outcome data
		-$R:R$ indicates the column that holds the campaign subcategory
```
````

The percentage of "successful", "failed", and "canceled" campaigns in subcategory "plays" was then calculated for each funding goal range. 

![Outcomes_vs_Goals_Table](https://github.com/lmobashe/FirstModule/blob/main/Resources/Outcomes_vs_Goals_Table.png)

Our data was then visualized on a line graph of the percentage of successful and failed campaigns (y-axis) across funding goal ranges (x-axis).

![Outcomes_vs_Goals](https://github.com/lmobashe/FirstModule/blob/main/Resources/Outcomes_vs_Goals.png)

### Challenges and Difficulties Encountered

For this analysis outliers were not identified, this could be an additional parameter to explore to verify outliers are not skewing the results. Each campaign included a category/subcategory entry; to look at the data by parent category (e.g. Theater) and subcategory (e.g. plays) separately the data column needs to be segregated into separate data columns using the "convert text to columns wizard" and "Delimited" process.

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

May and June were the highest performing months for theater Kickstarters with 67% and 65%, respectively, successful campaigns. January through July show a success rate of over 50% each month while August through December having a success rate of less than 50%. December is the least successful month for theater Kickstarters with only an 18% success rate.

- What can you conclude about the Outcomes based on Goals?

The funding goal with the highest percentage of successful campaigns are less than $1,000 (75.81% successful) and $1,000 to $4,999 (72.66% successful). The next most successful ranges, $35,000 to $39,999 and $40,000 to $44,999, had a success rate of 66.67$. The least successful funding goals are $45,000 to $49,999 (0% success rate) and campaigns with goals greater than $50,000 (12.5% success rate).

- What are some limitations of this dataset?

Kickstarter campaigns rely heavily on social media outreach for their success. The data provided doesn't provide any data about how these Kickstarters were advertised or which communities their donor base stems from. To have the best understanding of how to run a successful Kickstarter campaign data about advertising would be integral.

- What are some other possible tables and/or graphs that we could create?

It would be interesting to look at length of time campaigns were active in days as a bar chart.