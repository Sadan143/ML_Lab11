# ML_Lab11
# Final Questions & Answers

1. Why is this an unsupervised learning problem?**
    This is an unsupervised learning problem because the dataset does not contain any predefined target labels or a dependent variable ($y$). The goal is to discover hidden patterns and naturally group the customers based purely on the similarities in their behavioral data, without any prior training guidance.

2. Why did we remove the `CUST_ID` column?**
The `CUST_ID` column is a unique identifier for each credit card holder. It does not carry any statistical weight or represent any actual behavioral pattern. Leaving it in the dataset would confuse the distance-based clustering algorithm by treating a sequential or arbitrary ID as a meaningful numeric feature.

3. Which columns had missing values?**
The columns with missing values were `MINIMUM_PAYMENTS` and `CREDIT_LIMIT`.

4.How did you handle the missing values?**
 Missing values were handled using **mean imputation**. The null values in each column were replaced with the mathematical mean (average) of that specific column, ensuring no data rows were lost.

5. Why is scaling important before applying K-Means?**
 K-Means relies entirely on calculating **Euclidean distance** to group data points together. Features with massive numeric ranges (like `BALANCE` or `CREDIT_LIMIT` in the thousands) will naturally dominate the distance calculations over features with tiny ranges (like frequencies bounded between 0 and 1). Scaling standardizes all features to the same scale, ensuring they contribute equally to the distance metrics.

6. Which K value did you choose? Explain your answer using the elbow method and silhouette score.**
 I chose **$K = 4$**. When observing the Elbow Curve, the sharp drop in inertia (Within-Cluster Sum of Squares) begins to slow down and flatten out clearly around $K=4$. Furthermore, looking at the silhouette scores, $K=4$ balances a healthy separation score while providing a highly interpretable and practical breakdown of customer segments for real-world marketing.

7. Based on the cluster summary table, describe each customer segment in your own words:
1)Cluster - High-Spenders / VIPs:** Customers with high credit limits, very high purchasing volume, and high purchase frequencies. They utilize their cards heavily for transactions.
2)Cluster - Cash Advance Reliers:** Customers who primarily use their cards to withdraw physical cash. They have high `CUSH_ADVANCE` balances and transaction counts, but low retail purchases.
3)Cluster - Balanced / Moderate Users:** The average customer group. They maintain a moderate balance and make occasional purchases but don't lean heavily into extreme spending or cash advances.
4)Cluster - Inactive / Low-Spenders:** Customers who maintain low or near-zero balances and rarely make any purchases or cash advances.

8. Which cluster may represent high-value customers?**
 The cluster representing the **High-Spenders / VIPs** (the group with the highest average `PURCHASES` and `PURCHASES_FREQUENCY`). They generate steady transaction fee revenue for the credit card company.

9. Which cluster may represent customers who rely more on cash advance?**
 The cluster that displays the highest mean values for both `CASH_ADVANCE` and `CASH_ADVANCE_TRX`.

10. How can a company use these clusters for marketing strategy?**
For High-Spenders:** Offer premium cashback rewards, tier-upgrades, and exclusive loyalty programs to encourage even higher transaction volumes.

For Cash Advance Users:** Target them with personalized offers regarding lower interest rates on cash advances, or educate them on installment plan alternatives.

For Inactive Users:** Launch re-engagement email campaigns with introductory promotional discounts or zero-annual-fee reminders to motivate them to reactivate their cards.
