# User Loyalty Analysis for Yandex Afisha

## Project Overview
This project analyzes user loyalty and purchasing behavior in the Yandex Afisha ticket booking service. The analysis is based on 290,611 transaction records with 14 features, aiming to identify patterns that drive user engagement and retention.

## Business Goals
- Identify promising customers and facilitate their platform transition through personalized offers
- Optimize advertising campaigns to reduce order returns
- Optimize marketing costs and improve customer retention
- Understand user behavior patterns to enhance service quality

## Data Description
The dataset contains information about user orders with the following features:
- `user_id` - Unique user identifier
- `device_type_canonical` - Device type (mobile/desktop)
- `order_id` - Unique order identifier
- `order_dt` - Order creation date
- `order_ts` - Order creation timestamp
- `currency_code` - Payment currency
- `revenue` - Order revenue
- `tickets_count` - Number of tickets purchased
- `days_since_prev` - Days since previous purchase (null for single purchases)
- `event_id` - Unique event identifier
- `service_name` - Ticket operator name
- `event_type_main` - Main event type (theater, concert, etc.)
- `region_name` - Event region
- `city_name` - Event city

## Data Processing
### Data Cleaning
- Converted revenue to single currency (RUB) in new column `revenue_rub`
- Filtered 2,917 records with anomalous ticket prices and quantities
- Normalized text columns: `city_name`, `region_name`, `event_type_main`, `service_name`
- Handled missing values in `days_since_prev` (single purchases)
- Reduced data type precision for `tickets_count`
- Verified value ranges and data validity

### Final Dataset
- **Initial**: 290,611 records, 14 columns
- **After filtering**: 21,849 users → 20,146 users (after outlier removal)

## Key Findings

### User Behavior Patterns
- **41.5%** of users have only one purchase
- **'Билеты без проблем'** is the dominant ticket operator (**23.86%** market share)
- Typical orders contain **2-3 tickets**
- **Concerts** are the most popular first purchase category (**44%** vs 25% for "Other")

### Device and Regional Preferences
- **83%** of first purchases are made via **mobile devices**
- Top regions for first purchases:
  - **Каменевский регион**: 32.43%
  - **Североярская область**: 17.29%

### Temporal Patterns
- Peak new orders occur on **Friday and Saturday**
- Highest repeat purchase probability for orders placed on **Monday and Wednesday**
- Optimal interval between orders: **4-7 days**

### Customer Loyalty Insights
- **70.61%** repeat purchase rate for users buying 2-3 tickets
- Repeat purchase likelihood is higher when revenue is close to average values
- Strong correlation (0.71) between number of orders and average days between orders

## Recommendations

### Platform Optimization
1. **Focus on mobile experience** - 83% of first purchases come from mobile devices
2. **Target key regions** - Concentrate marketing efforts on Каменевский регион and Североярская область
3. **Single-ticket purchasers** - Lower return probability suggests potential for loyalty programs

### Marketing Strategy
1. **Weekend campaigns** - Increase advertising on Friday-Saturday during peak ordering periods
2. **Retention programs** - Develop "second purchase" incentives for 41.5% single-purchase users
3. **Optimal timing** - Send reminders/promotions within 4-7 day intervals
4. **Pricing strategy** - Maintain revenue close to average values for better retention

### Customer Engagement
1. **Personalized offers** for Monday/Wednesday first-time purchasers
2. **Push notifications/email campaigns** during optimal re-engagement windows
3. **Lifetime value focus** - Leverage correlation insights for long-term customer development

## Technical Implementation
- SQL queries for data extraction from `data-analyst-afisha` database
- Python data processing with pandas
- Statistical analysis and correlation studies
- Data visualization for pattern identification