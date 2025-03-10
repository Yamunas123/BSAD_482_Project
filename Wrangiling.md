# Wrangling.md

## **Data Wrangling Process**

### **1. Data Acquisition**
The datasets used for this analysis were obtained from Kaggle and include:
- **US Domestic Flight Delays Dataset** ([Source](https://www.kaggle.com/datasets/giovamata/airlinedelaycauses))
- **USA Airport Dataset** ([Source](https://www.kaggle.com/datasets/flashgordon/usa-airport-dataset))
- **Airline Passenger Satisfaction Dataset** ([Source](https://www.kaggle.com/datasets/teejmahal20/airline-passenger-satisfaction))

---

### **2. Data Cleaning & Preprocessing**

The following preprocessing steps were performed using **Tableau Prep**:

#### **Handling Missing Values**
- **Flight Delay Dataset:**
  - Missing values in `ArrTime` and `DepTime` for canceled flights were left as null since they are not applicable.
- **Passenger Satisfaction Dataset:**
  - Null values in passenger feedback fields were removed to avoid misleading analysis.
  
#### **Removing Duplicates**
- Identified and removed duplicate flight records where `FlightNum`, `Origin`, `Dest`, and `DepTime` matched across multiple rows.

#### **Standardizing Formats**
- **Dates**: Converted all date formats to `YYYY-MM-DD` for consistency.
- **Airline Codes**: Standardized airline carrier names using a lookup reference to ensure uniformity in merging.
- **Numeric Fields**: Converted delay times to integer format and normalized passenger satisfaction scores between 0 and 5.

#### **Filtering Unnecessary Data**
- Removed irrelevant columns such as `TailNum`, `TaxiIn`, `TaxiOut`, and `CancellationCode`, which were not needed for analysis.
- Filtered out data for flights with extreme outliers (delays greater than 12 hours) to maintain data quality.

---

### **3. Data Integration & Transformation*

#### **Pivoting & Aggregations**
- **Flight Delay Data:** Pivoted different delay types (`CarrierDelay`, `WeatherDelay`, `NASDelay`, etc.) to analyze their distribution across airlines.
- **Satisfaction Scores:** Aggregated scores by airline and airport to identify patterns.
- **Flight Route Analysis:** Created a derived field combining `Origin Point` and `Destination point` to track the most traveled and most delayed routes.

---

### **4. Exploratory Data Analysis & Visualization**

The following visualizations were created in **Tableau** to analyze flight performance, delays, and customer satisfaction:

#### **1. Flight Routes & Airport Network Mapping**
![](https://github.com/Yamunas123/BSAD_482_Project/blob/6e4d4ca0b0ca402682660bbd4709de72e5499998/Images/Routs.png)
- This visualization shows the **most frequently traveled routes** and highlights **airports with the highest passenger traffic**.
- The **line thickness** represents the volume of flights on each route.
- Darker nodes indicate **major hub airports** (e.g., JFK, LAX), where delays could have a cascading effect on the network.

#### **2. Airports with the Worst Delays**
![](https://github.com/Yamunas123/BSAD_482_Project/blob/14cc4826afdfb8ae0ab2c3cd978a2842854f3b33/Images/Airport1.png)
- Displays which **airports experience the longest average arrival delays**.
- Uses a **bubble map** where larger, darker bubbles represent **higher average delay times**.
- Helps identify **problematic airports** that contribute to systemic flight delays.

#### **3. Delay Types Across Airlines**
![](https://github.com/Yamunas123/BSAD_482_Project/blob/93be44a4ffeb538d7b678a01029fc40668002c42/Images/Airline1.png)
- A **stacked bar chart** that categorizes delay causes (**Carrier, Weather, NAS, Late Aircraft, and Security Delays**) per airline.
- Allows comparison of **which airlines suffer most from delays** and what type of delay affects them the most.
- Airlines with a high share of **carrier delays** may need to improve operational efficiency, while those with **weather-related delays** may need to optimize scheduling strategies.

#### **4. Correlating Satisfaction Scores with Delays**
![](https://github.com/Yamunas123/BSAD_482_Project/blob/bb109d4a5ab78c8d5cb75c9174fbf657bc0d0d3e/Images/relation.png)
- A **scatter plot with trend lines** that examines how **departure delays impact customer satisfaction**.
- Each dot represents a flight’s delay time and its corresponding **passenger satisfaction score**.
- The trend lines indicate how satisfaction changes for different factors (e.g., seat comfort, baggage handling, inflight service).
- Helps airlines determine **which service aspects mitigate the negative effects of delays**.
