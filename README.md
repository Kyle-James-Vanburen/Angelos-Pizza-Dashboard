# Angelos-Pizza-Dashboard

**Introduction:**

Angelos-Pizza-Dashboard is a comprehensive tool developed to analyze Angelo's Pizza sales data and optimize business operations. This dashboard provides insights into orders, sales, inventory, and staff labor costs, enabling informed decision-making for increased profitability.

**Important Links:**

• Tableau Story (View Dashboard): https://public.tableau.com/app/profile/kyle.vanburen/viz/AngelosPizzaAnalytics/Final?publish=yes

• Excel CSV Files: https://drive.google.com/drive/folders/1wXkVaWjAplONy5PT8Nxc25CdNh6pyFnX?usp=sharing

## S.T.A.R

### Situation:

The owner of Angelo's Pizza tasked me with developing three unique dashboards to enhance business profit through data-driven strategies.

### Tasks:

**1. Orders & Sales Dashboard:**

• Develop visualizations comparing orders and sales, including charts for food & pizza type comparisons, delivery patterns, and sales trends.

**2. Inventory Dashboard:**

• Create a dashboard displaying ingredient costs, quantities, and top-selling pizzas based on real-time data.

**3. Staff Labor Cost Dashboard:**

• Build a dashboard detailing staff names, shift timings, hours worked, hourly rates, and daily labor costs.

### Actions:

• Utilized MySQL's import data wizard and SQL queries to collect and transform data.

• Leveraged Tableau's visualizations and slicer filters to create unique dashboards for each specific aspect.

• Designed detailed visualizations including donut charts, bar charts, line charts, pie charts, and heat maps.

### Results:

• Discovered that pizza constitutes 64% of total sales, prompting strategic focus on pizza offerings.

• Identified the top-selling pizza ("Large Quattro Formaggi") generating $741 in revenue.

• Pinpointed peak order times (1 pm) and highest sales period (7 pm) for targeted business strategies.

• Noted inventory shortages in items like banoffee pie, anchovies, and pizza dough, signaling necessary adjustments in supply chain management.

• Addressed high labor costs by suggesting optimized staff schedules, potentially saving costs.

## Query Script Breakdown

**1. ORDER & SALES**

• SQL script retrieving specific data from the "orders," "item," and "address" tables.

• Provides a comprehensive overview of orders, item details, and delivery information.

        SELECT
	    o.order_id,
	    i.item_price,
	    o.quantity,
	    i.item_cat,
	    i.item_name,
	    o.created_at,
	    a.delivery_address1,
	    a.delivery_address2,
	    a.delivery_city,
	    a.delivery_zipcode,
	    o.delivery 
        
	FROM
	    orders o
	    LEFT JOIN item i ON o.item_id = i.item_id
	    LEFT JOIN address a ON o.add_id = a.add_id

**2. STOCK1**

• Creates a view named 'stock1' detailing ingredient costs, quantities, and unit costs for items in the database.

• Utilizes data from "orders," "item," "recipe," and "ingredient" tables to generate insights into stock metrics.

    CREATE VIEW stock1 AS
    
    SELECT
       s1.item_name,
       s1.ing_id,
       s1.ing_name,
       s1.ing_weight,
       s1.ing_price,
       s1.order_quantity,
       s1.recipe_quantity,
       s1.order_quantity * s1.recipe_quantity AS ordered_weight,
       s1.ing_price / s1.ing_weight AS unit_cost,
       (s1.order_quantity * s1.recipe_quantity) * (s1.ing_price / s1.ing_weight) AS ingredient_cost
    
    FROM (SELECT
	   o.item_id,
       i.sku,
	   i.item_name,
       r.ing_id,
       ing.ing_name,
       r.quantity AS recipe_quantity,
	   sum(o.quantity) AS order_quantity,
       ing.ing_weight,
       ing.ing_price
    
    FROM 
	   orders o
	   LEFT JOIN item i ON o.item_id = i.item_id
       LEFT JOIN recipe r ON i.sku = r.recipe_id
       LEFT JOIN ingredient ing ON ing.ing_id = r.ing_id
    
    GROUP BY 
	   o.item_id,
	   i.sku,
       i.item_name,
       r.ing_id,
       r.quantity,
       ing.ing_name,
       ing.ing_weight,
       ing.ing_price) s1;

3. ING COST&WEIGHT - This SQL script performs a calculation to determine ingredient costs for items based on order data and recipes. It creates a result set that includes various metrics related to ingredient costs and quantities.

       SELECT
          s1.item_name,
          s1.ing_id,
          s1.ing_name,
          s1.ing_weight,
          s1.ing_price,
          s1.order_quantity,
          s1.recipe_quantity,
          s1.order_quantity * s1.recipe_quantity AS ordered_weight,
          s1.ing_price / s1.ing_weight AS unit_cost,
         (s1.order_quantity * s1.recipe_quantity) * (s1.ing_price / s1.ing_weight) AS ingredient_cost
    
       FROM (SELECT
	      o.item_id,
          i.sku,
	      i.item_name,
          r.ing_id,
          ing.ing_name,
          r.quantity AS recipe_quantity,
	      sum(o.quantity) AS order_quantity,
          ing.ing_weight,
          ing.ing_price
    
       FROM 
	      orders o
	      LEFT JOIN item i ON o.item_id = i.item_id
          LEFT JOIN recipe r ON i.sku = r.recipe_id
          LEFT JOIN ingredient ing ON ing.ing_id = r.ing_id
    
       GROUP BY 
	      o.item_id,
	      i.sku,
          i.item_name,
          r.ing_id,
          r.quantity,
          ing.ing_name,
          ing.ing_weight,
          ing.ing_price) s1;
 
   
If you have any questions or need further assistance, please feel free to contact the project maintainer at vanburen.kyle@yahoo.com.


   

   
