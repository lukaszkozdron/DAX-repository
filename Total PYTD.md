## Description

The `Total PYTD` DAX expression is intended for use in Power BI to calculate the year-to-date (YTD) total based on certain conditions. It utilizes the `ShowValueForDates` condition to determine whether to display the YTD total.

### Functionality

1. **ShowValueForDates**: This expression evaluates whether to display the YTD total based on the availability of data for the previous year. It uses the `CALCULATE` and `CALCULATETABLE` functions to ascertain whether data exists for the previous year. If `ShowValueForDates` is TRUE, the YTD total is calculated, otherwise, it returns NULL.

### Usage

The `Total PYTD` expression is employed to dynamically show or hide the YTD total based on the presence of data for the previous year. It allows for more context-aware visualization and analysis in Power BI reports.

### Example

```DAX
Total PYTD = 
IF(
    [ShowValueForDates],
    CALCULATE(
        [Total YTD],
        CALCULATETABLE(
            DATEADD('Calendar'[Date],-1,YEAR),
            'Calendar'[DateWithSale] = TRUE
        )
    )
)
