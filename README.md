# Awesome-Chocolates-Sales-Insights-Interactive-Power-BI-Dashboards
Interactive Power BI reports built on the Awesome Chocolates Company sales dataset. 
The project focuses on cleaning and preparing raw sales data, designing dashboards to track KPIs, and uncovering insights into revenue trends, product performance, and regional sales distribution.
This project contains two Power BI dashboards created using the Awesome Chocolates Company sales dataset. 
The reports highlight:
 - Revenue trends and growth patterns
 - Product performance across categories
 - Regional sales distribution and KPIs 
## Features
 - Interactive filters and drill‑downs
 - Visualizations including bar charts, line charts, and maps
 - Actionable insights for business decision making
 ## DAX used in Report1
    -amount_per_box = DIVIDE([total_amount],[total_boxes])
    -profit_per_box = DIVIDE([total_profit],[total_boxes])
    -profit_percentage = DIVIDE([total_profit],[total_amount])
    -shipment_count = COUNTROWS(shipments)
    -total_actual_cost = sum(shipments[actual_cost])
    -total_amount = sum(shipments[Amount])
    -total_amount_last_year = CALCULATE([total_amount],SAMEPERIODLASTYEAR('calendar'[cal_date]))
    -total_profit = [total_amount]-[total_actual_cost]
    -total_boxes_last_year = CALCULATE([total_boxes],SAMEPERIODLASTYEAR('calendar'[cal_date]))

## DAX used in Report2:
     -latest_date = LASTDATE('calendar'[Start of Month])
     -latest_MOM_sales_change% = var ld=[latest_date] var this_month_sales=[Total_sales_latest_month] var prev_month_sales=CALCULATE([Total_sales],'calendar'[Start of Month]=EDATE(ld,-1))  RETURN DIVIDE(this_month_sales-prev_month_sales,prev_month_sales)
     -LBS_% = DIVIDE([LBS_count],[Total_shipments])
     -LBS_count = CALCULATE([Total_shipments],shipments[Boxes]<50)
     -MOM_boxes_change% = var this_month=[Total_Boxes] var prev_month=[Total_Boxes_prev_month] return DIVIDE(this_month-prev_month,prev_month)
     -MOM_sales_change% = var this_month=[Total_sales] var prev_month=[Total_sales_prev_month] return DIVIDE(this_month-prev_month,prev_month)
     -Profit_% = DIVIDE([Total_profit],[Total_sales])
     -status = IF([Profit_%]>[Profit_target],"👍","👎")
     -Total_sales_latest_month = var ld=[latest_date] return CALCULATE([Total_sales],'calendar'[Start of Month]=ld)
     -Total_sales_prev_month = CALCULATE([Total_sales],PREVIOUSMONTH('calendar'[Date]))
     - Total_shipments_prev_month = CALCULATE([Total_shipments],PREVIOUSMONTH('calendar'[Date]))
## Visulaizations used in Report1:
        -KPI card:Total sales,Total boxes,Total profit,shipment count,profit%
        -Area chart: total_amount last year vs prevoius year
        -Bar graph:shipment_count by no of boxes
        -donut chart:geo by total_amount
        -Area chart: Boxes last year vs prevoius year
        -Table: product,total_amount,profit%
        -Table: picture,first_name,last_name,total_boxes,profit%

## Visulaizations used in Report2:
        -KPI card:Total sales,Total boxes,Total profit,shipment count,profit%
        -Line chart:Start of month vs Parameter(Total sales,Total boxes,Total profit,shipment count,profit%)
        -Gauge:profit%,LBS%
        -Stacked Column chart:Boxes vs Total_shipments
        -Table:Product,Totalsales,totalprofit,profit%,status
        -Table:picture,salesperson,totalsales,totalprofit,profit%,status
        -
































