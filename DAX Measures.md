**Total Revenue**: COALESCE(SUM('Quickbooks'[Amount]), 0)

  --Calculates the total amount of revenue across all transactions from Quickbooks dataset
  
**Total Hours Logged**: COALESCE(SUM('Job_Log'[Hours_Logged]), 0)

  --Calculates the total hours logged across all jobs
  
**Revenue Per Man-Hour**: COALESCE(DIVIDE([Total Revenue], [Total Hours Logged]), 0)

  --Calculates how much revenue per hour logged was received
  
**Average Ticket Size**: COALESCE(DIVIDE([Total Revenue], DISTINCTCOUNT('Quickbooks'[Num])),0)

  --Calculates the revenue taken in on average per job completed
  
**Total Labor Cost**: COALESCE([Total Hours Logged] * 18, 0)

  --Calculates total cost of Labor using a rate of $18 per hour
  
**Product Revenue**: COALESCE(CALCULATE([Total Revenue], 'Quickbooks'[Product/Service full name] IN{"Soil", "Concrete", "Sod", "Rock Fountain", "Pump", "Rocks", "Sprinkler Heads", "Sprinkler Pipes"}), 0)
 
  --Calculates total amount made from selling products

**Service Revenue**: COALESCE(CALCULATE([Total Revenue], 'Quickbooks'[Product/Service full name] IN {"Design", "Gardening", "Pest Control", "Maintenance & Repair", "Services"}), 0)
 
  --Calculates total amount made from rendering services

**Month Year**: FORMAT('Calendar'[Date], "mmm yyyy")

  --Adds an option to calendar to select for month and year (abbreviated month to three characters; used for Date Slicer)

**Month Sort**: FORMAT('Calendar'[Date], "yyyyMM")

  --Filter for added "Month Year" measure (ensures months are not listed alphabetically but rather by month order)

**KPI Arrow**: IF([Revenue Per Man-Hour] >= 30,"▲","▼")

  --Creates visual to show if "Revenue Per Man-Hour" is hitting targeted amount or not ($30 per Man-Hour is the target)

**KPI Arrow Color**: SWITCH(TRUE(),[Revenue Per Man-Hour] >= 30, "#107C41", [Revenue Per Man-Hour] < 30, "#A80000", "#000000")

  --Adds green color to "KPI Arrow" measure if target amount is reached, and red color if target amount is not reached (for quick glance readability)
