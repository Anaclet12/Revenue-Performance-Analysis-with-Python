<img width="1790" height="620" alt="image" src="https://github.com/user-attachments/assets/68390f79-e5e9-44ef-99c3-9133323f1c00" />


# UK Customer Spending Analysis

## 1. Project Overview
This project analyzes customer spending patterns across the company ProWidget Systems in the United Kingdom to identify cites with the highest and lowest spending levels.  
It also aims to uncover potential underserved cities based on total revenue and spending behavior.

**Objective:**  
Understand where customers spend the most and explore opportunities for deeper insights into geographic and demographic spending trends.

**Dataset Used:**  
- Customer transaction dataset filtered by:
  - `city`
  - `address`
  - `total_spend`

---

## 2. Problem Statement
Our main business question:  
> **Which cities in the UK have the highest customer spending, and which are underserved compared to London?**

Additional sub-questions:
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
5. **Communication of Findings** – visualized results with Matplotlib and Plotly for stakeholder presentations.

---

## 4. Data Exploration and Preparation
- Checked for missing or misformatted addresses.  
- Removed null and duplicate entries.  
- Grouped data by `city` and aggregated `total_spend`.  
- Identified anomalies such as PO Boxes or incomplete city names.  
- Created a clean dataset ready for analysis.

---

## 5. Analysis and Results

### Key Visualizations
- **Top 20 Cities by Total Spend** – identifies where customers spend the most.  
- **Bottom 20 Cities by Total Spend** – highlights underperforming regions.  
- **Pie Chart (London vs Other vs Rest)** – shows the dominance of London compared to other areas.  
- **Interactive Bar Charts** – hover-enabled visualization of spending by city using Plotly.

### Example Insight
> London accounts for over 20% of total customer spending, while the rest 75 big cities (24%) demonstrate moderate growth potential.

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
- Python (`pandas`, `plotly`)
- Jupyter Notebook for exploratory analysis [Notebook](https://github.com/Anaclet12/UK-Customer-Spending-Analysis/blob/main/scripts/UK%20Customer%20Spending%20Analysis.ipynb)
- GOV.UK dataset for the official list of cities

**Key Resources:**
- [UK Cities List (GOV.UK)](https://www.gov.uk/government/publications/list-of-cities/list-of-cities-html)
- [Plotly Documentation](https://plotly.com/python/)
- [Pandas API Reference](https://pandas.pydata.org/docs/)

---

✳️ *Author:* Anaclet Sado Fokam  
📅 *Date:* November 2025  
💼 *Project Type:* Data Analytics / Business Insights  
