# Back To Viz Basics (#B2VB) community project - Week 1, 2022

A brand new Tableau community project were introduced at the end of last year.
The [B2VB](https://www.thetableaustudentguide.com/vizbasics) team is handing out simple data sources each week which are waiting for to be visualized using easy-to-understand charts and diagrams.

This is my attempt for the first week:
![visualization](https://user-images.githubusercontent.com/96722899/148657605-f5f37484-ee03-4c5a-a965-b5132e6afaa1.png)


Find the interactive on my [Tableau Public profile](https://public.tableau.com/app/profile/norbert.borb.s/viz/B2VB_Week1/NCAA?publish=yes).

## Idea

## Calculations

```
IF [Win Percentage] >= {PERCENTILE([Win Percentage], 0.50)} THEN "Over Median"
//ELSEIF [Win Percentage] >= {PERCENTILE([Win Percentage], 0.50)} THEN "50-74%"
//ELSEIF [Win Percentage] >= {PERCENTILE([Win Percentage], 0.25)} THEN "25-49%"
ELSEIF [Win Percentage] >= {PERCENTILE([Win Percentage], 0)} THEN "Under Median"
END
```

```
{PERCENTILE([Win Percentage], 0.50)}
```
