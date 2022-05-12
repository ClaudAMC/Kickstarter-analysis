# Kickstarter-analysis with Excel
### Performing analysis on Kickstarter data to uncover trends
---
## Overview of Project
A playwright, Louise, is funding her play "Fever" via a crowdfunding campaign. Her play got close to her fundraising goal and would now like some insight into how other campaigns fared based on two factors: the campaign launch date and the campaign goals.
### Purpose
The purpose of this project was to help Louise find out how different campaigns faired with respect to when they launched and what their funding goals were.

## Analysis and Challenges
The file and any subsequent analysis can be found in the file below.

[Kickstarter_Challenge.xlsx](https://github.com/ClaudAMC/Kickstarter-analysis/files/8648221/Kickstarter_Challenge.xlsx)

### Analysis of Outcomes Based on Launch Date
To better visualize the outcomes of crowdfunded campaigns with respect to when the campaigns launched I first extracted the year of launch from the "Date Created Conversion" column using the YEAR() function. This column had been previously generated by converting the Unix timestamp to a date in the (yyyy-mm-dd) format. 
The Image below shows the function used and the column created.

![YEAR ( )](https://user-images.githubusercontent.com/103139895/167700774-30101f0f-9235-463e-822a-f4083b3f8119.png)

Next a pivot table using the Kickstarter worksheet was created. This pivot table was generated in a new worksheet called "Theater Outcomes by Launch Date". The Outcomes field was displayed in both the columns area and the values are to get the Count of outcomes. Next the Parent Category and the Years column were used in the filters area. Finally, the Date Created Conversion column was used in the rows area; this field when placed here gets split into three different fields: Date Created Conversion, Years, and Quarters - the only field that is kept is the Date Created Conversion field. The Outcome column labels are then filtered to only show the cancelled, failed, and successful outcomes. The pivot table at this stage can be viewed in the image below.

![Pivot Table 1 - Outcomes by Launch Date](https://user-images.githubusercontent.com/103139895/167702947-c5f0be37-e3e9-4a7e-9c8d-aaade537e256.png)

Following this I focused on theater campaigns by filtering the Parent Category to only show theater campaigns and resorted the outcome data in descending order to show the successful campaigns first. This can be viewed in the image of the pivot table below.

![Pivot Table 2 - Theater Outcomes by Launch Date](https://user-images.githubusercontent.com/103139895/167703818-c8abfb22-8025-4324-a9b8-756a05e1a31c.png)

Finally, to visualize this data I created a line chart from the pivot table. This line chart is better able to show us the relationship between outcome and launch months.

![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/103139895/167704507-f981e384-fa20-4fe6-9268-fa2493a6aea1.png)

### Analysis of Outcomes Based on Goals
To find out how campaigns faired based on their goals I looked at the percentage of failed, successful, and cancelled campaigns across different goal ranges. To do this I created a new worksheet titled "Outcomes Based on Goals" where I created a table with the following headings (columns): 
- Goal
- Number Successful
- Number Failed
- Number Canceled
- Total Projects
- Percentage Successful
- Percentage Failed
- Percentage Canceled

The "Goal" column dollar ranges are:

![Goal Ranges](https://user-images.githubusercontent.com/103139895/167726514-ef36847d-cb01-4d19-84ef-d17785c26124.png)

Using these ranges and the function COUNTIFS() I populated the Number Successful, Failed, and Canceled columns. The exact function used for cell B2 under the Number Successful column was: =COUNTIFS(Kickstarter!$F:$F,"successful",Kickstarter!$D:$D,"<1000",Kickstarter!$R:$R,"plays").
Using this function I specified the desired outcome, and the desired goal amount within the subcategory of "plays". This would then give me a count of all the campaigns that matched these parameters.

![COUNTIFS ( ) - Results](https://user-images.githubusercontent.com/103139895/167727524-a16887d6-8190-483a-a8ec-422b2c3a251c.png)

Next I summed the amounts of those counted columns in the "Total Projects" column using the SUM() function (e.g SUM(B2:D2)).
Next, to calculate the percentage of Successful, Failed, and Canceled projects I divided the Number of successful campaigns to the Total Projects corresponding cell. I then formatted that column to present Percentage values from decimals numbers. For example, the formula I used in cell F2 is =B2/$E2; This way the Column I and dividing remains the same "Total Projects" but the cell I divide is shifted to populate the cells around it.

![Outcomes v Goals Table](https://user-images.githubusercontent.com/103139895/167729741-35e8a233-cc60-42d1-a9f8-24fe699047c7.png)

Finally, using this percentage data and table I created a line chart. This way I can follow the trend of campaign outcomes by the fundraising goal they had.

![Outcomes_vs_Goal](https://user-images.githubusercontent.com/103139895/167728771-ce5bc308-f3c8-442c-9659-218ab926a356.png)

### Challenges and Difficulties Encountered

The main challenges I encountered were withe the Outcomes Based on Goals worksheet. When I originally created my COUNTIF() function statement I did not lock the column I was referring to using the $ notation. This meant when I tried to populate the other columns they shifted along with the population. I was trying to save time by doing this but instead created more work for myself. This happened to me again with the percentage calculation where I did not initially add the $ before the denominator's column for the referred cell. This meant when I tried populating the columns to the right the denominator no longer referred to the "Total Project" column but instead the column to its right. Lastly, when I generated the line chart the y values were all in decimals since I had not multiplied my initial calculation by 100. To fix this I changed the y-axis properties to show values of decimals as percentages - this was able to correct the y-axis values to show desired units.

## Results

### Conclusions about the Outcomes based on Launch Date

1) One conclusion we can draw from the Theater Outcomes by Launch Date analysis is that there were more successful campaigns launched in the month of May than in any other month; there were more successful campaigns than both failed and canceled campaigns combined.
From this we can conclude that campaigns launch in May could be more successful than campaigns launched in any other months.

2) A second conclusion that we could draw is that December is the worst month to launch a campaign. During this month there were almost an equal amount of successful and failed campaigns. This could mean a campaign launched in December may be as likely to succeed as it is to fail.

### Conclusion about the Outcomes based on Goals

1) One conclusion we can draw from the analysis of the outcomes based on campaign goals is that the general trend shows that as the goal increases the campaign is more likely to fail. The most successful campaigns have a goal under $1000 and as the goals increase there is a decrease in the percentage of successful campaigns. Similarly, the percentage of campaigns that failed is lower for those with a goal under $1000, that percentage increases as the goal increases. Therefore, lower campaigns goals may lead to a more successful campaign.

### Limitations of this Dataset

A limitation of this study is that when looking at the "outcomes based on campaign goals" data it is skewed toward the lower goals - there are more campaigns that had lower goals (<15000). This means we have very few data points to look at and compare for campaigns that had higher goals. Ideally, we would have many data points for each goal grouping this way we can more accurately compare the campaign outcomes. Also according to this data no play campaigns were ever canceled. 
Another limitation of this dataset is that the currency is not standardized; this means the goal grouping may be misleading if Louise is assuming all monetary amounts are in USD - some of these campaigns may have been in GBP or CAD where if converted to USD the goal grouping could change. Without having done this conversion there is no way of having full certainty that our groupings are correct with regard to USD currency values.

### Other possible tables and/or graphs that we could create

Another table that could have been created was one depicting the outcomes based on the average donation and the number of backers for the subcategory of plays. This way we could see if changes in the average donation for the number of backers a campaign had could affect he success or failure of a campaign. Further breaking this information down by the goal grouping we created above could narrow down if donations were on average higher for lower goals or if they had more backers - perhaps having a lower goal leads to more backers or backers willing to give higher donations. It is possible this will also show us that there is no correlation between goal amount and average donations or number of backers.

Finally, we could also look at location/ country where the campaigns are run - we can see if location has an impact on how successful a campaigns is. From this we can see where Louise's play would be more likely to run a successful fundraising campaign.

