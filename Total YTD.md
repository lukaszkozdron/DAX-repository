## Description

The `Total YTD` measure in this DAX expression is designed for use in Power BI to calculate the year-to-date (YTD) total based on certain conditions. It utilizes the `ShowValueForDates` condition to determine whether to display the YTD total.

### Functionality

1. **ShowValueForDates**: This condition evaluates whether to display the YTD total based on the availability of data for the current year. If `ShowValueForDates` is TRUE, the YTD total is calculated; otherwise, it returns NULL.

### Usage

The `Total YTD` measure is useful for tracking cumulative values over the course of the year in Power BI reports. It allows for dynamic calculation of YTD totals based on the presence of data in the current year.

### Example

```DAX
Total YTD = 
IF(
    [ShowValueForDates],
    CALCULATE(
        SUM ( 'Fact'[Value] ),
        DATESYTD('Calendar'[Date])
    )
)
