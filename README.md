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

## Requirements

- Python libraries: `pandas`, `matplotlib`, `seaborn`

## Conclusion

This RFM segmentation project provides a robust method for analyzing customer behavior, helping businesses optimize their marketing efforts and improve customer experience. By utilizing RFM scores, you can better understand customer value and loyalty, allowing for more effective decision-making and customer relationship management.

--- 

This `README.md` file outlines the purpose, methods, and key code elements of your RFM analysis project, providing a clear overview for anyone reviewing or using the project.
