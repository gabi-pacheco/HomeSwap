# HomeSwap Customer Churn Analysis

This project is the culmination of a 400-hour Data Analytics bootcamp at Le Wagon.

You can access the streamed presentation [here](https://youtu.be/3r17zuc80HY).

You can see the dashboard [here](1_homeswap_overview.pdf).

**Mission:** Identify the factors contributing to subscriber churn and provide actionable insights based on this analysis.

## Team Members
- [Anna Lazarieva](https://github.com/annalazarieva)
- [Gabriella Pacheco](https://github.com/gabriellapacheco)
- [Núria M. Martí](https://github.com/nuriamarti)

## Technologies and Methods Used
- Python (Google Colab, Jupyter Notebooks)
- SQL (Google BigQuery)
- Data Visualization (Power BI)
- Machine Learning and Statistical Testing

## Overview
This project analyzed data from HomeSwap, a community where subscribers swap their residences and enjoy unlimited travel accommodations through an annual membership.

Members can participate in reciprocal exchanges or use guest points for non-reciprocal exchanges. Points are earned by hosting other members and can be redeemed to stay in other homes. While basic membership is free, activating an annual membership is required to complete an exchange.

HomeSwap operates on a subscription-based model, making churn rate a critical factor in business growth. By understanding the drivers of churn, the company can develop targeted strategies to reduce it.

## Task
The HomeSwap analytics team was tasked with developing a business intelligence dashboard to provide actionable insights into the factors correlated with churn.

To achieve this, our team:
1. Defined what constitutes a "churner" based on the available data.
2. Formulated hypotheses regarding the factors influencing churn and validated them using statistical methods and machine learning models.
3. Extracted actionable insights and presented them in a deliverable dashboard.

## The Data

The dataset for this analysis comprised two files: one containing home exchange information and one containing subscription information over nearly three years, from 2019 to 2021.

- **Exchanges:** The raw dataset contained over 11 million rows of information on customer interactions and home swaps. Each row corresponds to a `conversation_id` between a potential guest and a host, involved in a specific home swap (`exchange_id`). Multiple `conversation_ids` can be associated with a single `exchange_id`. The dataset allows for analysis from multiple dimensions, including demographics, conversation start and swap dates, stay details (number of nights and guests), and information about the swap, residence, and home type.

- **Subscriptions:** The raw dataset contained 100k rows of user subscription data, including subscriptions from 2019 to 2021. Each row represents a single subscription; if a user renewed their subscription within the timeframe, they have one row per year of active membership. This dataset also includes demographic and financial details.

The relationship between these tables is many-to-many, connected only by the `user_id` in the Subscriptions table and the `guest_id` or `host_id` in the Exchanges table. This presented a significant challenge:

- A user can have multiple subscriptions, requiring aggregation before joining tables.
- Each row in the Exchanges table contains both `guest_id` and `user_id`, so merging the tables necessitated analyzing the data from one of these perspectives.
