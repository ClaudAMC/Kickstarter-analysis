# Kickstarter-analysis with Excel
Performing analysis on Kickstarter data to uncover trends
---
## Overview of Project
A playwright, Louise, is funding her play "Fever" via a crowdfunding campaign. Her play got close to her fundrasing goal and would now like some insight into how other campaigns fared based on two factors: the campaign launch date and the campaign goals.
### Purpose
The purpose of this project was to help Louise find out how different campaigns faired with respect to when they launched and what their funding goals were.

## Analysis and Challenges
The file and any subsequent analysis can be found in the file below.

[Kickstarter_Challenge.xlsx](https://github.com/ClaudAMC/Kickstarter-analysis/files/8648221/Kickstarter_Challenge.xlsx)

### Analysis of Outcomes Based on Launch Date
To better visualize the outcomes of crowdfunded campaigns with respect to when the campaigns launched I first extracted the year of launch from the "Date Created Conversion" column using the YEAR() function. This column had been previosuly generated by converting the unix timestamp to a date in the (yyyy-mm-dd) format. 
The Image below shows the function used and the column created.

![YEAR ( )](https://user-images.githubusercontent.com/103139895/167700774-30101f0f-9235-463e-822a-f4083b3f8119.png)

Next a pivot table using the Kickstarter worksheet was created. This pivot table was generated in a new worksheet called "Theater Outcomes by Launch Date". The Outcomes field was displayed in both the columns area and the values are to get the Count of outcomes. Next the Parent Category and the Years column were used in the filters area. Finally, the Date Created Conversion column was used in the rows area; this field when placed here gets plit into three different fields: Date Created Conversion, Years, and Quarters - the only field that is kept is the Date Created Conversion field. The Outcome column labels are then filtered to only show the cancelled, failed, and successful outcomes. The pivot table at this stage can be viewed in the image below.

![Pivot Table 1 - Outcomes by Launch Date](https://user-images.githubusercontent.com/103139895/167702947-c5f0be37-e3e9-4a7e-9c8d-aaade537e256.png)

Following this I focused on theater campaigns by filtering the Parent Category to only show theater campaigns and resorted the outcome data in descending order to show the successful campaigns first. This can be viewed in the image of the pivot table below.

![Pivot Table 2 - Theater Outcomes by Launch Date](https://user-images.githubusercontent.com/103139895/167703818-c8abfb22-8025-4324-a9b8-756a05e1a31c.png)

Finally to visualize this data I created a line chart from the pivot table. This line chart is better able to show us the relationship between outcome and launch months.

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

Using these ranges and the function COUNTIFS() I populated the Number Successful, Failed, and Canceled columns. The excat function used for cell B2 under the Number Successful column was: =COUNTIFS(Kickstarter!$F:$F,"successful",Kickstarter!$D:$D,"<1000",Kickstarter!$R:$R,"plays").
Using this function I specified the desired outcome, and the desired goal amount within the subcatagory of "plays". This would then give me a count of all the campaigns that matched these parameters.

![COUNTIFS ( ) - Results](https://user-images.githubusercontent.com/103139895/167727524-a16887d6-8190-483a-a8ec-422b2c3a251c.png)

Next I summed the amounts of those counted columns in the "Total Projects" column using the SUM() function (e.g SUM(B2:D2)).
Next, to calculate the percentage of Successful, Failed, and Canceled projects I divided the Number of successful campaigns to the Total Projects corresponding cell. I then formatted that column to present Percentage values from decimals numbers. For example the formula I used in cell F2 is =B2/$E2; This way the Column I and dividing remains the same "Total Projects" but the cell I divide is shifted to populate the cells around it.

Finally, using this percentage data and table I created a line chart. This way I can follow the trend of campaign outcomes by the fundraising goal they had.

![Outcomes_vs_Goal](https://user-images.githubusercontent.com/103139895/167728771-ce5bc308-f3c8-442c-9659-218ab926a356.png)

### Challenges and Difficulties Encountered

The main challenges I encountered were withe the Outcomes Based on Goals worksheet. When I orginonally created my COUNTIF() function statement I did not lock the column I was referring to using the $ notation. This meant when I tried to populate the other columns they shifted along with the population. I was trying to save time by doing this but instead created more work for myself. This happened to me again with the percetage calculation where I did not intially add the $ before the denominators column for the referred cell. This meant when I tried populating the collumns to the right the denominator no longer referred to the "Total Project" column but instead the column to its right. Lastly, when I generated the line chart the y values were all in decimals since I had not multiplied my intial calculation by 100. To fix this I changes the y-axis properties to show values of decimals as percentages - this was able to correct the y-axis values to show desired units.

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

- What can you conclude about the Outcomes based on Goals?

- What are some limitations of this dataset?

- What are some other possible tables and/or graphs that we could create?
