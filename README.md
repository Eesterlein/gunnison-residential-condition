# gunnison-residential-condition
# Residential Improvements – Cyberpunk Dashboard  

 **Live Dashboard**: [View Here](https://eesterlein.github.io/gunnison-residential-condition/)  
** Or copy & paste link into browser: https://eesterlein.github.io/gunnison-residential-condition/**


This project is an interactive data dashboard built with **HTML, CSS, JavaScript, Plotly.js, and PapaParse**.  
It visualizes assessor data on **residential improvements in Gunnison County**.  

---

##  What the Code Does  

###  Styling & Layout  
- Neon cyberpunk-inspired theme using CSS gradients and variables.  
- Dashboard structure:  
  - **KPI Cards** – total properties, median value, average square footage, most common condition, median year built.  
  - **Tabbed Navigation** – Condition, Quality, Improvements, Size & Value, Economic Areas.  
  - **Responsive Design** – charts resize automatically when switching tabs or resizing the window.  

###  Data Handling  
- Loads data directly from `RI_v2 - Sheet1.csv` with **PapaParse**.  
- Helper functions calculate **median, average, unique values**.  
- Economic Area codes are **cleaned** (trimmed, leading zeros removed, blanks dropped).  

###  Visualizations (Powered by Plotly.js)  
- **Condition Tab**  
  - Pie chart of overall property condition distribution.  
  - Box plot of market value by condition (excludes Minimum & Salvage).  

- **Quality Tab**  
  - Bar chart of construction quality distribution.  
  - Grouped bar chart of bedroom counts by condition (restricted to **1–5 bedrooms**, excluding Minimum & Salvage).  

- **Improvements Tab**  
  - Treemap of top residential improvement types.  

- **Size & Value Tab**  
  - Dual-axis line chart comparing average **square footage vs. market value** by condition.  

- **Economic Areas Tab**  
  - Grouped bar chart of condition by **Economic Area (1, 2, 6, 8 only)**.  
  - Axis shows only real codes present in the dataset (phantom codes removed).  

---

##  Dashboard Sections  

### Condition Analysis  

#### Condition Breakdown (Pie Chart)  
- **Average condition** dominates: ~69% of homes.  
- **Good condition** makes up ~14%.  
- **Excellent + Very Good** together: ~12%.  
- Less than 5% fall into **Below Average, Minimum, or Salvage**.  

➡ **Insight**: Most Gunnison homes fall in the “middle” condition category, with relatively few at the extreme ends.  

#### Market Value by Condition (Box Plot)  
- **Very Good** homes show the **highest median values** and the widest spread.  
- **Excellent** homes are **not always more valuable** than Very Good — size, location, and style also play roles.  
- **Average & Below Average** homes are clustered at the lower end.  

➡ **Insight**: The biggest jump in value is from **Average → Good → Very Good**, not from **Very Good → Excellent**.  

---

### Quality & Bedrooms Analysis  

#### Quality Distribution  
- Most homes are rated **Fair** or **Average** quality.  
- Few are in the **Excellent** or **Very Good** categories.  

➡ **Insight**: Gunnison housing stock leans toward **mid-range construction standards** rather than luxury builds.  

#### Bedrooms by Condition  
- Majority are **2- and 3-bedroom homes in Average condition**.  
- Very few **Excellent/Very Good homes** across all bedroom sizes.  
- **Below Average** homes tend to be smaller (1–2 bedrooms).  
- Code was adjusted to **show only up to 5 bedrooms** for clarity.  

➡ **Insight**: Gunnison homes are typically **moderately sized** and mid-quality, with limited extremes.  

---

### Top Improvement Types (Treemap)  
- **Single-Family Dwellings** are the most common improvement type.  
- Other large categories: **Conventional builds, Multiple Units, Duplexes**.  
- Smaller shares: **Cabins, Log Homes, Manufactured Housing, A-Frames**.  

➡ **Insight**: The county’s housing is dominated by **traditional single-family dwellings**, with a mix of multi-unit and alternative housing types.  

---

### Average Square Footage & Value by Condition  

- **Very Good** homes: ~2,100 sq ft, ~$2M average value → peak of dataset.  
- **Excellent** homes: slightly smaller and lower value than Very Good.  
- **Good → Average → Below Average**: consistent downward trend in both size and value.  
- Sharpest drop is **Good → Average**.  

➡ **Insights**:  
- **Size and value track closely** across all conditions.  
- The **“Excellent vs. Very Good” anomaly** suggests:  
  - Assessors may reserve “Excellent” for smaller high-quality homes.  
  - Market favors size more than incremental condition upgrades.  
- **Takeaway**: Condition influences value, but **size is a stronger driver**.  

---

### Condition by Economic Area  

- Chart compares **condition distribution** across Economic Areas **1, 2, 6, and 8**.  
- **Average condition dominates all areas**.  
- **Excellent/Very Good homes** cluster in **Area 1 (City of Gunnison)** and **Area 6 (Upper East River Valley & Crested Butte area)**.  
- **Below Average/Minimum/Salvage homes** appear more frequently in **Areas 1 & 8** (Gunnison proper and broader rural zones).  

➡ **Insights**:  
- High-value, higher-condition homes are concentrated in **Gunnison & Crested Butte**.  
- Lower-condition housing is more common in **rural and older housing stock areas**.  

 **Reference Map**: [Gunnison County Economic Areas Map](https://www.gunnisoncounty.org/DocumentCenter/View/2101/Economic_Areas_Map?bidId=)  

---

##  How to Use  

1. Clone or download this repository.  
2. Place `index.html` and `RI_v2 - Sheet1.csv` in the same folder.  
3. Open `index.html` in a web browser.  
4. Use the tabs to explore different aspects of the data.  

---
