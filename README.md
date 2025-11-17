<img width="1790" height="620" alt="image" src="https://github.com/user-attachments/assets/68390f79-e5e9-44ef-99c3-9133323f1c00" />


# Revenue Performance Analysis with Python

## 1. Project Overview
This project analyzes customer spending patterns for **ProWidget Systems** in the United Kingdom using a customer transactions dataset.
The focus is on **city-level performance**: answering where revenue is concentrated, which cities generate the most and the least revenue, and which locations may be underserved relative to their potential.

**Objective:**  
Understand where customers spend the most and explore opportunities for deeper insights into geographic and demographic spending trends.

**Dataset Used:**  
- Customer transaction dataset filtered by:
  - `company_id` - unique identifier for each customer
  - `address` - customer address (raw text)
  - `total_spend` - total amount spent by the customer

---

## 2. Problem Statement
The initial business question from the board was:  
> **Which cities in the UK have the highest customer spending, and which are underserved compared to London?**

To answer this question, we explore several sub-question:
- How does spending vary by city and region?
- How concentrated is spending in London versus the rest of the UK?
- What strategies could help better serve low-spending areas?

---

## 3. Methodology
The analysis follows a straightforward, results-oriented workflow:
1. **Data Understanding** – reviewed customer address formats, identified inconsistencies, and missing values.  
2. **Data Cleaning** – standardized addresses, removed duplicates, and normalized city names.  
3. **City Identification** – matched addresses with the official [UK Cities List](https://www.gov.uk/government/publications/list-of-cities/list-of-cities-html).  
4. **Exploratory Analysis** – calculated total spending by city, visualized distributions, and identified top/bottom performers.
5. **Feature Engineering (City-Level Metrics)** - Computed key city-level indicators — company count, total spend, spend per company, and market/revenue shares.
6. **Underserved Cities Framework** Built a composite underserved score by combining company share, spend share, and spend per company to identify cities where customer presence exceeds revenue contribution.
7. **Communication of Findings** – visualized results with Matplotlib and Plotly for stakeholder presentations.

---

## 4. Data Exploration and Preparation
- Checked for missing or misformatted addresses.  
- Removed null and duplicate entries.  
- Grouped data by `city` and aggregated `total_spend`.  
- Identified anomalies such as PO Boxes or incomplete city names.  
- Created a clean dataset ready for analysis.

---

## 5. Analysis and Results

### 5.1 Revenue Concentration by City
- **Top 10 Cities by Total Spend** – identifies where customers spend the most.
<p align="center">
  <img src="docs/Top 10 Cities by Spends and Companies.png" width="800" alt="Top 10 Cities by Spends and Companies">
</p>
The group OTHER is at the top in term of spendings and transactions.
It is followed by LONDON, whose spending and transactions are +10 times more than its closest follower city<br>  
We were clearly identify in the dataset the primary UK cities, and the rest such as the Isle of Man and the Overseas <br>  Territories were grouped under OTHER.This creates a slight distortion, since these locations appear unusually large in the charts compared to what we would expect.<br>   
Nevertheless, the OTHER category remains an interesting area for further analysis, as breaking it down could reveal meaningful patterns once the underlying cities are properly classified.<br>

- **London vs Other vs Rest** – shows the dominance of London compared to other areas.  
<p align="center">
  <img src="docs/London focus.png" width="600" alt="Pie Chart London vs Other vs Rest">
</p>
The customers spend the most in bigger cities since there are generally more customers in larger cities, and London generates nearly as much income as all the other big cities combined.

- **City-Level Performance Metrics** - To go beyond simple totals, three key indicators were computed for each city:

Company Count (company_count)<br>
Number of unique company_id in the city.<br>
→ Measures market size in terms of existing customers.<br>

Total Spend (total_spend)<br>
Sum of total_spend in the city.<br>
→ Measures revenue contribution.<br>

Spend per Company (spend_per_company)<br>
total_spend / company_count.<br>
→ Measures average engagement / adoption level per company.<br>

From these, two shares were derived:<br>

company_share = company_count / total_companies<br>

spend_share = total_spend / total_spend_all_cities<br>

These allow us to compare a city’s market size with its revenue contribution.<br>

- **Market Distribution**: shows the lowest city on the KPIs extracted for our analysis.
<p align="center">
  <img src="docs/Market Distribution.png" width="600" alt="Market Distribution">
</p>
**On the left**, cities have a very small company base, so naturally they contribute little to total revenue.<br> 
**On the middle**, these cities produce extremely low revenue and may be weak markets, inactive, or underserved, epending on how many companies they contain.<br>
**On the right**, these cities show low adoption, weak usage, and true `underserved potential`, even when they have companies present.<br>
When the same cities appear repeatedly across the three charts, the pattern is clear, they are the most underserved, either because they lack reach, awareness, or proper customer activation.<br>
Cities consistently showing up across all three metrics:<br>
`ST DAVIDS`, `BRIGHTON & HOVE`, `ST ASAPH` and `RIPON`

---

## 6. Conclusion
Our analysis confirms that **London customers account for the majority of total spending**, representing a substantial share of overall revenue across the United Kingdom.  

However, when comparing spending across all cities, we observe that **several regional cities and towns remain underserved**, showing significantly lower total spend despite moderate population levels.  

## 7. Recommendations

- **Enhance city identification:**  
  - Use UK postcode data to identify cities/towns precisely.  
  - Ensure all addresses contain valid postcodes.

- **Augment with demographics and dates:**  
  - Combine spending data with population and saisonality.  
  - Identify underserved cities based on spending per capita.
 
- **Differentiate customer types:**  
  - Compare spending between business and private addresses. 

- **Collaborate with stakeholders:**  
  - Evaluate which enhancements provide tangible business value.  
  - Prioritize work aligned with strategic goals.

---

## 8. Appendix
**Tools and Libraries:**
- Python (`pandas`, `matplotlib`, `plotly`)
- Jupyter Notebook for exploratory analysis [Notebook link](https://github.com/Anaclet12/UK-Customer-Spending-Analysis/blob/main/scripts/UK%20Customer%20Spending%20Analysis.ipynb)
- GOV.UK dataset for the official list of cities

**Key Resources:**
- [UK Cities List (GOV.UK)](https://www.gov.uk/government/publications/list-of-cities/list-of-cities-html)
- [Plotly Documentation](https://plotly.com/python/)
- [Pandas API Reference](https://pandas.pydata.org/docs/)

---

✳️ *Author:* Anaclet Sado Fokam  
📅 *Date:* November 2025  
💼 *Project Type:* Data Analytics / Business Insights  
