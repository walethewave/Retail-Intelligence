# Retail-Intelligence: Customer Segmentation with RFM Analysis

Unlock the power of customer data with **Retail-Intelligence**, a project that leverages RFM (Recency, Frequency, Monetary) analysis to segment customers based on their purchasing behavior. This framework empowers businesses to craft targeted marketing strategies, enhance customer retention, and maximize profitability through data-driven insights.

---

## Project Overview

RFM analysis is a widely recognized technique in customer segmentation, evaluating three core metrics:
- **Recency (R)**: How recently a customer made a purchase.
- **Frequency (F)**: How often a customer makes purchases.
- **Monetary (M)**: How much a customer spends.

By assigning scores to these metrics, businesses can categorize customers into actionable segments—such as high-value loyalists or at-risk groups—enabling personalized campaigns and optimized resource allocation.

---

## Data and Methodology

### Data
The analysis utilizes customer transaction data with the following attributes:
- **Recency**: Number of days since the last purchase.
- **Frequency**: Total number of purchases per customer.
- **Monetary**: Total amount spent by each customer.

*Note: The dataset is a sample for demonstration purposes and contains no sensitive information.*

### Methodology
1. **RFM Scoring**:
   - Customers receive scores from 1 to 5 for each metric.
   - **Recency**: Inversely scored (lower days since last purchase = higher score).
   - **Frequency and Monetary**: Directly scored (higher values = higher scores).

2. **Segment Creation**:
   - Customers are grouped into segments (e.g., "Platinum," "Gold," "Silver," "Bronze") based on their RFM scores.
   - These segments reveal behavioral patterns and loyalty levels.

---

## Code and Analysis

The RFM analysis is implemented in Python within a Jupyter Notebook (`Customer Segmentation.ipynb`). Key steps include:
- Data preprocessing to calculate RFM metrics.
- Scoring customers using quantile-based discretization.
- Segmenting customers by combining RFM scores.

**Example Code Snippet** (RFM Segment Calculation):
```python
rfm['RFM_Segment'] = rfm['Frequency_Score'].astype(str) + "_" + rfm['Monetary_Score'].astype(str)
rfm_segment_counts = rfm['RFM_Segment'].value_counts()
```

The results are saved as `rfm_analysis_results.csv` for further use.

---

## Visualizations

### Python Visualizations
The Jupyter Notebook includes exploratory visualizations:
- **Bar Chart**: Customer distribution across RFM segments.
- **Pie Chart**: Percentage breakdown of customers by segment.
- **Heatmap**: RFM score distribution across Recency, Frequency, and Monetary.
- **Histograms**: Individual distributions of Recency, Frequency, and Monetary scores.

These visualizations highlight customer behavior trends and segment characteristics.

### Power BI Dashboard
![image](https://github.com/user-attachments/assets/271a4f87-e057-45b2-abe0-84e4f6f0de0f)

The interactive Power BI dashboard (`Customer Segmentation.pbix`) provides a dynamic view of the analysis:
- **RFM Score Distribution**: Bar chart of customer counts by segment.
- **RFM Score Trend by Segment**: Line chart showing engagement consistency.
- **Purchases by Frequency Score**: Donut chart emphasizing purchase concentration (e.g., Platinum segment: 66.93% of purchases).
- **Revenue by Spending Score**: Bar chart of monetary contributions (e.g., Platinum segment: $5.3M).
- **Revenue by Customer Segment**: Treemap highlighting top revenue-generating segments.
- **Recency Score by Segment**: Visualization of recent activity by segment.

---

## Dashboard Overview

The Power BI dashboard offers actionable insights:
- **Platinum Segment**: High RFM scores, driving significant revenue and purchases.
- **Gold and Silver Segments**: Moderate engagement, ripe for upselling or retention efforts.
- **Bronze Segment**: Low activity, signaling re-engagement opportunities.

These insights inform strategic decisions, from retaining top customers to reactivating dormant ones.

---

## Business Implications and Recommendations

### Proposed Solutions
- **Retention Strategies**: Loyalty programs and exclusive offers for Platinum customers.
- **Upselling Opportunities**: Targeted promotions for Gold customers to boost spending.
- **Re-engagement Campaigns**: Email marketing or discounts for Bronze and Silver segments.

### Effectiveness
Focusing on high-value segments (Platinum and Gold) drives efficient revenue growth, while re-engaging lower segments increases customer lifetime value with minimal investment.

### Next Target Audience
- **Primary Focus**: Platinum and Gold customers for retention and upselling.
- **Secondary Focus**: Bronze and Silver customers for reactivation.

---

## Requirements and Usage

### Requirements
- **Python Libraries**: `pandas`, `matplotlib`, `seaborn`
- **Software**: Power BI Desktop

### Usage Instructions
1. Clone the repository:
   ```bash
   git clone https://github.com/walethewave/Retail-Intelligence.git
   ```
2. Open `Customer Segmentation.ipynb` in Jupyter Notebook to run the RFM analysis.
3. Launch `Customer Segmentation.pbix` in Power BI Desktop to explore the dashboard.

---

## Conclusion

**Retail-Intelligence** showcases the power of RFM analysis in decoding customer behavior and informing strategic marketing. By leveraging these insights, businesses can enhance customer experiences, optimize marketing ROI, and drive sustainable growth.

---

## About the Author

**Afolabi Olawale** is a data analyst with expertise in business intelligence and customer analytics. Proficient in Python and Power BI, he transforms raw data into actionable strategies.

---

## Resources and Links

- [GitHub Repository](https://github.com/walethewave/Retail-Intelligence)
- [Jupyter Notebook](https://github.com/walethewave/Retail-Intelligence/blob/main/Customer%20Segmentation.ipynb)
- [Power BI Dashboard](https://github.com/walethewave/Retail-Intelligence/blob/main/Customer%20Segmentation.pbix)
- [RFM Results CSV](https://github.com/walethewave/Retail-Intelligence/blob/main/rfm_analysis_results.csv)

---
