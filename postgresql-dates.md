### Table of Contents
[Dates 101](https://github.com/hekwawu/cheat-sheets/postgresql-dates/main.md###Dates101) </br>
[Formatting Dates](https://github.com/hekwawu/cheat-sheets/postgresql-dates/main.md###FormattingDates)
[Extracting Dates](https://github.com/hekwawu/cheat-sheets/postgresql-dates/main.md###ExtractingDates)
[Date Math](https://github.com/hekwawu/cheat-sheets/postgresql-dates/main.md###FormattingDates)


### Dates 101 
- Dates default to the 'YYYY-MM-DD' format

```sql
SELECT NOW()            ## Selects current full timestamp
SELECT CURRENT_DATE     ## Selects current date
``` 

### Formatting Dates
```sql
TO_CHAR(timestamp, date_format)
```
- Date format should include spaces and punctuation (/, - etc), don't need to add extra commas
  - Example: Transform date to this format: Jan 01, 2021
  
      ```sql
       TO_CHAR(timestamp::DATE, 'Mon DD, YYYY')
      ```
  -  When only using date component, cast the timestamp as a date
  
  
#### Common date formats
  <details>
  <summary>Year/Quarter</summary>
    
    |         |                                  |        |
    |-------- |----------------------------------|--------|
    | YYYY | Year, numeric, 4 digits          | 2018   |
    | YY    | Year, numeric, 2 digits          | 18     |
    | Q    | Quarter                          | 1      |
  </details>
  
  <details>
  <summary>Month</summary>
    |    	|                          	|    	|
    |----	|--------------------------	|----	|
    | MM 	| Month, numeric (01 - 12) 	| 01 	|
    | Mon	| Month, 3 day abbrev      	| Jan |


   </details>
   
   <details>
  <summary>Day/Week</summary>
    |   |   |   |
    |---|---|---|
    | `DD`    | Day of the month (0-31)                   | 15   |
    | `D`     | Day of the week (Sun = 1, Sat = 7)        | 3    |
    | `ID`    | ISO day of the week (Mon = 1, Sun = 7)    | 2    |
    | `WW`    | Week number of the year (1 - 53)          | 01   |
  </details>

#### Common time formats 

  <details>
  <summary>AM/PM Indicators</summary>
    |   |   |   |
    |---|---|---|
    | `AM, am, PM or pm	`        | Meridiem indicator (w/o periods)   | 1 pm |
    | `A.M., a.m., P.M. or p.m.	`| Meridiem indicator (w/ periods)    | 1 p.m|
  </details>
  
  <details>
  <summary>Hour</summary>
    |   |   |   |
    |---|---|---|
    | `HH12`    | Hour of the day (01 - 12)        | 1  (PM) |
    | `HH24`    | Hour of the day (00 - 23)        | 13 (PM) |
  </details>
  
  <details>
  <summary>Minute</summary>
    |   |   |   |
    |---|---|---|
    | `MI`    | Minute (00 - 59)       | 30 |
  </details>
  
  <details>
  <summary>Second</summary>
    |   |   |   |
    |---|---|---|
    | `SS`      | second (00 - 59)      | 30 |
  </details>

### Extracting Dates

```sql 
EXTRACT(component FROM timestamp) 
```
- Available Date Components for Extraction:
  - YEAR
  - MONTH
  - DAY
- Available Time Components for Extraction:
  - HOUR
  - MINUTE
  - SECOND

### Rounding Timestamps
```sql
SELECT DATE_TRUNC('date_part', timestamp)
```
- Returns date rounded to the relevant date part
- Available units for truncation:
  - year
  - quarter
  - month
  - week
  - day
  - hour
  - minute
  - second
  - milliseconds
  
### Date Math
- Dates that are in the same format that can be added or subtracted without reformatting