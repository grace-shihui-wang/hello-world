# Data Dictionary for Exec 2.0 Dashboard 
## Overview
This data dictionary provides key business KPIs (e.g. revenue, sessions) which are used in [Exec2.0 dashboard] (https://10ay.online.tableau.com/#/site/alo/views/ExecDash2_0DateRangeTabDRAFT/Yesterday) to track Alo's digital performance. We listed the key terms here in dbt doc for DE's visibility and to help DE-DA-DS collaboration.

## Referenced by 
[Tableau Doc] https://10ay.online.tableau.com/t/alo/views/DataDictionary/ExecutiveDashboardDataDictionary

## Depend on
DA's inputs and

[Terms' Reference] https://alodigital.atlassian.net/wiki/spaces/AD/pages/1572044846/Dashboard+Metrics+Data+Dictionary+-+Alo+Yoga+WIP


## Column Descriptions

### YESTERDAY View

| Category | KPI Name | Definition | Source | Original Name | Table |
|---|---|---|---|---|---|
| Revenue | Revenue | Total monetary value of orders placed in digital space which gets reported on **initial** order creation/order_processed_date_pst, excluding cancellations, discounts, and duties. Digital revenue further excludes SDD (Same-Day Delivery), BOPIS (Buy Online, Pick Up In Store), and SFS (Ship from Store, Digital revenue but excluded here) orders. | Shopify | revenue_less_sfs | `sil_post_alo_daily_metrics` |
| Revenue | Revenue vs LY | % change of **YESTERDAY’S** Revenue (exclude SDD, BOPIS) vs same date last year’s revenue, in fiscal calendar | Shopify | revenue | `sil_post_alo_daily_metrics` |
| Revenue | Revenue vs Budget \| Target | % change between actual revenue and budget (target set by Finance) \| Target (stretch target by Data Science) | Shopify, Forecasting | target; stretch_target | `sil_post_alo_daily_metrics` |
| Revenue | SFS Revenue | Digital Revenue Ship From Store | Shopify | sfs_revenue | `sil_post_alo_daily_metrics` |
| Spend | Spend | Digital Spend (e.g., paid POAs) | Shopify | spend | `sil_post_alo_daily_metrics` |
| Spend | Spend vs LY | % change of **YESTERDAY’S** Spend vs same date last year in fiscal calendar | Shopify | spend | `sil_post_alo_daily_metrics` |
| Spend | Paid ROAS | Paid Attributed Revenue / Total Spend | Shopify | paid_roas | paid_revenue_adj from `silver.sil_ga4_last_click_performance_daily` and `silver.sil_post_channel_performance_daily_rollup` → later migrate to `sil_post_alo_daily_metrics` |
| Spend | Paid ROAS vs LY | % change of **YESTERDAY’S** Paid ROAS vs same date last year in fiscal calendar | Shopify | paid_roas | same as above |
| Spend | Omni ROAS | Revenue (exclude SDD/BOPIS/SFS) / Total performance marketing investment | Shopify | roas | `silver.sil_post_channel_performance_daily_rollup` |
| Spend | Omni ROAS vs LY | % change of **YESTERDAY’S** Omni ROAS vs same date last year in fiscal calendar | Shopify | roas | `sil_post_alo_daily_metrics` |
| Customer | Customers Acquired | New customers who made their first digital purchase at Alo | Shopify | new_customers | `sil_post_alo_daily_metrics` |
| Customer | Customers Acq'd vs LY | % change of **YESTERDAY’S** Customers Acquired vs same date last year in fiscal calendar | Shopify | new_customers | `sil_post_alo_daily_metrics` |
| Sessions | Sessions | Number of user visits within a time period. A session begins when a user lands on the site and ends after 30 minutes of inactivity or when they leave/close the browser. | GA | sessions | `sil_post_alo_daily_metrics` |
| Sessions | Sessions vs LY | % change of **YESTERDAY’S** Sessions vs same date last year in fiscal calendar | GA | sessions | `sil_post_alo_daily_metrics` |
| CVR | CVR | Conversion Rate (Orders/Sessions) | Shopify/GA | orders/sessions | `sil_post_alo_daily_metrics` |
| CVR | CVR vs LY | % change of **YESTERDAY’S** CVR vs same date last year in fiscal calendar | Shopify/GA | orders/sessions | `sil_post_alo_daily_metrics` |
| AOV | AOV | Average Order Value (Revenue excluding SDD/BOPIS Orders) | Shopify | revenue/orders | `sil_post_alo_daily_metrics` |
| AOV | AOV vs LY | % change of **YESTERDAY’S** AOV vs same date last year in fiscal calendar | Shopify | revenue/orders | `sil_post_alo_daily_metrics` |
| Omni | SFS | SFS Orders \| Revenue | Shopify | sfs_orders, sfs_revenue | `sil_post_alo_daily_metrics` |
| Omni | SDD | SDD Orders \| Revenue (Same Day Delivery) | Shopify | sdd_orders, sdd_revenue | `sil_post_alo_daily_metrics` |
| Omni | BOPIS | BOPIS Orders \| Revenue (Buy Online Pick Up in Store) | Shopify | bopis_orders, bopis_revenue | `sil_post_alo_daily_metrics` |



## Related Models
- **Upstream**: mainly from sil_post_alo_daily_metrics
