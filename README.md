# Retail-Intelligence
Here is a `README.md` file in Markdown format for your RFM analysis project:

---

# RFM Analysis for Customer Segmentation

This project focuses on performing an RFM (Recency, Frequency, Monetary) analysis to segment customers based on their purchasing behavior. This model helps businesses identify groups of customers to target for specific marketing strategies, retention efforts, and personalized campaigns.

## Project Overview

The RFM model is widely used in customer segmentation as it provides a detailed analysis of customer activity using three key metrics:
1. **Recency (R)**: How recently a customer made a purchase.
2. **Frequency (F)**: How often a customer makes a purchase.
3. **Monetary (M)**: How much a customer spends.

By analyzing these three metrics, businesses can categorize customers into various segments, allowing for targeted strategies to enhance customer experience, boost retention, and optimize marketing efforts.

## RFM Segmentation Process

1. **Data Collection**: The dataset includes customer transaction data, which contains the following attributes:
   - `Recency`: Number of days since the last purchase.
   - `Frequency`: Number of purchases made by the customer.
   - `Monetary`: Total amount spent by the customer.

2. **RFM Scoring**: Each customer is assigned a score for Recency, Frequency, and Monetary values on a scale from 1 to 5. Higher scores indicate higher activity in each category:
   - Recency scores are inversely proportional, with lower values indicating recent purchases.
   - Frequency and Monetary scores are directly proportional, with higher values indicating frequent purchases and higher spending.

3. **RFM Segment Creation**: Customers are grouped into segments based on their RFM scores (e.g., "Gold_Silver", "Bronze_Bronze"). These segments help to identify customer behavior patterns and loyalty levels.

4. **Data Visualization**: Various visualizations provide insights into customer distribution across segments and RFM scores:
   - **Bar Chart**: Shows the count of customers in each RFM segment.
   - **Pie Chart**: Displays the percentage distribution of customers by segment.
   - **Heatmap**: Illustrates the distribution of RFM scores across Recency, Frequency, and Monetary values.
   - **Histograms**: Show the distribution of each RFM score (Recency, Frequency, and Monetary).

## RFM Segmentation Insights

After segmenting customers, we can identify groups with different purchasing behaviors:
- **High-Value Customers** (e.g., "Platinum_Platinum"): Customers with recent, frequent, and high-value purchases. These customers are highly engaged and valuable.
- **Potential Loyalists** (e.g., "Gold_Silver", "Silver_Silver"): Customers who frequently purchase but may not have the highest spend. They could be targeted for upselling.
- **Low-Value Customers** (e.g., "Bronze_Bronze"): Customers who rarely make purchases or spend low amounts. These customers may need re-engagement or promotional offers.

## Code and Analysis

Below are the key code snippets used in this project:

### 1. RFM Segment Calculation

```python
rfm['RFM_Segment'] = rfm['Frequency_Score'].astype(str) + "_" + rfm['Monetary_Score'].astype(str)
rfm_segment_counts = rfm['RFM_Segment'].value_counts()
```

### 2. Visualizations

#### Bar Chart - RFM Segment Distribution
```python
import matplotlib.pyplot as plt
plt.figure(figsize=(12, 8))
rfm_segment_counts.plot(kind='bar', color='skyblue')
plt.title('Distribution of Customers Across RFM Segments')
plt.xlabel('RFM Segments')
plt.ylabel('Number of Customers')
plt.xticks(rotation=45, ha='right')
plt.tight_layout()
plt.show()
```

#### Pie Chart - Percentage Distribution of Customers by RFM Segment
```python
plt.figure(figsize=(8, 9))
rfm_segment_counts.plot(kind='pie', autopct='%1.1f%%', colors=plt.cm.Paired.colors)
plt.title('Percentage Distribution of Customers Across RFM Segments')
plt.ylabel('')
plt.tight_layout()
plt.show()
```

#### Heatmap - RFM Scores Distribution
```python
import seaborn as sns
rfm_scores = rfm[['R_Score', 'F_Score', 'M_Score']].groupby(['R_Score', 'F_Score', 'M_Score']).size().reset_index(name='Customer Count')
rfm_pivot = rfm_scores.pivot_table(index='R_Score', columns=['F_Score', 'M_Score'], values='Customer Count', aggfunc='sum', fill_value=0)
plt.figure(figsize=(12, 8))
sns.heatmap(rfm_pivot, annot=True, fmt='d', cmap='YlGnBu', cbar=True)
plt.title('Heatmap of RFM Scores Distribution')
plt.xlabel('Frequency and Monetary Scores')
plt.ylabel('Recency Scores')
plt.tight_layout()
plt.show()
```

#### Histograms - Distribution of Recency, Frequency, and Monetary Scores
```python
fig, axes = plt.subplots(1, 3, figsize=(18, 5))
axes[0].hist(rfm['R_Score'], bins=5, color='lightgreen', edgecolor='black')
axes[0].set_title('Distribution of Recency Scores')
axes[1].hist(rfm['F_Score'], bins=5, color='salmon', edgecolor='black')
axes[2].hist(rfm['M_Score'], bins=5, color='lightblue', edgecolor='black')
plt.tight_layout()
plt.show()
```

### 3. Saving the RFM Results

```python
# Save RFM results for further analysis
rfm.to_csv('rfm_analysis_results.csv')
```

## Results and Interpretation

The results of the RFM analysis help in understanding the customer base and developing targeted strategies:
- **Customer Retention**: Identify high-value customers for retention strategies.
- **Targeted Campaigns**: Create personalized marketing campaigns for different segments.
- **Customer Lifetime Value (CLV)**: Use RFM scores to estimate the long-term value of customers.
- **Re-engagement**: Design strategies for inactive or low-value customers.
![Screenshot 2024-11-09 030254](https://github.com/user-attachments/assets/2e67a501-bd5f-463e-b01d-ebda0fb33bd5)

  #### Customer Segmentation Dashboard
Overview
This dashboard provides an in-depth analysis of customer behavior using RFM (Recency, Frequency, and Monetary) scoring. The data visualizations help to understand customer engagement, spending habits, and segmentation. By breaking down the customer base into Platinum, Gold, Silver, and Bronze segments, this dashboard aims to guide data-driven decision-making for targeted marketing strategies.

Key Insights
RFM Score Distribution:
The bar chart shows the distribution of customers' RFM scores across various segments. Higher RFM scores are associated with Platinum customers, who contribute significantly to the total sales, frequency, and recency metrics.
RFM Score Trend by Segment:
This trend line shows how RFM scores vary across customer segments, indicating which segments are more consistent in engagement over time. Platinum customers maintain the highest RFM scores, suggesting strong loyalty and frequent engagement.
Purchases by Frequency Score:
The donut chart indicates that Platinum customers make up the largest share of total purchases (66.93%), followed by Gold, Silver, and Bronze segments. This reflects a concentration of purchases among the highest loyalty segment.
Revenue by Spending Score:
The bar chart compares the monetary contribution of each segment, with Platinum customers generating the highest revenue (5.3M). This metric reinforces the significance of the Platinum segment in terms of spending power.
Revenue by Customer Segment:
The treemap shows the revenue breakdown by individual RFM segments, highlighting “Platinum_Platinum” as the most lucrative customer group. This segment alone contributes a substantial portion of the overall revenue.
Recency Score by Segment:
This visualization of recency scores per segment demonstrates that the highest recency scores belong to Platinum segments, showing that these customers have been active recently. It also highlights opportunities to re-engage lower-recency segments like Bronze and Silver.
Proposed Solutions
Based on the insights:

Targeted Marketing:

Focus on retention strategies for the Platinum segment to maintain their high engagement. This could include loyalty programs, exclusive discounts, or personalized product recommendations.
Re-engagement campaigns for lower-recency segments (e.g., Bronze and Silver) through email marketing or special offers could bring these customers back into active status.
Customer Acquisition and Upselling:

Upsell opportunities can be focused on Gold customers, who are already moderately engaged and could be moved up to Platinum with targeted promotions.
New customer acquisition campaigns could prioritize customers with spending habits similar to the Silver and Bronze segments but emphasize value and benefits to increase their frequency and spending.
Optimized Resource Allocation:

Allocate marketing resources to segments based on their revenue potential, with the majority directed toward high-value segments (Platinum and Gold) for sustained returns.
Effectiveness of Proposed Solutions
The proposed strategies aim to maximize the value from existing high-value customers while encouraging less engaged segments to increase their frequency and spending. By concentrating efforts on Platinum and Gold segments, the business can drive revenue growth efficiently. Re-engagement efforts for lower segments, while more challenging, offer potential for customer lifetime value improvements with minimal costs.

Next Target Audience
The next marketing campaigns should aim at:

Platinum and Gold Customers for upselling and retention, given their strong revenue contributions.
Bronze and Silver Customers for reactivation, particularly focusing on lapsed users with potential to return to regular purchasing patterns.

This dashboard offers a comprehensive view of customer segmentation, emphasizing actionable insights for each customer segment. Through targeted marketing, re-engagement strategies, and efficient resource allocation, these insights can lead to increased customer lifetime value and optimized marketing ROI.

## Requirements

- Python libraries: `pandas`, `matplotlib`, `seaborn`
- Power Bi
## Conclusion

This RFM segmentation project provides a robust method for analyzing customer behavior, helping businesses optimize their marketing efforts and improve customer experience. By utilizing RFM scores, you can better understand customer value and loyalty, allowing for more effective decision-making and customer relationship management.

--- 

This `README.md` file outlines the purpose, methods, and key code elements of your RFM analysis project, providing a clear overview for anyone reviewing or using the project.
Afolabi Olawale.
