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

###  Data Handling  
- Loads data directly from `RI_v2_sanitized.csv` with **PapaParse**.  
- Helper functions calculate **median, average, unique values**.   

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
  - Grouped bar chart of condition by **Economic Area (1, 2, 6, 8)**.
---

##  Data Transparency  

This dataset originates from the **Gunnison County Assessor’s Office** database.  
It was prepared in response to a formal internal request from leadership for *“a list of the current condition on every residential improvement in the county, including any additional fields that could provide context for analysis.”*  

While the initial request focused on a simple tabular list, I extended the work by curating fields that would be most relevant for visualization and deeper analysis. These include:  

- **EXT CONDITION** – Exterior condition rating of the improvement (Excellent → Salvage).  
- **IMPQUALITY** – Construction quality rating.  
- **IMPDESCRIPTION** – Type of improvement (e.g., Single-Family Dwelling, Duplex, Cabin).  
- **IMPNETSF** – Net square footage.  
- **BEDROOMCOUNT** – Number of bedrooms.  
- **AYB** – Actual year built.  
- **MaxOfCURR ACT** – Current actual market value.  
- **ECONOMICAREACODE** – Assessor-defined economic area code for neighborhood grouping.  

### Primary Improvements Only  
This dataset is limited to **primary residential improvements**.  
In assessor terminology, the *primary improvement* is the **main dwelling or structure on a property account**, as opposed to secondary structures (garages, sheds, ADUs, barns, etc.). Restricting to primary improvements avoids duplication, ensures consistency across parcels, and provides the clearest picture of the housing stock as experienced by occupants. Names, account numbers, and property addresses have been redacted from this dataset to protect privacy. 

### Limitations  
- **Not comprehensive of all structures** – Outbuildings and secondary units are excluded.  
- **Condition and quality are assessor-derived** – These ratings reflect professional judgment within standard guidelines but may not perfectly align with buyer perceptions.  
- **Point-in-time snapshot** – Values and conditions reflect the moment the dataset was pulled and will evolve with future assessments.   

By acknowledging these parameters, the dashboard should be understood as an **analytical tool** that provides meaningful insight into the county’s housing stock, rather than as an exact valuation or real estate listing resource.  

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

## Contextual Storytelling: Affordability & Market Dynamics

Gunnison County faces a pronounced **housing affordability crisis**, driven by a shortage of units for low- and moderate-income households and local workers. The **median listing price** in Gunnison hovers around **$1.2 million**, while the **average home value** is approximately **$705,000**, both significantly higher than the U.S. median.  
([Zillow](https://www.zillow.com/home-values/2313/gunnison-county-co/?utm_source=chatgpt.com))

In contrast, the **national median home price** sits near **$462,000**, with a Zillow-estimated **average U.S. home value of about $368,600**.  
([Forbes](https://www.forbes.com/advisor/mortgages/real-estate/median-home-prices-by-state/?utm_source=chatgpt.com), [Zillow](https://www.zillow.com/home-values/102001/united-states/?utm_source=chatgpt.com))

This stark difference highlights how even **average-quality homes in Gunnison are exceptionally expensive**—a far cry from affordability.

### What This Means

- **Local housing doesn’t meet the needs of all residents**, particularly workers and families with moderate incomes.  
- The **price premium** on average-condition homes underlines the lack of mid-market housing—whether rental or owner-occupied.  
- To bridge this affordability gap, **public and nonprofit interventions are critically needed**—such as deed-restricted housing, subsidized workforce units, or incentives for lower-cost developments.

---

##  How to Use  

1. Clone or download this repository.  
2. Place `index.html` and `RI_v2 - Sheet1.csv` in the same folder.  
3. Open `index.html` in a web browser.  
4. Use the tabs to explore different aspects of the data.  

---
