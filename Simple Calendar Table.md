## Description

The `Calendar` DAX expression generates a calendar table containing monthly dates from January 2022 to February 2024. This calendar table is commonly used as a Date dimension table in Power BI for time-based analysis and reporting.

### Functionality

- Creates a table with columns: "Date", "Year", "Month", "MonthName", "YearMonth", and "YearMonthName".
- Populates the "Date" column with monthly dates from January 2022 to February 2024.
- Extracts year, month, and their respective names from the date.
- Formats the date as "YYYY-MM" and "MMMM YYYY" for the "YearMonth" and "YearMonthName" columns, respectively.

### Usage

You can use this calendar table as a Date dimension table in your Power BI model. It facilitates time-based calculations and enables filtering and grouping of data by various time dimensions.

### Example

```DAX
Calendar = 
ADDCOLUMNS (
    CALENDAR (DATE(2022, 1, 1), DATE(2024, 12, 31)), // place start and end date - example start: 2022-01-01 /  end: 2024-12-31
    "Year", YEAR ( [Date] ),
    "Month", MONTH ( [Date] ),
    "MonthName", FORMAT ( [Date], "MMMM" ),
    "YearMonth", FORMAT ( [Date], "YYYY-MM" ),
    "YearMonthName", FORMAT ( [Date], "MMMM YYYY" )
)
