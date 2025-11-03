# 🏙️ UK Customer Spending Analysis

## 1. Project Overview
This project analyzes customer spending patterns across the United Kingdom to identify regions with the highest and lowest spending levels.  
It also aims to uncover potential underserved cities based on total revenue and spending behavior.

**Objective:**  
Understand where customers spend the most and explore opportunities for deeper insights into geographic and demographic spending trends.

**Dataset Used:**  
- Customer transaction dataset including:
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
> London accounts for over 40% of total customer spending, while several medium-sized cities demonstrate moderate growth potential.

---

## 6. Next Steps
After presenting the results, stakeholders may request deeper analysis or more accurate data matching.  
Potential directions include:

- **Enhance city identification:**  
  - Use UK postcode data to identify cities/towns precisely.  
  - Ensure all addresses contain valid postcodes.

- **Expand geographic coverage:**  
  - Add towns above a certain population threshold.  
  - Address cases where city names are missing in addresses.

- **Explore geocoding solutions:**  
  - Integrate third-party APIs (e.g., Google Maps) for better city identification.  
  - Assess privacy and compliance implications before data sharing.

- **Augment with demographics:**  
  - Combine spending data with population and demographic data.  
  - Identify underserved cities based on spending per capita.

- **Collaborate with stakeholders:**  
  - Evaluate which enhancements provide tangible business value.  
  - Prioritize work aligned with strategic goals.

---

## 7. Further Analysis Opportunities
Once the foundation is established, more advanced analyses can provide deeper insights:

- **Granular geographic analysis:**  
  - Drill down into sub-city regions (boroughs, districts, or regional clusters).  

- **Differentiate customer types:**  
  - Compare spending between business and private addresses.  

- **Integrate demographic data:**  
  - Add population or income data to compute **spending per capita**.  
  - Explore relationships between wealth and spending intensity.  

---

## 8. Conclusion
This project provides a foundational understanding of customer spending across UK cities.  
The findings highlight regional disparities and potential areas for business focus.  
Future work should combine enriched geographic data and demographic insights to support targeted decision-making.

---

## 9. Appendix
**Tools and Libraries:**
- Python (`pandas`, `matplotlib`, `plotly`, `numpy`, `seaborn`)
- Jupyter Notebook for exploratory analysis
- GOV.UK dataset for the official list of cities

**Key Resources:**
- [UK Cities List (GOV.UK)](https://www.gov.uk/government/publications/list-of-cities/list-of-cities-html)
- [Plotly Documentation](https://plotly.com/python/)
- [Pandas API Reference](https://pandas.pydata.org/docs/)

---

✳️ *Author:* Your Name  
📅 *Date:* November 2025  
💼 *Project Type:* Data Analytics / Business Insights  
