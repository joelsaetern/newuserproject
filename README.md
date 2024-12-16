
# Analyzing New Player Engagement in Mobile Games
## Insights from Clustering and Machine Learning  
### Author: Joel Saetern  
*Write-up and Code Supported by GPT-4o*  

---

## Introduction

Imagine you're diving into a new mobile game. Some players become hooked instantly, while others drop off after a single session. **What separates the loyal gamers from the ones who leave?**  
That's the mystery we set out to solve. By combining **machine learning** and **behavioral analysis**, we cracked the code on what keeps players coming back.

---

## Overview of the Data

Our dataset offers a sneak peek into the early journeys of new players. It captures everything from their **first-day activity** to the type of **in-game offers** they encounter.

### Key Features:

- **`d0_session_duration`**: How much time a player spent in the game on Day 1.  
- **`fp_offer_type`**: The kind of offer (e.g., bonus items or discounts) presented to the player.  
- **`first_list_price`**: The amount of their first purchase.  
- **`d0_level`**: How far they progressed on the first day.  
- **Categorical Features**: Player demographics like location, platform, and channel type.  
- **Target Variable**: Whether a player remained active after 30 days (**`d30_is_active`**).  

### Key Questions Addressed:
1. **Can we group players into meaningful clusters based on their engagement patterns?**
2. **What factors predict whether a player will stick around?**

---

## Clustering New Users

### K-Means Clustering
We applied **K-Means clustering** to uncover hidden patterns among players. After processing the data using **PCA** (a technique to simplify features), we grouped users into three distinct clusters:

- **Cluster 0**: The *casual crowd*. Players had moderate session durations and average engagement metrics.
- **Cluster 1**: The *super fans*. Players spent the most time in the game, progressed quickly, and often made significant purchases.
- **Cluster 2**: The *one-and-dones*. Players showed minimal activity, short sessions, and little sign of returning.

> **Silhouette Score**: `0.75`  
Clusters were well-defined, making them a powerful tool for targeted strategies.

### Hierarchical Clustering
To understand relationships between players further, we applied **Hierarchical Clustering**. This offered a more granular look at engagement patterns:

- **Cluster 0**: Players with moderate session durations and relatively balanced `fp_offer_type` preferences.
- **Cluster 1**: High-engagement players with the highest `first_list_price` values and long session durations.
- **Cluster 2**: Players with very short session durations and higher `fp_offer_type` values, potentially overwhelmed or disengaged quickly.

> **Silhouette Score**: `0.47`  
While weaker compared to K-Means, Hierarchical Clustering revealed **sub-clusters**, adding valuable nuance to player behavior.

---

## Predicting Long-Term Engagement

### Random Forest Classifier
**Random Forest** achieved outstanding accuracy for overall prediction:  
- **Accuracy**: `97.65%`  
- **Challenge**: Recall for **active players** remained low at `19%` (due to class imbalance).  

#### Top Features Driving Retention:
1. **`d0_session_duration`**: Players spending more time on Day 1 were more likely to stick around.  
2. **`fp_offer_type`**: Certain offers resonated more effectively.  
3. **`d0_level`**: Progressing further on Day 1 strongly correlated with retention.

---

### Logistic Regression
In comparison, **Logistic Regression** struck a better balance:  
- **Accuracy**: `90.63%`  
- **Recall for active players**: `73%`  

#### Feature Insights:
- **Positive Correlations**:  
  - `is_ever_regular_customer`: Prior purchases predicted stronger loyalty.  
  - `d0_is_purchaser`: Players making early purchases were highly engaged.  
- **Negative Correlations**:  
  - `lt_first_geo_tier`: Some geographic regions showed lower retention.

> **Why it matters**: Logistic Regression is a reliable tool for understanding **what drives player loyalty**.

---

## Implications for Game Developers

### 1. Retention Strategies  
- **Super Fans (Cluster 1)**:  
  - Offer premium content, exclusive deals, and early access features.  
  - Reinforce momentum with milestones and leaderboards.  

- **Casual Players (Cluster 0)**:  
  - Introduce features that turn casual gamers into loyal fans (e.g., daily challenges, personalized rewards).  

- **One-and-Dones (Cluster 2)**:  
  - Simplify onboarding and provide engaging tutorials to hook players early.  

### 2. Offer Optimization  
- Analyze **`fp_offer_type`** performance to fine-tune offers.  
- Use geographic insights to **tailor offers regionally**.  

### 3. Predictive Analytics for Early Intervention  
- Flag **at-risk players** early to provide timely rewards or bonuses.  
- Appreciate high-value players with loyalty perks.

---

## Conclusion

Mobile gaming is as much about **data** as it is about **fun**. By clustering players and predicting engagement, developers can create experiences that resonate with every type of player:

- From **super fans** grinding for achievements  
- To **casual players** seeking a quick escape  

> With these insights, you're not just reacting to player behavior—you're **anticipating it**.  

**Every player's journey starts somewhere. Why not make it unforgettable?** 🚀

---

**Contact**: Joel Saetern  
*Write-up and Code Supported by GPT-4o*

