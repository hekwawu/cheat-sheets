### Table of Contents
[Datetimes 101](#datetimes-101) </br>
[Formatting Dates](#formatting-dates)</br>
[Extracting Date Parts](#extracting-date-parts)</br>
[Truncating Datetimes](#truncating-datetimes)</br>
[Datetime Math](#datetime-math)</br>


### Datetimes 101
- Default timestamp follows the format 'YYYY-MM-DD HH24:MMI:SS:MS'
- If you're looking to only work with the date of a timestamp, use a `CAST` function
```sql
timestamp::date
```
- Getting current timestamps
```sql
SELECT NOW()            ## Selects current full timestamp
SELECT CURRENT_DATE     ## Selects current date
SELECT CURRENT_TIME     ## Selects current time
``` 

### Formatting Dates
```sql
## When working with full timestamp:
TO_CHAR(timestamp, format)::timestamp
## when working with just dates:
TO_CHAR(timestamp::date, format)::date
```
- Be aware that `TO_CHAR` turns timestamp to a string, if any type of math is going to be done on it, cast back into a datetime
- Date format should include spaces and punctuation (/, - etc), don't need to add extra commas
 
#### Common date formats
- Default format is 'YYYY-MM-DD'
- Key date queries to know
 ```sql
 TO_CHAR(timestamp, 'MM/DD/YYYY')     ## Result: 01/01/2023
 TO_CHAR(timestamp, 'Mon DD, YYYY')   ## Result: Jan 01, 2023
 TO_CHAR(timestamp, 'YYYY - MM')      ## Result: 2023-01
 TO_CHAR(timestamp, 'Mon YYYY')       ## Result: Jan 2023
 ```
 
- Popular date formats:

  |         |                                         |           |
  |-------- |-----------------------------------------|-----------|
  | `YYYY`  | Year, numeric, 4 digits                 | 2018      |
  | `YY`    | Year, numeric, 2 digits                 | 18        |
  | `Q`     | Quarter                                 | 1         |
  | `MM`    | Month, numeric (01 - 12) 	              | 01  	    |
  | `Mon`   | Month, 3 day abbrev      	              | Jan 	    |
  | `DD`    | Day of the month (0-31)                 | 15        |
  | `D`     | Day of the week (Sun = 1, Sat = 7)      | 3 (Tues)  |
  | `ID`    | ISO day of the week (Mon = 1, Sun = 7)  | 2 (Tues)  |
  | `WW`    | Week number of the year (1 - 53)        | 01        |
  

#### Common time formats 
- Default format is `HH24:MI:SS:MS`
- Key queries to know
```sql
TO_CHAR(timestamp, 'HH24:MI')            ## Result: 22:30
TO_CHAR(timestamp, 'HH12:MI am or pm')   ## Result: 10:30 pm
```
- Popular time formats
 
   |                            |                                  |         |
   |----------------------------|----------------------------------|---------|
   | `HH12`                     | Hour of the day (01 - 12)        | 1  (PM) |
   | `HH24`                     | Hour of the day (00 - 23)        | 13 (PM) |
   | `MI`                       | Minute (00 - 59)                 | 30      |
   | `SS`                       | Second (00 - 59)                 | 30      |
   | `AM, am, PM or pm`         | Meridiem indicator (w/o periods) | 1 pm    |
   | `A.M., a.m., P.M. or p.m.` | Meridiem indicator (w/ periods)  | 1 p.m.  |

### Extracting Date Parts

```sql 
EXTRACT(component FROM timestamp)
DATE_PART(component FROM timestamp)
```
- Returns specific part of a datetime
- Relevant Components for Extraction:
*note that outputs do not have leading 0s)
  - YEAR
  - MONTH 
  - DAY 
  - HOUR
  - MINUTE
  - SECOND

### Truncating Datetimes
```sql
DATE_TRUNC('date_part', datetime)
```
- Returns date rounded to the relevant date part. Does NOT change the type
- Relevant units for truncation:
  - year 
  - quarter
  - month
  - week
  - day
  - hour
  - minute
  - second
  - millisecond
  
### Datetime Math
- Difference between *dates only* can be calculated using "-" operand
  - Output will be number of days, as a *integer* data type
- To calculate the difference between timestamps:
```sql
AGE(later_ts, earlier_ts) ## Differnces between timestamps
AGE(ts)                 ##Difference between now and timestamp
```
- To add a set amount of time to datetimes, use an `INTERVAL` function

```sql
date + INTERVAL 'x UNIT'
date - INTERVAL `' UNIT'
``` 
  - Note that the unit is *never plural* (Ex. 2 DAY, NOT 2 DAYS)
  - Can include multiple intervals 
- Relevante units for datetime math:
  - year
  - month
  - week
  - day
  - hour
  - minute
  - second
  - millisecond
