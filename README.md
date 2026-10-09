### I took a construction H&S tracker that lived entirely in Excel and rebuilt it as an interactive Power BI report.
The goal was to keep the existing dashboard structure while making reporting automatic, filterable and comparable across periods.

## The original workbook used fixed-range COUNTIFS formulas and an action tracker that was updated by hand. In Power BI, I:
    -Consolidated actions from observations, incidents, RFAs and SLT tours into a single Master Action Tracker, so nothing is entered twice
    -Added previous-period comparisons (observations, RFAs, incidents, open actions, RIDDOR, AFR, AAFR)
    -Built an action-age profile and raised vs closed trends
    -Added slicers for date range, package, contractor, status and overdue
    -Tracked AFR, AAFR, HiPo and lost-time indicators over time
    -Audited the Excel logic and corrected inconsistent ranges and labels

 Tools: Power BI, DAX, Power Query, Excel.
## Excel form 
 ![](https://github.com/Ebenezer080925/Upgrading-an-Excel-safety-tracker-to-Power-BI/blob/main/Excel%20Executive%20Dashboard.png)  
 ![](https://github.com/Ebenezer080925/Upgrading-an-Excel-safety-tracker-to-Power-BI/blob/main/Excel%20Executive%20Dashboard%202.png)

 ## Power Bi Upgraded Format 
 ![](https://github.com/Ebenezer080925/Upgrading-an-Excel-safety-tracker-to-Power-BI/blob/main/To%20upgrade%20.png)
 ![](https://github.com/Ebenezer080925/Upgrading-an-Excel-safety-tracker-to-Power-BI/blob/main/To%20upgrade%202%20.png)

 ## 2.The problem (the Excel version)
    -The action tracker was updated manually
    -Formulas used fixed ranges (e.g. rows 2 to 1109), so new data could be missed
    -Some figures were hard-coded (e.g. the open-actions total)
    -No automatic comparison with the previous period
    -Limited filtering by package or contractor
 ## 3.Data sources (the workbook's sheets)
Observations, RFA Tracker, Incident Tracker, SLT Tours, The Voice, Action Tracker, and drop-list lookups. [Add record counts, e.g. 200+ observations, ~400 RFA rows.]

## 4. Data model
    -Four fact tables (Observation, RFA Tracker, Incident Tracker, SLTsTours) linked to a shared DateTable
    -A calculated Master Action Tracker that unions actions from all sources into one standard shape (source, date raised, description, status, close date, owner, due date)
    -A dedicated measures table for all DAX
## 5. What I added beyond the Excel version
| Area | Excel | Power BI |
|---|---|---|
| Action tracking | Entered manually | Auto-consolidated from four sources |
| Period comparison | None | Previous-period value and % change on each KPI card |
| Action ageing | None | Action-age profile chart |
| Actions over time | None | Raised vs closed by month and by day of week |
| Filtering | Date cells only | Slicers: date, package, contractor, status, overdue |
| Rate trends | Single figures | AFR and AAFR trend lines |
| Risk themes | Basic counts | Golden Risk and severity breakdowns |

|  |   |   |
|---|---|---|
| Rate trends | Reported in the Excel dashboard | Interactive AFR and AAFR trend lines that respond to the filters |
| Risk themes | Golden Risk reporting | Golden Risk and severity breakdowns that respond to the filters |

 
## 6. Key DAX and techniques
    -DATEADD- for previous-period comparisons
    -DIVIDE- for safe percentage change
    -Open/closed- action logic using status lists
    -DATEDIFF- for action age buckets
    -Dynamic- title showing the selected date range
    -UNION and SELECTCOLUMNS- for the Master Action Tracker

## 7. Dashboard pages(Overall)
1.Executive Dashboard: KPIs, trends, golden risks, incidents
2.Master Action Tracker: all actions with filters

![](https://github.com/Ebenezer080925/Upgrading-an-Excel-safety-tracker-to-Power-BI/blob/main/Upgrade%20.png)
![](https://github.com/Ebenezer080925/Upgrading-an-Excel-safety-tracker-to-Power-BI/blob/main/Upgrade%201.png)
![](https://github.com/Ebenezer080925/Upgrading-an-Excel-safety-tracker-to-Power-BI/blob/main/Upgrade%202.png)

