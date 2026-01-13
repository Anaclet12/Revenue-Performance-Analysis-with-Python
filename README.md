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

### 5.1 **Top 10 Cities by Total Spend**:
Identifies where customers spend the most.
<p align="center">
  <img src="docs/Top 10 Cities by Spends and Companies.png" width="800" alt="Top 10 Cities by Spends and Companies">
</p>
The group OTHER is at the top in term of spendings and transactions.
It is followed by LONDON, whose spending and transactions are +10 times more than its closest follower city<br>  
We were clearly identify in the dataset the primary UK cities, and the rest such as the Isle of Man and the Overseas <br>  Territories were grouped under OTHER.This creates a slight distortion, since these locations appear unusually large in the charts compared to what we would expect.<br>   
Nevertheless, the OTHER category remains an interesting area for further analysis, as breaking it down could reveal meaningful patterns once the underlying cities are properly classified.<br>

### 5.2 **London vs Other vs Rest**:
Shows the dominance of London compared to other areas.  
<p align="center">
  <img src="docs/London focus.png" width="600" alt="Pie Chart London vs Other vs Rest">
</p>
The customers spend the most in bigger cities since there are generally more customers in larger cities, and London generates nearly as much income as all the other big cities combined.<br>

### 5.3 **City-Level Performance Metrics**:
To go beyond simple totals, three key indicators were computed for each city:

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

### 5.4 **Market Distribution**:
Shows the lowest city on the KPIs extracted for our analysis.
<p align="center">
  <img src="docs/Market Distribution.png" width="600" alt="Market Distribution">
</p>
**On the left**, cities have a very small company base, so naturally they contribute little to total revenue.<br> 
**On the middle**, these cities produce extremely low revenue and may be weak markets, inactive, or underserved, epending on how many companies they contain.<br>
**On the right**, these cities show low adoption, weak usage, and true `underserved potential`, even when they have companies present.<br>
When the same cities appear repeatedly across the three charts, the pattern is clear, they are the most underserved, either because they lack reach, awareness, or proper customer activation.<br>
Cities consistently showing up across all three metrics:<br>
`ST DAVIDS`, `BRIGHTON & HOVE`, `ST ASAPH` and `RIPON`

### 5.5 **Underserved Score**
<p align="center">
  <img src="docs/Company Share vs Spend Share.png" width="600" alt="Company Share vs Spend Share">
</p>
This scatter plot shows the trend of the underserved since it visualize the company_share and spend_share together.  
Most cities cluster around the bottom-left corner (very small company and spend shares), confirming they are micro-markets.
London and OTHER lie along the diagonal, where revenue is broadly proportional to market size.
No large city falls far below the diagonal, indicating that there is no major region where revenue dramatically lags behind the size of the customer base.
The highest underserved scores therefore relate to very small cities with low absolute revenue, which are opportunities but not immediate priority markets.
<p align="center">
  <img src="docs/Underserved Score.png" width="600" alt="Underserved Score">
</p>
The underserved score is a weighted combination of our three metrics normalized.<br>
The metrics are normalized so they are comparable on the same scale, preventing any one measure from dominating the score due to differences in units or magnitude.<br>
Company share receives the highest weight (0.4) because a city with many companies but low revenue is the strongest signal of being underserved.<br>
Spend share and spend per company each receive a weight of 0.3, since together they show how effectively the market potential is being converted into revenue and customer engagement.<br>
- Most cities cluster around the bottom-left corner (very small company and spend shares), confirming they are micro-markets.<br>
- London and OTHER lie along the diagonal, where revenue is broadly proportional to market size.<br>
- No large city falls far below the diagonal, indicating that there is no major region where revenue dramatically lags behind the size of the customer base.<br>
- The highest underserved scores therefore relate to very small cities with low absolute revenue, which are opportunities but not immediate priority markets.

---

## 6. Conclusion
This project shows that:
- Revenue is **highly concentrated** in **LONDON** and the **OTHER** category, but the **REST OF CITIES** still contributes a meaningful share.
- A set of cities (**ST DAVIDS, BRIGHTON & HOVE, ST ASAPH, RIPON, NEWPORT**, etc.) consistently underperform across multiple metrics, indicating **weak adoption and engagement** despite the presence of some customers.
- There is **no major city** where revenue is dramatically out of line with its market size; underservice is mainly a **long-tail phenomenon**, not a large structural problem.
- London performs broadly as expected, though there is still room to improve **spend per company**.

These findings provide a **data-driven view of geographic performance** and a solid foundation for the board to prioritize commercial actions.
 

## 7. Recommendations

### 7.1 Targeted Activation in the Most Underserved Cities

**Cities concerned:** ST DAVIDS, BRIGHTON & HOVE, ST ASAPH, RIPON, and a small group of similar towns.

These locations **do have customers**, but they show **very low spend and weak engagement**.

**Suggested actions:**
- **Sales** → re-engage existing accounts with targeted outreach.  
- **Customer Success** → run light onboarding or usage review sessions to boost product adoption.  
- **Marketing** → deploy low-cost, scalable campaigns (emails, webinars, demos) focused on these underserved areas.  

### 7.2 Strengthen Engagement in London

London remains a **strategic market** with high company and revenue share, but there is still room to increase **spend per company**.

**Suggested actions:**
- **Account Management** → identify growth-ready accounts and build penetration plans.  
- **Marketing** → reinforce brand presence through focused campaigns.  
- **Customer Success** → encourage product adoption and cross-sell / up-sell initiatives.  

### 7.3 Break Down the “OTHER” Group for Further Analysis

The **OTHER** group aggregates a mix of cities, dependencies, and overseas territories that could not be precisely mapped.  
This category appears **unexpectedly large**, which suggests that several meaningful UK locations may be hidden inside it.

**Why this matters:**
- The size of the group distorts city-level insights.  
- Some potentially important cities may be misclassified.  
- Breaking down OTHER may reveal **new underserved or high-potential areas**.  

**Suggested next steps:**
- Perform a dedicated cleanup of addresses assigned to **OTHER**.  
- Use postcode data or additional geocoding tools to correctly map each location.  
- Re-run the underserved score after reclassification to reveal a more accurate ranking.  

### 7.4 Establish a Simple Monthly Monitoring Routine

Even without a dedicated data team, the company can maintain a **light, effective analytics workflow**:

- Nominate an internal **“data champion”** (within Sales Ops or Finance).  
- Export city-level data **monthly**.  
- Track key KPIs:
  - `company_count`  
  - `total_spend`  
  - `spend_per_company`  
  - `company_share`  
  - `spend_share`  
- Update the underserved ranking periodically to measure the impact of commercial actions.  

A simple dashboard or shared spreadsheet is enough to support ongoing decision-making.

### 7.5 Improve and Enrich the Dataset

Before scaling decisions, the board should support **better data collection** to enable deeper and more reliable analysis.

**What to add:**
- Transaction **dates** to analyze recency, frequency, and seasonality.  
- Clear separation of **B2B vs B2C** customers.  
- Basic customer attributes (**company size**, **sector**, when available).  

**Teams to engage:**
- **Sales** → responsible for CRM hygiene and accurate exports.  
- **Customer Success / Support** → can provide qualitative context and identify usage or onboarding gaps.  

Improving data quality will enable more advanced segmentation—such as spend per capita, sector-based behavior, or churn risk—and support more strategic decisions.

This analysis provides a clear, data-driven understanding of how revenue is distributed across UK cities, revealing both strong markets like London and a long tail of small, underserved locations.
---

## 8. Appendix
**Tools and Libraries:**
- Python (`pandas`, `matplotlib`, `plotly.express`, `plotly.graph_objects`)
- Jupyter Notebook for exploratory analysis [Notebook link](https://github.com/Anaclet12/UK-Customer-Spending-Analysis/blob/main/scripts/UK%20Customer%20Spending%20Analysis.ipynb)
- GOV.UK dataset for the official list of cities (f0r validation and standardization)

**Key Resources:**
- [UK Cities List (GOV.UK)](https://www.gov.uk/government/publications/list-of-cities/list-of-cities-html)
- [Plotly Documentation](https://plotly.com/python/)
- [Pandas API Reference](https://pandas.pydata.org/docs/)

---

✳️ *Author:* Anaclet Sado Fokam  
📅 *Date:* November 2025  
💼 *Project Type:* Data Analytics / Business Insights  
