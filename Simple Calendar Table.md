## Description

The `Calendar` table in this DAX expression is designed for use in Power BI to generate a date table covering the range from January 1, 2022, to December 31, 2024. It also adds additional columns for year, month, month name, year-month, and year-month name for enhanced date analysis.

### Functionality

1. **DateWithSale**: This additional column checks whether each date in the calendar table corresponds to a date with a sale in the "Fact" table. If a sale occurred on the date, it returns TRUE; otherwise, it returns FALSE.

### Usage

The `Calendar` table is crucial for time-based analysis and visualization in Power BI reports. The inclusion of the "DateWithSale" column allows for deeper insights into sales patterns and facilitates the creation of dynamic visualizations based on sales data.

### Example

```DAX
Calendar = 
ADDCOLUMNS (
    CALENDAR (DATE(2022, 1, 1), DATE(2024, 12, 31)), // place start and end date - example start: 2022-01-01 /  end: 2024-12-31
    "Year", YEAR ( [Date] ),
    "Month", MONTH ( [Date] ),
    "MonthName", FORMAT ( [Date], "MMMM" ),
    "YearMonth", FORMAT ( [Date], "YYYY-MM" ),
    "YearMonthName", FORMAT ( [Date], "MMMM YYYY" ),
    "DateWithSale", IF([Date] <= MAX('Fact'[Date]), TRUE(), FALSE())
)
