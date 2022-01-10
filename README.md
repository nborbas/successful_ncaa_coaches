# Back To Viz Basics (#B2VB) community project - Week 1, 2022

A brand new Tableau community project was introduced at the end of last year.
The [B2VB](https://www.thetableaustudentguide.com/vizbasics) team is handing out simple data sources each week which are waiting for to be visualized using easy-to-understand charts and diagrams.

This is my attempt for the first week:
![visualization](https://user-images.githubusercontent.com/96722899/148657605-f5f37484-ee03-4c5a-a965-b5132e6afaa1.png)


Find the interactive on my [Tableau Public profile](https://public.tableau.com/app/profile/norbert.borb.s/viz/B2VB_Week1/NCAA?publish=yes) with a downloadable workbook.

## Idea

The motto for Week 1 is:
> Build a Scatter Plot

I wanted to create something simple, with visualizing the **Wins** and **Losses** for each coach and creating some kind of grouping based on their **Win Percentage**.  

So here is the "process" I took:
- I decided making two simple groups: **Over-Win-Percentage Median and Under-Win-Percentage Median coaches**. Find the calculation below!  
- Then I drew two scatter plots in Tableau with the grouping on color, which returned what I wanted, the "opposites" in Wins vs. Losses:  
![image](https://user-images.githubusercontent.com/96722899/148792025-7b8f1a2a-a9c5-49ba-a3d9-883996207c7f.png)
- The "BAN" area in the upper right corner of the dashboard is enabled by filter action. Clicking on a data point draws out the statistics for the selected coach (same function is available in the tooltips). While the "Median Win Percentage" is unchanged and acts as a comparison point.  
![image](https://user-images.githubusercontent.com/96722899/148793745-a7c52753-c532-4de6-b916-a5ca89ac0b09.png)
- The Legend functions as a data point highlighter as well (using a highlight action) - idea by Autumn Battani's [entry](https://public.tableau.com/app/profile/autumnbattani/viz/Back2VizBasicsScatterplot/D1Coaches):
![image](https://user-images.githubusercontent.com/96722899/148793675-3e5c1810-fe29-4490-b93a-18da41a54a3d.png)
- As for the introduction text, I went with a description of what we are looking at. The project's aim is to make the understanding as simple as possible, so this text confirms what we see visually:
![image](https://user-images.githubusercontent.com/96722899/148792753-68e7a728-5a26-4d73-9f1c-c58eff50aac2.png)
- Additional context is added via annotated areas. First, I liked the thought that there are coaches who are relatively new, but already holding an over-the-median win percentage. Second, the Losses scatterplot made obvious that the Wins outnumber the Losses, thus in the data we are really looking at only the most successful coaches (plus I saw Andy Cotgreave's video about this note on LinkedIn).
![image](https://user-images.githubusercontent.com/96722899/148793604-08814e7d-e2bc-4a5a-b38c-34687a903c7a.png)

As per the visual elements such as background, title, text annotations etc., I used [Figma](https://www.figma.com/).

## Tableau Calculations

**Overall Median** - simple FIXED LOD (fun fact: you can leave the keyword in case of a FIXED LOD, using curly brackets is enough)
```
{PERCENTILE([Win Percentage], 0.50)}
```

**Win Percentage Median** - First I intended to do more than 2 categories, that is why I used the PERCENTILE() function and ELSEIF branches instead of the MEDIAN() and a simple ELSE branch, but I ended up using only 2. However, I never used the PERCENTILE() function before, thus didn't change it to MEDIAN() for the sake of practice.
```
IF [Win Percentage] >= {PERCENTILE([Win Percentage], 0.50)}
THEN "Over Median"
ELSEIF [Win Percentage] >= {PERCENTILE([Win Percentage], 0)}
THEN "Under Median"
END
```
