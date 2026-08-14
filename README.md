# Landscaping Revenue Analysis/Data Integration
Often times, a business has the issue of disjointed data (data that is spread across multiple mediums/software/locations) which makes actionable data driven decision making impossible, requiring a business to make guesses based on "feel." In addition to this, the data and information is often not in a digestible format, and is costly on time. These factors prevent the data from "speaking" to a business owner or team. This project conjoins data from multiple sources, provides/visualizes valuable KPIs and data driven insights to address these pain points, and empower decision making capabilities.
## **Methodology** 
For this project's data sources I used Quickbooks, and Mockaroo. I exported a "Sales by Customer Detail" report from Quickbooks's Sandbox environment (an area on Quickbooks's website that uses generated data to allow a user to experiment with Quickbooks's native features) from a mock Landscaping Company I titled "Tim's Landscaping and Design" to an excel file. This report ran from 1/1/2026-7/26/26 and provided lists of clients and services/products rendered. With Mockaroo, I generated an excel file data set that has 200 entries of services and hours logged to complete the given jobs. These two excel files simulate a common situation for businesses that have disjointed data; one location has customer and sales information while another has operational information for the business (these raw excel files can be found attached to the main branch). Before i could connect these files in the model, I first created a date table ("Calendar;" code for table can be found linked to the main branch) and linked both excel source files to this date table (this was done to help sure up discrepancies between the auto generated Mockaroo file and Quickbooks export where dates might have been generated in Mockaroo but not reflected in Quickbooks report). In order to conjoin and allow insights to be made with this data, I then used PowerBI's "Power Query" capabilities and "DAX Measures" to first clean, then model, then calculate KPI measures, and finally visualize performance year-to-date (7/26/26) for Tim's Landscaping and Design.

--Quickbooks Sandbox: https://sandbox.qbo.intuit.com/app/homepage

--Mockaroo: https://mockaroo.com/

**Considerations**

**DATA CLEANING** For these datasets, all cleaning was done inside PowerBI via Power Query, with most of the cleaning being done to the Quickbooks exported report. Quickbooks is known for adding extra top rows when exported to an excel file, so I removed these (returns null values). I also filtered out other null values, changed the data types of the columns, and replaced other relevant null values with "0" (there is a quantity section in the sales report that returned some "null" values because the service rendered would not have had a quantity in the first place, so replacing with 0 is a valid transformation). Lastly, I filtered out blank rows caused by a mismatch of "Product/Service Full Name" and "Discounts" that were applied.  

**KPI METRICS** For the visualization of data portion of this project, I provided 4 industry specific KPI metrics to be tracked and accessed in PowerBI which are as follows: "Total Revenue", "Total Hours Logged", "Revenue Per Man-Hour", and "Average Ticket Size" (the DAX measures for these KPI can be found in the attached "DAX Measures" file). These KPIs track essential information for a landscaping business, and are must have additions to a visualization because they allow the business to quickly assess current profile health. 

## **Results**
**DASHBOARD ELEMENTS** The dashboard features a performance banner that is comprised of the aforementioned essential KPI metrics. In addition to this banner there are other charts:

Pie Chart (to show the share of revenue that comes from services rendered vs product sales)

Column Charts (one to show which services/products are the most profitable and another to show which clients are the most profitable)

Line Chart (to show the trend of revenue through the year)

Date Slicer (to allow quick filtering of data by month)
