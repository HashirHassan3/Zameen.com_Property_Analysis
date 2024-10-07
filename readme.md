
### **Zameen.com Property Listing Data (2019-2020) Analysis and Dashboard**

---

#### **Overview**
This project involved cleaning and transforming property listing data from Zameen.com (2019-2020), sourced from Kaggle, and building a dashboard for insightful analysis. The focus was on data cleaning, outlier removal, and data visualization to draw actionable insights about property listings.

---

#### **Data Cleaning and Transformation**

- **Imported CSV to Power Query:**  
  Cleaned and prepared the dataset for analysis.

- **Handled Missing Values:**  
  Replaced missing values (25%) with "Unknown."

- **Fixed Data Inconsistencies:**  
  Corrected formatting, applied proper capitalization, and trimmed unnecessary spaces.

- **Removed Irrelevant Columns:**  
  Deleted unnecessary columns such as longitude, latitude, page URL, agent, and location ID.

- **Extracted New Columns:**  
  Created two new columns from the area field: area_size and area_unit. Corrected data types and applied proper formatting.

- **Grouped Area Ranges:**  
  Grouped properties into ranges (e.g., 0-3 Marla, 3-6 Marla, 1-4 Kanal) using pivot tables. Created lower and upper limits for both Marla and Kanal and assigned each row to the appropriate range.

---

#### **Outlier Detection and Removal**

- **Outlier Detection:**  
  Calculated mean, standard deviation, and Z-Score for property prices using Power Pivot. Defined outliers as values with Z-Scores > 3 or < -3.
  
- **Outlier Removal:**  
  Removed outliers, reducing the dataset from 191,394 rows to 187,887 rows.

---

**Formulas Used in Power Pivot:**

- **Z-Score:**
```excel
IF('Property'[StdDev(Price)] <> 0, ('Property'[price] - 'Property'[Mean(Price)]) / 'Property'[StdDev(Price)], 0)
```
- **Outlier:**
```excel
IF('Property'[ZScore(Price)] > 3 || 'Property'[ZScore(Price)] < -3, "Yes", "No")
```
- **Mean and Std Dev:**
```excel
CALCULATE(AVERAGE('Property'[baths]), ALLEXCEPT('Property', 'Property'[areaRanges]))
CALCULATE(STDEVX.P('Property', 'Property'[baths]), ALLEXCEPT('Property', 'Property'[areaRanges]))
```

---

#### **Dashboard (Zameen.com Property Analysis)**

The dashboard provides a detailed view of the property listings and trends:

- **KPIs and Metrics:**
  - Total Number of Listings
  - Most Expensive House Listed

- **Visualizations:**
  - **Pie Chart:** Percentage of Listings for Sale vs Rent
  - **Line Chart:** Property Listings by Month
  - **Bar Chart:** Property Listings by City
  - **Double-Deck Donut Chart:** Average Property Size by Marla and Kanal in each city
  - **Donut Chart:** Percentage of Listings by Property Type
  - **Big Cards:**
    - Median House Price by City (Marla)
    - Median House Price by City (Kanal)
  - **Donut Chart:** Percentage of Listings by Unit Type (Marla vs Kanal)

---

#### **Descriptive Analysis / Key Insights**

- **Listing Trends by Month:**  
  June and July had the highest number of property listings, indicating seasonal trends.
  
- **Sale vs Rent Distribution:**  
  66% of the properties were listed for sale, while 34% were for rent.

- **Median House Prices by City:**
  - *Faisalabad* had the lowest median house price in Marla units.
  - *Karachi* had the lowest median house price in Kanal units.

- **Property Type Distribution:**  
  Houses had the highest percentage of listings, followed by flats and portions, which were second and third, respectively.

---

#### **Key Accomplishments**

- **Data Cleaning:**  
  Applied a structured approach to handle missing data, remove irrelevant fields, and fix inconsistencies.

- **Outlier Detection:**  
  Implemented Z-Score-based outlier removal to improve the accuracy of analysis.

- **Dashboard Creation:**  
  Designed an interactive dashboard for property analysis, focusing on key metrics and insights using charts and visual representations.

---