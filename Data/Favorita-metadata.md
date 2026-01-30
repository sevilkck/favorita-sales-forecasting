# Favorita Grocery Sales Metadata

This dataset contains historical sales, product information, store metadata, holidays, oil prices, and transaction counts for Corporación Favorita supermarkets in Ecuador. It is used to build time‑series forecasting models that predict daily unit sales for thousands of store–item combinations.

---

## Project Scope

For the purpose of this project, I will only use these **six** files:

- `holidays_events.csv`
- `items.csv` 
- `oil.csv` 
- `stores.csv`
- `train.csv`
- `transactions.csv`  

The remaining files (`test.csv`, `sample_submission.csv`) were part of the Kaggle competition workflow, and **not required** for this analysis.

---

## Column Descriptions

Below is a breakdown of the columns in every file, including their data types and descriptions.

### `holidays_events.csv`

| Column | Type | Description |
| --- | --- | --- |
| **date** | `date` | Calendar date |
| **type** | `string` | Holiday/event type |
| **locale** | `string` | National, Regional, Local |
| **locale_name** | `string` | Region/city name |
| **description** | `string` | Holiday/event name |
| **transferred** | `bool` | Whether the holiday was moved |

**Notes:**  
- `transferred` holidays officially fall on that calendar day, but was moved to another date by the government.  
- To find the day that it was actually celebrated, look for the corresponding row where `type` is "Transfer".
- Where `type` is "Bridge", these are extra days that are added to a holiday (e.g., to extend the break across a long weekend).
- Days not normally scheduled for work that are used to pay back 'Bridge' days are indicated with `type` "Work Day".
- "Additional" `type` extend existing holidays.

---

### `items.csv`

| Column | Type | Description |
| --- | --- | --- |
| **item_nbr** | `int` | Product ID |
| **family** | `string` | Product family/category |
| **class** | `int` | Product class |
| **perishable** | `int` | Whether the item is perishable |

**Notes:**  
-  Items marked as `perishable` have a score weight of **1.25**; otherwise, the weight is **1.0**.

---

### `oil.csv`

| Column | Type | Description |
| --- | --- | --- |
| **date** | `date` | Calendar date |
| **dcoilwtico** | `float` | Daily oil price |

### `stores.csv`

| Column | Type | Description |
| --- | --- | --- |
| **store_nbr** | `int` | Store ID |
| **city** | `string` | City name |
| **state** | `string` | Province/state |
| **type** | `string` | Store type |
| **cluster** | `int` | Grouping of similar stores |

---

### `train.csv`

| Column | Type | Description |
| --- | --- | --- |
| **id** | `int` | Row identifier used by Kaggle (not a transaction ID) |
| **date** | `date` | Calendar date |
| **store_nbr** | `int` | Store identifier |
| **item_nbr** | `int` | Product identifier |
| **unit_sales** | `float` | Units sold |
| **onpromotion** | `bool` | Whether the item was on promotion |

**Notes:**  
- No rows exist for store–item combinations with zero sales.  
- Negative values represent returns.
- Approximately 16% of the `onpromotion` values are missing.

---

### `transactions.csv`

| Column | Type | Description |
| --- | --- | --- |
| **date** | `date` | Calendar date |
| **store_nbr** | `int` | Store ID |
| **transactions** | `int` | Number of transactions that day |

---

## General Notes About the Dataset

- `unit_sales` is the target variable.
- There is no information as to whether or not an item was in stock for a particular store on a specific date to explain zero `unit_sales`.
- Ecuador is an oil-dependent country and its economical health is highly vulnerable to shocks in oil prices.
- Wages in the public sector are paid every two weeks on the 15<sup>th</sup> and on the last day of the month. Supermarket sales could be affected by this.
- A magnitude 7.8 earthquake struck Ecuador on 16 April 2016. People rallied in relief efforts, donating water and other first need products, which greatly affected supermarket sales for several weeks after the earthquake.
