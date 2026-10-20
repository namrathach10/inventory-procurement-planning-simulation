# Inventory & Procurement Planning — Analysis Report

## 1. Executive Summary

This project presents an Excel-based inventory and procurement planning simulation for a fictional retail business. The model includes 30 stock-keeping units (SKUs) across five product categories and 90 synthetic supplier quotations, with three supplier options evaluated for each SKU.

Using the workbook's input data and stated formulas, the model estimates total current inventory value at **₹21,81,880**. Stationery accounts for the largest share of inventory value at **₹7,93,350 (36.4%)**, followed by Electronics at **₹6,95,430 (31.9%)**. The baseline replenishment analysis flags **11 of 30 SKUs** at or below their reorder points. Under the high-demand scenario, this increases to **12 SKUs**, and under the supplier-delay scenario it increases to **15 SKUs**.

The model estimates a baseline suggested purchase cost of **₹14,09,718.99**, an annual holding cost of **₹4,80,013.60**, and order-processing costs of **₹11,700** for 26 suggested purchase orders. These are scenario estimates based on synthetic data and assumptions, not actual business expenses.

**Calculation note:** The uploaded workbook contains formulas but does not contain cached calculated values for many formula cells. The results in this report were independently calculated from the workbook's input data using the formulas and assumptions documented in the file. Open the workbook in desktop Excel, allow recalculation, and verify the results before treating them as final.

**Data disclaimer:** All product, supplier, demand, and cost data are synthetic and intended for educational and portfolio purposes. The project does not use real company records.

## 2. Business Problem and Objectives

Businesses need enough stock to meet customer demand without tying up excessive working capital in inventory. Ordering too late can increase stockout risk and disrupt service, while ordering too early or in excessive quantities can increase holding costs and storage requirements.

Supplier selection also involves trade-offs among unit price, lead time, quality, delivery reliability, and minimum order quantity (MOQ).

The objectives of this project are to:

- Identify products at or below their reorder points.
- Estimate replenishment quantities using demand, lead time, safety stock, and target stock cover.
- Compare suppliers using a weighted evaluation model.
- Estimate current inventory value, purchase costs, holding costs, and order-processing costs.
- Assess the effects of higher demand and supplier delays.
- Present decision-support metrics through an Excel dashboard.

## 3. Data and Methodology

### 3.1 Inventory Analysis

The dataset contains 30 synthetic products across Electronics, Home, Lifestyle, Stationery, and Fitness. Each product includes unit cost, current stock, average daily demand, lead time, and safety stock.

**Reorder Point = Average Daily Demand × Lead Time + Safety Stock**

**Inventory Value = Current Stock × Unit Cost**

Products with current stock at or below the reorder point are flagged for replenishment review.

### 3.2 Supplier Evaluation

The workbook contains 90 supplier quotations, with three options per SKU. Suppliers are scored using the following weights:

| Criterion | Weight |
|---|---:|
| Price | 40% |
| Lead time | 25% |
| Quality / defect rate | 20% |
| On-time delivery | 15% |
| **Total** | **100%** |

Price, lead-time, and defect-rate scores are normalized relative to the three supplier options for each product. On-time delivery is scored using the simulated delivery percentage. The score reflects the chosen weights and simulated data; it is not a universal measure of supplier quality.

### 3.3 Replenishment Planning

Target stock is calculated from demand during lead time, safety stock, and an additional target stock-cover period.

**Base Order Quantity = MAX(0, Target Stock − Current Stock)**

When an order is needed, the suggested quantity is adjusted to meet the selected supplier's minimum order quantity. The purchase-cost estimate is calculated using the adjusted order quantity and selected supplier unit price.

These outputs are planning estimates, not automatic purchasing instructions. Real decisions would also consider cash availability, storage capacity, actual supplier terms, and business priorities.

### 3.4 Cost Analysis

The model uses the following assumptions:

| Assumption | Value |
|---|---:|
| Annual holding-cost rate | 22% |
| Order-processing cost per purchase order | ₹450 |
| Illustrative stockout penalty | ₹180 per unit |
| High-demand multiplier | 1.30 (30% increase) |
| Additional supplier delay | 4 days |
| Additional target stock cover | 14 days |

Annual holding cost is estimated as current inventory value multiplied by the annual holding-cost rate. Order-processing cost is estimated as the number of suggested purchase orders multiplied by ₹450.

The stockout-risk estimate is a simplified proxy based on the positive gap between reorder point and current stock. It is not a forecast of actual stockouts or lost sales.

### 3.5 Scenario Analysis

Three operating scenarios were evaluated:

1. **Baseline:** Original demand and supplier lead times.
2. **High demand:** Average daily demand increases by 30%.
3. **Supplier delay:** Supplier lead time increases by four days.

For each scenario, the model recalculates reorder points and estimated suggested order quantities.

## 4. Findings and Results

### 4.1 Inventory Profile

The total current inventory value is estimated at **₹21,81,880**.

| Product category | Inventory value | Share of total |
|---|---:|---:|
| Stationery | ₹7,93,350 | 36.4% |
| Electronics | ₹6,95,430 | 31.9% |
| Fitness | ₹3,66,140 | 16.8% |
| Home | ₹2,05,940 | 9.4% |
| Lifestyle | ₹1,21,020 | 5.5% |
| **Total** | **₹21,81,880** | **100.0%** |

Stationery has the highest inventory value, representing approximately 36.4% of the total. Electronics is the second-largest category at approximately 31.9%. Together, these two categories account for approximately 68.3% of current inventory value and are therefore important areas for inventory monitoring.

### 4.2 Replenishment Requirements

The baseline model flags **11 of 30 SKUs** at or below their reorder points.

The largest current-stock shortfalls relative to reorder points are:

| SKU | Product | Current stock | Reorder point | Shortfall |
|---|---|---:|---:|---:|
| SKU025 | Desk Organizer | 45 | 255 | 210 |
| SKU020 | Bedside Organizer | 182 | 252 | 70 |
| SKU022 | Headphones | 100 | 165 | 65 |
| SKU007 | Storage Box | 40 | 70 | 30 |
| SKU012 | Backpack | 18 | 40 | 22 |
| SKU027 | Reusable Bag | 52 | 72 | 20 |
| SKU019 | Lunch Container | 126 | 144 | 18 |
| SKU023 | Packing Cubes | 92 | 108 | 16 |
| SKU018 | Running Bottle | 42 | 52 | 10 |
| SKU029 | Webcam Cover | 51 | 60 | 9 |
| SKU009 | Travel Mug | 85 | 88 | 3 |

Desk Organizer has the largest gap relative to its reorder point, with stock 210 units below the calculated threshold. It should receive particular attention in the model's replenishment review. The shortfall is a planning signal, not a direct measure of confirmed lost sales.

### 4.3 Supplier Trade-offs

The supplier comparison illustrates that the lowest unit price does not always correspond to the highest weighted score.

For example, for **SKU002 — USB-C Cable**:

| Metric | Supplier B (lowest price) | Supplier C (highest score) |
|---|---:|---:|
| Unit price | ₹167.32 | ₹199.18 |
| Lead time | 11 days | 6 days |
| Defect rate | 4.35% | 1.98% |
| On-time delivery | 98.5% | 95.1% |
| Weighted score | 75.24 | 88.70 |
| Minimum order quantity | 50 units | 25 units |

Supplier B offers the lowest price, but has a longer lead time and a higher simulated defect rate. Supplier C has the highest weighted score under the selected scoring method and a lower MOQ. The model therefore favors Supplier C for this product, even though its unit price is higher.

This example demonstrates why procurement decisions should consider multiple criteria rather than unit price alone. The preferred supplier should still be checked against actual business needs and commercial terms.

### 4.4 Scenario Sensitivity

The number of products at or below their scenario-specific reorder points changes as follows:

| Scenario | SKUs at or below reorder point | Products needing a suggested order under the model |
|---|---:|---:|
| Baseline | 11 of 30 | 26 |
| High demand (+30%) | 12 of 30 | 30 |
| Supplier delay (+4 days) | 15 of 30 | 30 |

Under high demand, the number of SKUs at or below the reorder point rises from 11 to 12. Under supplier delays, it rises to 15. Both scenarios result in all 30 products having a positive suggested order quantity under the workbook's target-stock rule.

The suggested order counts are higher than the reorder flags because the target stock formula includes an additional 14 days of stock cover. A product can therefore be above its reorder point but still have a positive order quantity to reach the model's target stock level.

The scenario model also estimates total suggested purchase costs of approximately:

| Scenario | Estimated suggested purchase cost |
|---|---:|
| Baseline | ₹14,09,718.99 |
| High demand (+30%) | ₹22,69,581.96 |
| Supplier delay (+4 days) | ₹19,78,422.56 |

The higher-demand scenario produces the largest estimated purchase cost because the model increases daily demand by 30%. The supplier-delay scenario also increases the modeled purchase requirement because it extends lead time by four days.

**Quantity caveat:** The high-demand scenario can produce fractional suggested unit quantities because the demand multiplier is 1.30. In a real inventory model, order quantities should be rounded up to whole units and then checked against MOQ. The high-demand cost above is calculated from the workbook's current formula logic and should be treated as an indicative estimate until this is corrected.

### 4.5 Cost Implications

The baseline cost estimates are:

| Metric | Estimated value | Interpretation |
|---|---:|---|
| Current inventory value | ₹21,81,880.00 | Value of stock currently held, using the unit costs in the inventory master |
| Suggested purchase cost | ₹14,09,718.99 | Estimated product purchase spend for baseline suggested orders |
| Annual holding cost | ₹4,80,013.60 | Current inventory value multiplied by the assumed 22% annual holding-cost rate |
| Order-processing cost | ₹11,700.00 | 26 suggested purchase orders × ₹450 |
| Illustrative stockout-risk cost | ₹85,140.00 | 473 units of aggregate reorder-point shortfall × ₹180 |

These figures represent different cost concepts and should not be added together as if they were all actual expenses in the same period. Current inventory value is the value of stock already held; suggested purchase cost relates to potential future orders; annual holding cost is an annualized estimate; and the stockout-risk cost is a simplified indicator.

## 5. Business Recommendations

Based on the modeled results, the following recommendations are appropriate for further review:

1. **Prioritize the largest replenishment gaps.** Desk Organizer has the largest shortfall relative to its reorder point, followed by Bedside Organizer and Headphones. Review their demand, supplier lead times, and target stock assumptions.
2. **Monitor high-value categories.** Stationery and Electronics together account for approximately 68.3% of current inventory value. These categories deserve particular attention in inventory-value reporting.
3. **Use balanced supplier selection.** The USB-C Cable example shows that the lowest-price supplier is not necessarily the highest-scoring option. Consider delivery time, quality, reliability, and MOQ alongside price.
4. **Plan for demand changes.** The high-demand scenario increases the number of SKUs at or below reorder point from 11 to 12 and raises estimated purchase requirements. Safety stock and target stock assumptions should be reviewed for products sensitive to demand changes.
5. **Account for delivery delays.** The supplier-delay scenario raises the number of SKUs at or below reorder point to 15. Products with longer lead times may require earlier reorder triggers or revised safety stock.
6. **Validate suggested order quantities.** Check MOQ, whole-unit rounding, storage capacity, and cash availability before translating suggested quantities into purchase orders.
7. **Review model assumptions.** The supplier weights, holding-cost rate, order-processing cost, and stockout penalty should be adjusted using actual business evidence before the model is used operationally.

## 6. Limitations

- All data is synthetic and has not been validated against real operational records.
- Average daily demand is treated as stable within each scenario; seasonality and probabilistic demand are not modeled.
- Supplier performance is simulated, and supplier rankings depend on chosen weights and normalization rules.
- Cost estimates are illustrative and do not fully account for freight, taxes, discounts, supplier capacity, cash-flow constraints, or storage limits.
- The stockout-risk estimate is a simplified reorder-point shortfall proxy, not a reliable forecast of actual lost sales.
- High-demand scenario quantities can be fractional in the current model and should be rounded up to whole units before practical use.
- The workbook's formula cells should be recalculated and checked in desktop Excel before final publication.

The results are suitable for demonstrating spreadsheet-based analytical methods, but should not be used for live procurement decisions without validation and further development.

## 7. Conclusion

This project demonstrates how Excel-based decision support can connect inventory records, supplier evaluation, replenishment rules, cost assumptions, and scenario planning within a single model.

The calculations identify Stationery as the category with the highest current inventory value, flag 11 SKUs for baseline replenishment review, and show that higher demand and supplier delays increase modeled replenishment pressure. The supplier comparison also illustrates the trade-off between unit price and broader supplier performance.

The findings are based on synthetic data and specified assumptions. Their value lies in showing a structured analytical approach: quantify inventory positions, compare suppliers transparently, test alternative scenarios, and translate the results into business recommendations.

## Tools Used

- Microsoft Excel
- Spreadsheet formulas and structured tables
- Conditional formatting and charts
- Weighted supplier scoring
- Inventory and procurement cost modeling
- Scenario analysis and KPI reporting
