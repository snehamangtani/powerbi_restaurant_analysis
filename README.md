
# Zomato Restaurant Analysis-Dashboard

Zomato offers a comprehensive set of services, facilitating restaurant search and discovery across various countries. Operating globally, Zomato provides detailed restaurant information and customer reviews.

## Objective

The primary goal is to uncover hidden anomalies in business data, leading to a thorough analysis for an accurate assessment of Zomato's business performance.

## Power BI Report Highlights

The Power BI report aims to:

#### 1. Analyze Restaurant Distribution:
Examine the total number of restaurants globally, categorized by continents, countries, and cities.

#### 2. Identify Top Performers:
Evalute top-performing restaurants based on criteria such as average customer ratings, minimum average cost, and the variety of cuisines offered.

#### 3. Navigation Capabilities:
Provide a seamless experience for users to navigate through the report. Enable them to view information globally or dive into granular details as needed.

#### 4. Filters for In-Depth Insights:

Incorporate filters based on geographic dimensions, restaurant offers, and rating colors to refine and focus the displayed information.

## Steps followed

### Data Import
#### 1. Import Data
- Import Data from the provided Excel files (Africa, Asia, , Europe, NAM, SAM, Oceania, Country-Code, Fact Table) into Power BI.

### Data Transformations
#### 1. Correct Values in the "City" Column:
- Remove the word "city" from every city name.
- Correct "Sí£o Paulo" to "São Paulo."
- Correct "Cedar Rapids/Iowa City" to "Cedar Rapids."
- Correct "ÛÁstanbul" to "Istanbul."
#### 2. Remove Unused Columns:
- Eliminate columns that are not used in the analysis.
#### 3. Separate Columns for Restaurant Name and Address:
- Create separate columns for "Restaurant Name" and "Restaurant Address."
#### 4. Create Cuisine List Table:
- Generate a separate table containing the list of cuisines served by each restaurant.
#### 5. Ensure Unique Values in "Country-Code" Table:
- Ensure the "Country-Code" table contains only unique and non-blank values.

### Data Modeling
#### 1. Model Data:
- Structure data according to reporting requirements.
#### 2. Establish Relationships:
- Set up relationships with appropriate "Cardinality" and "Cross-filter direction" for accurate aggregations.

### Data Manipulations
#### 1. Categorize Geographic Columns:
- Review the list of geographic columns and categorize them appropriately.
#### 2. Create User-Defined Hierarchy:
- Establish a user-defined hierarchy with all geographical dimensions.
#### 3.Group Countries into Continents:
- Group countries into their respective continents.
###  DAX Queries 
#### 1. Create "Rating Color" Column:

- Add a "Rating Color" column following the specified convention.
       
        Rating Color = 
        SWITCH (
            TRUE (),
            [Aggregate rating] > 4.5, "Dark Green",
            [Aggregate rating] >= 4, "Green",
            [Aggregate rating] >= 3.5, "Yellow",
            [Aggregate rating] >= 2.5, "Orange",
            [Aggregate rating] >= 1.8, "Red",
            [Aggregate rating] >= 0, "White"
        )
#### 2. Create Measures:

- In appropriate tables, create the following measures:

    a. Restaurant Count

        Restaurant Count = COUNTA('All Restaurants'[Restaurant ID])

    b. Average Cost
    
        Aveage Cost = AVERAGE(KPIs[Average Cost for two])

    c. Average Rating

        Average Rating = AVERAGE(KPIs[Aggregate rating])

    d. Cuisine Count

        Cuisine Count = COUNTA('All Restaurants'[Cuisines])
#### 3. Add "Continent" Column in "Country Code" Table:
- Create a new column called "Continent" in the "Country Code" table using the provided convention.

        Continent = SWITCH('Country Master'[Country],
        "South Africa","Africa",
        "Phillipines","Asia",
        "Singapore","Asia",
        "UAE","Asia",
        "India","Asia",
        "Indonesia","Asia",
        "Qatar","Asia",
        "Sri Lanka","Asia",
        "Turkey","Asia",
        "United Kingdom","Europe",
        "United States","North America",
        "Canada","North America",
        "Australia","Oceania",
        "New Zealand","Oceania",
        "Brazil","South America")
### Data Visualization
#### 1. Create Visuals:
- Develop the following visuals in the report:

    a. Card visual (Restaurant Count, Total Cities in the Restaurants, Total Cuisines Served, Locatality)

    b. Map visual (Restaurant Count on Geography hierarchy)

    c.  A pie chart is configured with the legend representing different rating categories, the values displaying the count of Restaurant IDs, and tooltips providing the maximum aggregated rating for each category.

    d. A map chart is configured to display restaurant data based on country locations, with the legend representing countries, and the bubble sizes corresponding to the count of Restaurant IDs in each country.

## Insights
- Restaurant Count by Country: There are a total of 9551 restaurants in the dataset. India has the highest number of restaurants.

- Cuisines: There are 1826 cuisine served by restaurants also varies by country. Indian restaurants serve the most cuisines, followed by Brazilian and Turkish restaurants.

- A pie chart is configured with the legend representing different rating categories, the values displaying the count of Restaurant IDs, and tooltips providing the maximum aggregated rating for each category.

- A map chart is configured to display restaurant data based on country locations, with the legend representing countries, and the bubble sizes corresponding to the count of Restaurant IDs in each country.

- There are restaurants in a total of 140 City and 1208 locality  spanning various country.

- Through Drill Down, Uncover hidden trends and patterns by,
    
    - Examining Individual Dish Performance
    - Identifying Customer Segments
    - Unveiling Trends & Patterns
