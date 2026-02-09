# Customer Segmentation & Retention Strategy with RFM | Retail Analytics (Python)

## What is this project about?
This project applies the **RFM (Recency–Frequency–Monetary)** framework to analyze
**4,338 customers** using **387,938 transactions** recorded between **December 2010
and December 2011**, with total revenue exceeding **$8.9M**.

Customers were segmented into **11 RFM segments** and consolidated into
**4 actionable customer groups**:
- **Loyal & High Value**
- **High Risk Customers**
- **New & Potential**
- **Inactive & Lost**

The analysis highlights a strong concentration of revenue among high-frequency
customers, while identifying a sizable group of previously valuable customers
who are now disengaging.

**Business outcome**
The project translates customer behavior into **clear retention, re-engagement,
and growth strategies**, and demonstrates why **Frequency (F)** is the most critical
lever for sustainable revenue growth in a retail business model.

## Business Context / Industry Context
Retail businesses typically operate with **high customer acquisition costs** and
thin margins, making **customer retention** a critical driver of profitability.

Understanding **who the customers are**, **how often they purchase**, and **how
recently they engaged** allows companies to:
- Prioritize marketing spend more effectively
- Reduce customer churn
- Increase customer lifetime value (CLV)

The RFM (Recency–Frequency–Monetary) framework is a widely used, practical method
to translate transactional data into **actionable customer segments** that support
data-driven marketing and sales strategies.

## Background & Overview
This project analyzes historical transactional data from a retail business to
segment customers based on their purchasing behavior.

By combining **Recency**, **Frequency**, and **Monetary** metrics, customers are
classified into behavioral segments that reveal:
- Engagement levels
- Revenue contribution
- Churn risk

### Project Objective
The primary objective of this project is to:
- Segment customers using the RFM model
- Identify high-value, at-risk, and inactive customer groups
- Provide actionable insights and recommendations to support
  **customer retention and revenue growth**

### Business Questions
This analysis aims to answer the following questions:
1. How are customers distributed across different RFM segments?
2. Which customer segments contribute the most to total revenue?
3. Which customer groups show signs of declining engagement and churn risk?
4. How do customer behaviors (Recency, Frequency, Monetary) change over time?
5. Which RFM metric should the business prioritize to drive sustainable growth?

### Who Is This Project For?
This project is designed for:
- **Marketing teams** looking to optimize campaign targeting and retention strategies
- **Sales teams** aiming to focus efforts on high-value and high-risk customers
- **Business Intelligence & Data Analysts** who support strategic decision-making
- **Management teams** seeking data-driven insights into customer behavior

## 2. 📂 Dataset Description & Data Structure

### 📌 Data Source  
- **Source**: Provided dataset for E-commerce retail analysis  
- **Size**: 541,910 rows × 8 columns (Sheet 1: E-commerce retail), additional segmentation details in Sheet 2  
- **Format**: .xlsx (Excel file with two sheets)  
## 📂 Data Structure & Relationships  

### 1️⃣ Tables Used  
The dataset consists of **two tables (sheets)**:  
- **Sheet 1: E-commerce Retail** – Contains transaction-level data, including order details, customer IDs, and purchase information.  
- **Sheet 2: Segmentation** – Stores customer segments along with their RFM scores.  

### 2️⃣ Table Schema & Data Snapshot  

#### 📌 Sheet 1: E-commerce Retail  
### 📋 Table Schema: E-commerce Retail  

<details>
  <summary>📂 **Dataset Schema** (Click to expand)</summary>

| Column Name  | Data Type         | Description  |  
|-------------|-----------------|--------------|  
| **InvoiceNo**  | `object`  | Unique invoice number for each transaction (6-digit). If it starts with 'C', it indicates a cancellation. |  
| **StockCode**  | `object`  | Unique product (item) code (5-digit). |  
| **Description**  | `object`  | Product (item) name. |  
| **Quantity**  | `int64`  | The number of units purchased per transaction. |  
| **InvoiceDate**  | `datetime64[ns]`  | Date and time when the transaction occurred. |  
| **UnitPrice**  | `float64`  | Price per unit of the product in sterling. |  
| **CustomerID**  | `float64`  | Unique 5-digit identifier for each customer. |  
| **Country**  | `object`  | Name of the country where the customer resides. |  

</details>

#### 📌 Sheet 2: Segmentation  
### 📊 Customer Segmentation & RFM Scores  

<details>
  <summary>📊 **RFM Segmentation Mapping** (Click to expand)</summary>

| **Segment**              | **RFM Score**  |  
|-------------------------|-----------------------------------------------------------|  
| **Champions**            | 555, 554, 544, 545, 454, 455, 445  |  
| **Loyal**                | 543, 444, 435, 355, 354, 345, 344, 335  |  
| **Potential Loyalist**   | 553, 551, 552, 541, 542, 533, 532, 531, 452, 451, 442, 441, 431, 453, 433, 432, 423, 353, 352, 351, 342, 341, 333, 323  |  
| **New Customers**        | 512, 511, 422, 421, 412, 411, 311  |  
| **Promising**            | 525, 524, 523, 522, 521, 515, 514, 513, 425, 424, 413, 414, 415, 315, 314, 313  |  
| **Need Attention**       | 535, 534, 443, 434, 343, 334, 325, 324  |  
| **About To Sleep**       | 331, 321, 312, 221, 213, 231, 241, 251  |  
| **At Risk**              | 255, 254, 245, 244, 253, 252, 243, 242, 235, 234, 225, 224, 153, 152, 145, 143, 142, 135, 134, 133, 125, 124  |  
| **Cannot Lose Them**     | 155, 154, 144, 214, 215, 115, 114, 113  |  
| **Hibernating Customers** | 332, 322, 233, 232, 223, 222, 132, 123, 122, 212, 211  |  
| **Lost Customers**       | 111, 112, 121, 131, 141, 151   |

</details>

## Data Cleaning & Preprocessing
Before conducting the analysis, the dataset was cleaned to ensure data accuracy
and reliability.

Key preprocessing steps included:
- Removed cancelled transactions and records with invalid quantities or prices.
- Handled missing customer identifiers to ensure correct customer-level analysis.
- Consolidated duplicate transaction records to avoid double-counting.
- Standardized transactional data to support accurate RFM metric calculation.

These steps ensured that customer behavior and revenue metrics accurately
reflected real purchasing activity.

## Analytical Approach
The analysis follows a structured, business-driven approach to transform
transactional data into actionable customer insights.

### Step 1: RFM Metric Construction
Customer behavior was quantified using three key metrics:
- **Recency (R):** Number of days since the customer’s most recent purchase.
- **Frequency (F):** Total number of purchase transactions.
- **Monetary (M):** Total revenue generated by the customer.

These metrics capture engagement, loyalty, and customer value.

### Step 2: RFM Scoring
Each RFM metric was scored on a scale from 1 to 5 using quantile-based ranking:
- Higher **Recency scores** represent more recent activity.
- Higher **Frequency scores** indicate more frequent purchases.
- Higher **Monetary scores** reflect higher revenue contribution.

The three scores were combined into a single **RFM score** to represent overall
customer value and engagement.

### Step 3: Customer Segmentation
Customers were assigned to **11 standard RFM segments** (e.g., Champions, Loyal,
At Risk, Lost Customers) based on their RFM scores.

To support strategic decision-making, these segments were further consolidated
into **4 actionable customer groups**:
- Loyal & High Value
- High Risk Customers
- New & Potential
- Inactive & Lost

### Step 4: Trend & Behavioral Analysis
Customer behavior and segment composition were analyzed over time to identify:
- Changes in engagement and purchasing patterns
- Early signals of churn risk
- Opportunities for retention and growth strategies

## Customer Segmentation Analysis
Using the RFM framework, customers were segmented into 11 distinct groups
based on their purchasing recency, frequency, and monetary value.

These segments reveal clear differences in customer engagement,
purchase behavior, and revenue contribution, forming the foundation
for targeted retention and growth strategies.

### 👥 Customer Share by Segment

<img width="1212" height="697" alt="image" src="https://github.com/user-attachments/assets/89bf5d4c-b98f-4aaa-8111-c8f264150ac1" />

- The customer base is concentrated in a few key segments, with **Champions (~19.2%)** and **Hibernating customers (~16.0%)** representing the largest shares.
- A significant portion of customers falls into **inactive or low-engagement segments** (**Hibernating + Lost = ~ 27.2%**), indicating weak recent engagement and elevated churn risk.
- **High-value segments** (**Champions + Loyal + Potential Loyalist = ~ 38.5%**) form a strong foundation for **retention and upsell strategies**.
- Smaller segments such as **Cannot Lose Them ( ~ 2.0%)** and **Promising ( ~ 3.0%)**, while limited in size, remain strategically important due to **potential value or churn risk**.

### 📊 Number of Customers by Segment

<img width="1251" height="622" alt="image" src="https://github.com/user-attachments/assets/2fc512e5-cd3b-40c7-9a3d-18d426e11049" />


- The largest customer segments by count are **Champions (835 customers)** and **Hibernating customers (696 customers)**, reflecting a split between highly engaged customers and those trending toward inactivity.
- Mid-sized segments such as **Lost (486)**, **Loyal (428)**, **At Risk (422)**, and **Potential Loyalist (414)** indicate multiple customer groups with sufficient scale for **targeted and segmented campaigns**.
- Smaller segments like **Cannot Lose Them (91)** and **Promising (136)** are well-suited for **personalized interventions**, as the customer base is relatively manageable.

### 💰 Total Revenue by Segment

<img width="1255" height="622" alt="image" src="https://github.com/user-attachments/assets/45b29ab0-8d83-4ee9-a737-e745b949653d" />

- **Champions** are the primary revenue drivers, contributing a disproportionate share of total sales and representing the most valuable customer group.
- **Loyal customers** generate the second-highest revenue, confirming that **repeat purchasing behavior** is a stable and reliable source of revenue.
- **At Risk customers** still contribute meaningful revenue despite declining engagement, making them a **high-priority retention segment** due to the potential revenue loss if churn occurs.
- Segments such as **New Customers**, **About To Sleep**, and **Lost customers** contribute relatively low revenue, suggesting that **reactivation and nurturing efforts should be evaluated carefully against expected return**.

**🔑 Key Takeaway**
- The customer base is clearly divided between **highly engaged revenue drivers** (**Champions and Loyal**) and a sizable group of **inactive or declining customers** (**Hibernating, Lost, and At Risk**), highlighting clear priorities for **retention and re-engagement strategies**.

### ⏱️ Segmentation by Recency (Median Days Since Last Purchase)

<img width="1202" height="692" alt="image" src="https://github.com/user-attachments/assets/848a4f69-3f10-4dbb-8627-44cda1c3efb6" />

- **Champions** have the lowest recency, indicating very recent and consistent purchasing behavior and confirming that they are the most engaged and active customers.
- **Loyal**, **New Customers**, **Potential Loyalist**, and **Promising** segments show low to moderate recency, suggesting ongoing engagement and strong potential for retention.
- **At Risk**, **Hibernating**, **Cannot Lose Them**, and **Lost** customers exhibit high recency, meaning a long time has passed since their last purchase.
- **Cannot Lose Them** and **Lost customers** stand out with the highest recency values, signaling severe disengagement and a high likelihood of permanent churn.

#### 🔑 Key Takeaway
- **Recency clearly differentiates active customers from disengaged ones and acts as the earliest and most actionable warning signal for churn.**

### 🔁 Segmentation by Frequency (Median Purchase Count)

<img width="1165" height="705" alt="image" src="https://github.com/user-attachments/assets/11639e2b-c046-4270-a570-1aae2877e517" />


- **Champions** show by far the highest purchase frequency, confirming their role as the core repeat-buying customer segment.
- **Loyal customers** also demonstrate strong purchase frequency, though at a lower level than Champions, reflecting stable but less intensive buying behavior.
- **At Risk** and **Need Attention** segments maintain moderate purchase frequency, suggesting they were previously valuable customers whose engagement is now declining.
- **New Customers**, **Promising**, **Hibernating**, **Lost**, and **Cannot Lose Them** segments exhibit very low purchase frequency, indicating weak or fading purchasing habits.

#### 🔑 Key Takeaway
- **A decline in purchase frequency often precedes full inactivity, making Frequency a critical lever for early retention and re-engagement efforts.**

### 💰 Segmentation by Monetary (Revenue Share)

<img width="1220" height="697" alt="image" src="https://github.com/user-attachments/assets/c2b48517-e365-40ab-8b06-e02afba434bc" />

- **Champions** dominate revenue contribution, accounting for **62.9% of total revenue**, highlighting extreme revenue concentration within a single segment.
- **Loyal customers** contribute the second-largest share (**11.5%**), reinforcing the importance of long-term repeat buyers.
- **At Risk customers** still generate a meaningful portion of revenue (**8.4%**), despite declining engagement in Recency and Frequency, making them a critical revenue-at-risk segment.
- All remaining segments contribute relatively small shares of revenue, suggesting limited short-term financial impact if they churn.

#### 🔑 Key Takeaway
- **Revenue is primarily driven by a small group of highly engaged customers, while disengaging segments still represent meaningful revenue at risk.**

## Strategic Customer Grouping
While the 11 RFM segments provide detailed behavioral insights,
they are too granular for strategic planning and execution.

To support clearer decision-making, the segments are consolidated
into four strategic customer groups based on shared characteristics
across Recency, Frequency, and Monetary dimensions.

### Loyal & High Value Customers
**Includes:** Champions, Loyal, Potential Loyalist

**Characteristics:**
- Low recency and high purchase frequency
- Highest revenue contribution
- Strong engagement and repeat purchasing behavior

This group represents the most valuable customer base and is critical
for sustaining long-term revenue growth.

### High Risk Customers
**Includes:** At Risk, Need Attention, About To Sleep, Cannot Lose Them

**Characteristics:**
- Increasing recency indicating declining engagement
- Moderate to high historical purchase frequency
- Meaningful revenue contribution at risk of churn

These customers were previously valuable but are now disengaging,
making them a top priority for retention efforts.

### New & Potential Customers
**Includes:** New Customers, Promising

**Characteristics:**
- Recent purchases but low frequency
- Low to moderate revenue contribution
- Early-stage relationship with growth potential

This group requires nurturing strategies to encourage repeat purchases
and long-term loyalty.

### Inactive & Lost Customers
**Includes:** Hibernating customers, Lost customers

**Characteristics:**
- Very high recency and minimal purchase activity
- Low frequency and low revenue contribution
- Low likelihood of reactivation without strong incentives

This group should be selectively targeted based on cost-benefit
considerations.

| Strategic Group | Included Segments | Key Focus |
|-----------------|------------------|-----------|
| Loyal & High Value | Champions, Loyal, Potential Loyalist | Retain & Upsell |
| High Risk | At Risk, Need Attention, About To Sleep, Cannot Lose Them | Re-engage |
| New & Potential | New Customers, Promising | Nurture |
| Inactive & Lost | Hibernating, Lost customers | Selective Win-back |


## Visualization & Trend Analysis

### Customer Group Contribution Overview

The customer base is not evenly distributed across strategic segments.

<img width="1006" height="563" alt="image" src="https://github.com/user-attachments/assets/ffdc19ad-9cfa-4d01-986c-9fa0e4cd73a4" />

- **Loyal & High Value customers (38.7%)** represent the largest share of the customer base.
  This group forms the core foundation of the business, contributing the most stable
  and predictable value over time.

- **Inactive & Lost customers (27.2%)** account for more than a quarter of total customers,
  indicating a significant portion of the customer base has already disengaged or is no
  longer actively purchasing.

- **High Risk customers (24.8%)** represent nearly one-fourth of customers.
  Although they previously showed purchasing activity, their current engagement levels
  suggest a high probability of churn without timely intervention.

- **New & Potential customers (9.3%)** make up the smallest share.
  While currently contributing less, this group represents future growth opportunities
  if nurtured effectively.

  #### 🎯 Business Interpretation
Overall, more than **50% of customers fall into High Risk or Inactive & Lost groups**.
This highlights that retention and re-engagement strategies are at least as critical
as customer acquisition for sustaining long-term business performance.

### Customer Group Trend Over Time

<img width="1253" height="591" alt="image" src="https://github.com/user-attachments/assets/54e11004-508d-477b-b9e6-56a3b73825dd" />

- **Loyal & High Value customers** consistently represent the largest group throughout the period.
  Their customer count shows a clear upward trend from mid-2011, peaking around Q4,
  indicating successful retention and repeat purchasing behavior during this time.

- **High Risk customers** increase gradually from early to mid-2011.
  This suggests that a portion of previously active customers are beginning to show
  declining engagement and are moving toward potential churn.

- **Inactive & Lost customers** display a declining trend toward the end of the period.
  This may indicate either successful reactivation efforts or customers fully exiting
  the customer base.

- **New & Potential customers** remain relatively small for most of the year but show
  a noticeable spike near the end of the period.
  This likely reflects seasonal customer acquisition or promotional campaigns.

  #### 🎯 Business Interpretation
The simultaneous growth of **Loyal & High Value** and **High Risk** groups suggests a
transition dynamic in the customer lifecycle: while loyal customers are being retained,
a parallel group is gradually becoming disengaged.

This highlights the importance of early intervention strategies to prevent High Risk
customers from transitioning into the Inactive & Lost group.

### Trend of Recency, Frequency, Monetary

<img width="1248" height="602" alt="image" src="https://github.com/user-attachments/assets/3ac65de8-9baf-4bdb-b543-689c40ecb947" />

<img width="1257" height="597" alt="image" src="https://github.com/user-attachments/assets/d8497986-8c2b-4e08-b028-d12a2312c89a" />

<img width="1251" height="602" alt="image" src="https://github.com/user-attachments/assets/72b21cea-ca80-4468-a016-1219723e1efd" />


| Customer Group | Observation | Insight |
|--------------|------------|---------|
| **Loyal & High-Value Customers**<br/>(Champions + Loyal + Potential Loyalist) | • Lowest recency (≈ 30–45 days), indicating frequent and consistent returns<br/>• Highest purchase frequency, with strong growth from Q3–Q4 2011<br/>• Contribute the majority of total revenue, with a clear spike around Sep–Nov 2011 | This group represents the **core revenue engine** of the business. Year-end revenue growth is driven primarily by these customers rather than new customer acquisition. |
| **High-Risk Customers**<br/>(At Risk + Need Attention + Cannot Lose Them + About To Sleep) | • Recency is improving slightly but remains higher than the loyal group<br/>• Purchase frequency is moderate but trending downward or flat<br/>• Still contribute meaningful revenue, but growth is not keeping pace over time | This segment represents **revenue at risk**. Customers have not churned yet, but without timely intervention, they are likely to slide into inactive or lost segments. |
| **Inactive & Lost Customers**<br/>(Hibernating + Lost) | • Highest recency, even with rolling time windows<br/>• Very low purchase frequency with little to no recovery<br/>• Revenue contribution is small and unstable | This group should **not be prioritized for large-scale marketing spend**, as mass reactivation efforts are likely to yield low ROI. |
| **New & Potential Customers**<br/>(New Customers + Promising) | • Low and stable recency, indicating recent first purchases<br/>• Slight increase in purchase frequency toward Q4 2011<br/>• Revenue contribution is still low, with a noticeable spike in Nov 2011 | While not yet major revenue contributors, this segment is a **future pipeline for Loyal and High-Value customers** if nurtured effectively. |


