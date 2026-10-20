# Inventory & Procurement Planning Simulation

## Overview

An Excel-based operations analytics project that simulates inventory management, supplier evaluation, procurement cost estimation, and replenishment planning for a fictional retail business.

The project demonstrates how spreadsheet-based decision-support tools can help businesses identify low-stock products, compare supplier performance, estimate purchasing costs, and evaluate the impact of changing demand and delivery lead times.

**Data disclaimer:** All product, supplier, demand, and cost data are synthetic and created for educational and portfolio purposes. The project does not use real company records.

## Business Objectives

- Identify products at or below their reorder points.
- Calculate suggested replenishment quantities.
- Evaluate suppliers based on price, lead time, quality, and delivery reliability.
- Estimate inventory holding, purchasing, and order-processing costs.
- Assess how higher demand and supplier delays affect replenishment requirements.
- Present inventory and procurement insights through an Excel dashboard.

## Tools & Technologies

- Microsoft Excel
- Excel formulas and structured tables
- Conditional formatting
- Excel charts and KPI reporting
- Weighted supplier scoring
- Scenario analysis
- Inventory and procurement cost modeling

## Workbook Structure

| Worksheet | Description |
|---|---|
| `Start_Here` | Project instructions, workflow, assumptions, and limitations |
| `Inventory_Master` | 30 product SKUs, stock levels, daily demand, lead times, safety stock, reorder points, and inventory values |
| `Supplier_Comparison` | 90 synthetic supplier quotes, with three supplier options per SKU and weighted performance scores |
| `Cost_Assumptions` | Editable assumptions for holding costs, order-processing costs, stockout penalties, demand changes, and delivery delays |
| `Replenishment_Plan` | Reorder status, target stock, suggested order quantities, supplier minimum order quantities (MOQs), and estimated purchase costs |
| `Scenario_Analysis` | Baseline, high-demand, and supplier-delay scenarios |
| `Cost_Analysis` | Estimated inventory holding, purchasing, order-processing, and illustrative stockout-risk costs |
| `Management_Dashboard` | Summary KPIs, inventory category analysis, and replenishment status charts |

## Methodology

### 1. Reorder Point

Calculates the stock level at which replenishment should be considered.

**Reorder Point = Average Daily Demand × Supplier Lead Time + Safety Stock**

### 2. Inventory Valuation

Estimates the value of inventory currently held.

**Inventory Value = Current Stock × Unit Cost**

### 3. Target Stock and Replenishment

Estimates the target inventory level using expected demand during lead time, safety stock, and an additional target stock-cover period.

**Base Order Quantity = MAX(0, Target Stock − Current Stock)**

The suggested order quantity is then adjusted to respect the selected supplier's minimum order quantity when an order is required.

### 4. Supplier Evaluation

Compares three supplier options per product using a weighted scoring model:

| Criterion | Weight |
|---|---:|
| Price | 40% |
| Lead time | 25% |
| Quality / defect rate | 20% |
| On-time delivery | 15% |
| **Total** | **100%** |

Supplier scores are normalized within each product's three supplier quotes. The weights represent illustrative business priorities rather than universal industry standards.

### 5. Cost Estimation

- **Annual holding cost estimate:** Current inventory value × assumed annual holding-cost rate.
- **Purchase cost estimate:** Suggested order quantity × selected supplier's unit price.
- **Order-processing cost estimate:** Number of suggested purchase orders × assumed processing cost per order.
- **Stockout-risk cost:** A simplified illustrative estimate based on inventory shortfall relative to the reorder point and an assumed penalty per unit. It is not a forecast of actual lost sales.

### 6. Scenario Analysis

Evaluates three operating conditions:

- **Baseline:** Original demand and supplier lead times.
- **High demand:** Demand increases by 30%.
- **Supplier delay:** Delivery lead time increases by four days.

The scenarios illustrate how changes in demand and supplier performance may affect replenishment needs.

## Key Findings

*Complete this section after reviewing the recalculated workbook results.*

- **Inventory profile:** Identify the product category with the highest inventory value.
- **Replenishment needs:** Report the number of SKUs flagged for reorder and identify products requiring attention.
- **Supplier trade-offs:** Compare supplier scores, prices, lead times, and MOQs.
- **Scenario impact:** Compare replenishment requirements across the three scenarios.
- **Cost implications:** Report estimated purchase and annual holding costs using the stated assumptions.

## Business Recommendations

Recommendations should be based on the calculated results. Potential areas for improvement include:

- Prioritizing products at or below their reorder points.
- Reviewing safety stock for products exposed to higher demand or longer delivery times.
- Considering total supplier performance rather than unit price alone.
- Reviewing minimum order quantities against inventory needs and storage constraints.
- Monitoring inventory value and procurement spending to support purchasing decisions.

## Limitations

- All data is synthetic and has not been validated against real operational records.
- Average daily demand is assumed to be stable within each scenario; seasonality and probabilistic demand are not modeled.
- Supplier scores depend on chosen weights and simplified normalization methods.
- Cost estimates use illustrative assumptions and do not fully account for freight, taxes, discounts, supplier capacity, or cash-flow constraints.
- The stockout-risk estimate is a simplified proxy, not a reliable prediction of actual losses.
- Scenario outputs are model-based estimates and should not be used for real purchasing decisions without validation.

## Conclusion

This project demonstrates how Excel can support inventory control, supplier evaluation, replenishment planning, procurement cost estimation, and scenario-based business decision-making. It connects operational data with practical business rules and management reporting in a structured, spreadsheet-based decision-support model.

## Author

**Namratha Chilukuri**
