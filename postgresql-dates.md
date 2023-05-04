### Table of Contents
[Dates](https://github.com/hekwawu/cheat-sheets/new/main.md###Dates)

### Formatting Dates
Dates default to the 'YYYY-MM-DD' format

  ```sql
  TO_CHAR(timestamp, date_format)
  ```

#### Useful date formats
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

#### Useful time formats 

  <details>
  <summary>AM/PM Indicators/summary>
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
NOW()
``` 

```sql
SELECT DATE_FORMAT(date_string, date_format)
```
Available Date Extractions:
  
  
### Date Math
