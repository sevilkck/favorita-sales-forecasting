# **Executive Summary: Actionable Sales Forecasting for Corporación Favorita**

### **Business Context**

Corporación Favorita operates in a high-volume, fast-moving retail environment where accurate short-term demand forecasting is critical to **inventory availability, cost control, and customer satisfaction**. This project evaluated multiple forecasting approaches to identify a **reliable and operationally usable** model for predicting daily sales and supporting store-level planning decisions.



### **Forecasting Approach**

Historical daily sales data from **August 2016 to August 2017** were analyzed using a strictly time-based modeling framework to ensure realistic forward-looking forecasts. Three models were assessed **—ARIMA/SARIMAX, Prophet, and XGBoost—** with performance evaluated using Mean Absolute Error (MAE) and Root Mean Squared Error (RMSE). The analysis prioritized **forecast stability and robustness** over overly complex optimization to reflect real-world deployment conditions.



### **Key Findings**

* **Prophet delivered the most accurate and stable forecasts**, outperforming XGBoost and ARIMA/SARIMAX under a clean evaluation framework.
* Prophet's strength lies in its ability to capture **weekly and annual seasonality**, which are dominant drivers of retail demand at Favorita.
* XGBoost showed potential but required more extensive tuning and feature engineering to outperform Prophet, making it less suitable as an immediate operational baseline.
* SARIMAX improved significantly over plain ARIMA by incorporating weekly seasonality and external regressors (holiday flag, oil price), but still underperformed Prophet and XGBoost.
* Plain ARIMA proved insufficient for capturing the complexity of modern retail demand patterns.



### **Operational Recommendations**

Based on the comparative results, the following recommendations are proposed:


1. **Inventory Planning & Replenishment:**
    - Use **Prophet-based forecasts** as the primary input for **short-term inventory replenishment** (7–30 day horizon).
    - Increase stock levels ahead of **predictable seasonal peaks** (weekends, holidays, promotional periods) identified by the model.
    - Reduce overstock risk by aligning reorder quantities with forecasted demand rather than historical averages.

2. **Store-Level Staffing Optimization**
    - Align **staff scheduling** with forecasted daily sales patterns to ensure adequate coverage during high-demand periods.
    - Reduce labor inefficiencies by scaling staffing down during forecasted low-demand days without impacting service quality.

3. **Promotion & Pricing Strategy**
    - Use forecast baselines to **quantify true promotional uplift**, distinguishing organic demand from promotion-driven spikes.
    - Schedule promotions during forecasted demand troughs to smooth sales volatility and improve capacity utilization.

4. **Waste Reduction & Cost Control**
    - Apply forecasts to **perishable goods planning**, particularly in fresh food categories, to minimize spoilage.
    - Improve supplier ordering accuracy, reducing emergency replenishments and logistics costs.

5. **Advanced Analytics Roadmap**
    - Adopt Prophet as the **default forecasting engine** for operational planning.
    - Pilot **XGBoost models for high-impact product categories** where richer feature sets (promotions, price elasticity, local effects) can be leveraged.
    - Establish a monthly forecast accuracy review to recalibrate models as demand patterns evolve.



### **Strategic Impact**

By implementing a robust and interpretable forecasting solution, Corporación Favorita can transition from reactive planning to **data-driven, proactive decision-making**. The use of Prophet as a baseline forecasting model provides immediate operational value through improved inventory availability, reduced waste, and more efficient workforce planning—while laying the groundwork for future machine learning enhancements.



### **Conclusion**

This project demonstrates that **accurate and operationally reliable forecasting does not require unnecessary complexity**. Under realistic deployment conditions, Prophet provides Corporación Favorita with a practical and scalable solution for improving retail operations today, while more advanced models such as XGBoost can be incrementally introduced to drive additional value in the future.
