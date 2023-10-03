# Angelos-Pizza-Dashboard
# IMPORTANT: Theres a web link bellow for the dashboards, if Tableau isnt installed onto your PC!! https://public.tableau.com/app/profile/kyle.vanburen/viz/AngelosPizzaAnalytics/Final?publish=yes

 MYSQL query scripts are included to give a better understanding for my numbers and the data I wanted to pull specifically.

 I did have to use the import wizard in mysql to import data from Excel csv files to make my tables in mysql. 

You will need to use Excel to access the CSV files, heres a link for the free web version of Excel: https://www.office.com/launch/excel?ui=en-US&rs=US&auth=2
 
 EXCEL csv file link: https://drive.google.com/drive/folders/1wXkVaWjAplONy5PT8Nxc25CdNh6pyFnX?usp=sharing

 S.T.A.R

SITUATION - Owner of Angelo's Pizza has requested me to develop three unique dashboards to increase the business profit.

TASK - One for orders & sales comparsions. A second one, for inventory quantity & cost. And the third and last dashboard for staff labor cost.

ACTION - Using Mysqls import data wizard tool and sql queries I collected and transformed the data from the excel sheets. Using Tableaus visualizations and slicer filters I built each dashboard unique and different. I created an orders dashboard that has a donut and bar chart to show comparisons in sales by food & pizza type. One pie chart to show camparisons on delivery(T or F). Along with a double line chart to show trends over time by total sales and total orders. And a heat map to show where the most sales are.

I developed an inventory dashboard has one color coded table visualization for showing the ingredient costs, quantity, and percent remaining. And a second table visualization for showing the top selling pizzas at the current time period of the day.


I built a staff labor cost dashboard for my last one that shows the staffs name, shift start & end time, shift hours, hourly rate, and cost of staff that day all in one table visualization.

RESULT - Because of my initiative, Angelo's owner now knows pizza makes up for 64% of total sales. Angelo's owner also knows to make more Large Quattro Formaggi pizzas since it's the top selling pizza at $741. Thanks to my findings, Angelo's owner can note 1pm has the highest amount of orders placed. And that 7pm produces the highest amount of sales. Angelo's owner can start increasing shipment order quantities for banoffe pie, anchovies, and pizza dough since the percent remaining was color coded red for take action. Finally, with labor cost being high, Angelo's owner can make changes to Luqmans'($548.25) and Mindys'($439.88) four day schedule to help lower labor cost since they cost the most in labor.


 # Query Script Breakdown
 1. ORDER&SALES - This SQL script is designed to retrieve specific data from the "orders" table along with related information from the "item" and "address" tables. It combines information about orders, items, and delivery addresses into one result set.
- order_id: The unique identifier for each order.
- item_price: The price of the item in the order.
- quantity: The quantity of the item in the order.
- item_cat: The category of the item.
- item_name: The name of the item.
- created_at: The timestamp when the order was created.
- delivery_address1 and delivery_address2: The delivery addresses.
- delivery_city: The city for delivery.
- delivery_zipcode: The ZIP code for delivery.
- delivery: Delivery information.


2. STOCK1 - This SQL script creates a view named 'stock1' that provides detailed information about the stock of ingredients required for items in your database. The view calculates various metrics related to ingredient costs and stock quantities based on order data and recipes.

    item_name: The name of the item.
- ing_id: The ingredient's unique identifier.
- ing_name: The name of the ingredient.
- ing_weight: The weight of the ingredient.
- ing_price: The price of the ingredient.
- order_quantity: The total quantity of the ingredient ordered.
- recipe_quantity: The quantity of the ingredient required according to the recipe.
- ordered_weight: The total weight of the ingredient ordered.
- unit_cost: The cost per unit weight of the ingredient.
- ingredient_cost: The total cost of the ingredient required for the orders.


3. ING COST&WEIGHT - This SQL script performs a calculation to determine ingredient costs for items based on order data and recipes. It creates a result set that includes various metrics related to ingredient costs and quantities.

   It combines data from the "orders," "item," "recipe," and "ingredient" tables to create a result set with the same columns as listed in script #3!!


4. EMPLOYEE COST - This SQL script retrieves and calculates staff costs based on rota data. It combines information from the "rota," "staff," and "shift" tables to create a result set with details about staff shifts and associated costs.
   date: The date of the shift.
- first_name: The first name of the staff member.
- last_name: The last name of the staff member.
- hourly_rate: The hourly rate of the staff member.
- start_time: The start time of the shift.
- end_time: The end time of the shift.
- hours_in_shift: The duration of the shift in hours.
- staff_cost: The cost of the staff member for the shift, calculated by multiplying the hours worked by the hourly rate.

If you have any questions or need further assistance, please feel free to contact the project maintainer at vanburen.kyle@yahoo.com.


   

   
