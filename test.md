# Data Dictionary for Exec 2.0 Dashboard 
## Overview
This data dictionary provides key business KPIs (e.g. revenue, sessions) which are used in [Exec2.0 dashboard](https://10ay.online.tableau.com/#/site/alo/views/ExecDash2_0DateRangeTabDRAFT/Yesterday) to track Alo's digital performance. It lives in dbt docs to increase visibility for DE and to support DE-DA-DS collaboration.

## Related/Reference
- [Tableau Doc](https://10ay.online.tableau.com/t/alo/views/DataDictionary/ExecutiveDashboardDataDictionary)

- [Terms' Reference](https://alodigital.atlassian.net/wiki/spaces/AD/pages/1572044846/Dashboard+Metrics+Data+Dictionary+-+Alo+Yoga+WIP)

## Conventions & Notes 
- **YESTERDAY** refers to the prior fiscal day unless otherwise noted.
- **Digital Revenue** excludes SDD (Same-Day Delivery), BOPIS (Buy Online, Pick Up In Store), and SFS (Ship from Store) orders where specified.
- All timestamps use `order_processed_date_pst` for Shopify metrics unless stated.

## Column Descriptions

### YESTERDAY View

| Category | KPI Name | Definition | Source | Original Name | Upstream Table |
|---|---|---|---|---|---|
| Revenue | Revenue | Total monetary value of orders placed in digital space reported on **initial** order creation/`order_processed_date_pst`; excludes cancellations, discounts, duties; **excludes SDD/BOPIS/SFS**. | Shopify | `revenue_less_sfs` | `sil_post_alo_daily_metrics` |
| Revenue | Revenue vs LY | % change of **YESTERDAY’s** Revenue (excl. SDD/BOPIS) vs same fiscal date last year. | Shopify | `revenue` | `sil_post_alo_daily_metrics` |
| Revenue | Revenue vs Budget \| Target | % change vs Budget (Finance) \| vs Target (stretch target by DS). | Shopify, Forecasting | `target`; `stretch_target` | `sil_post_alo_daily_metrics` |
| Revenue | SFS Revenue | Digital revenue from Ship From Store. | Shopify | `sfs_revenue` | `sil_post_alo_daily_metrics` |
| Spend | Spend | Digital performance-marketing spend (paid media). | Shopify | `spend` | `sil_post_alo_daily_metrics` |
| Spend | Spend vs LY | % change of **YESTERDAY’s** Spend vs same fiscal date last year. | Shopify | `spend` | `sil_post_alo_daily_metrics` |
| Spend | Paid ROAS | Paid Attributed Revenue / Total Spend. | Shopify | `paid_roas` | `paid_revenue_adj` from `silver.sil_ga4_last_click_performance_daily`, `silver.sil_post_channel_performance_daily_rollup` *(planned migration to `sil_post_alo_daily_metrics`)* |
| Spend | Paid ROAS vs LY | % change of **YESTERDAY’s** Paid ROAS vs same fiscal date last year. | Shopify | `paid_roas` | same as above |
| Spend | Omni ROAS | (Revenue excl. SDD/BOPIS/SFS) / Total performance-marketing investment. | Shopify | `roas` | `silver.sil_post_channel_performance_daily_rollup` |
| Spend | Omni ROAS vs LY | % change of **YESTERDAY’s** Omni ROAS vs same fiscal date last year. | Shopify | `roas` | `sil_post_alo_daily_metrics` |
| Customer | Customers Acquired | New customers who made their first digital purchase at Alo. | Shopify | `new_customers` | `sil_post_alo_daily_metrics` |
| Customer | Customers Acq’d vs LY | % change of **YESTERDAY’s** Customers Acquired vs same fiscal date last year. | Shopify | `new_customers` | `sil_post_alo_daily_metrics` |
| Sessions | Sessions | Number of user visits; a session begins on site entry and ends after 30 minutes of inactivity or browser exit. | GA | `sessions` | `sil_post_alo_daily_metrics` |
| Sessions | Sessions vs LY | % change of **YESTERDAY’s** Sessions vs same fiscal date last year. | GA | `sessions` | `sil_post_alo_daily_metrics` |
| CVR | CVR | Conversion Rate = Orders / Sessions. | Shopify / GA | `orders/sessions` | `sil_post_alo_daily_metrics` |
| CVR | CVR vs LY | % change of **YESTERDAY’s** CVR vs same fiscal date last year. | Shopify / GA | `orders/sessions` | `sil_post_alo_daily_metrics` |
| AOV | AOV | Average Order Value = Revenue (excl. SDD/BOPIS) / Orders. | Shopify | `revenue/orders` | `sil_post_alo_daily_metrics` |
| AOV | AOV vs LY | % change of **YESTERDAY’s** AOV vs same fiscal date last year. | Shopify | `revenue/orders` | `sil_post_alo_daily_metrics` |
| Omni | SFS | SFS Orders \| Revenue. | Shopify | `sfs_orders`, `sfs_revenue` | `sil_post_alo_daily_metrics` |
| Omni | SDD | SDD Orders \| Revenue (Same-Day Delivery). | Shopify | `sdd_orders`, `sdd_revenue` | `sil_post_alo_daily_metrics` |
| Omni | BOPIS | BOPIS Orders \| Revenue (Buy Online, Pick Up in Store). | Shopify | `bopis_orders`, `bopis_revenue` | `sil_post_alo_daily_metrics` |


## Related Models
- **Primary source:** `sil_post_alo_daily_metrics`  
- **Also referenced (Paid ROAS):** `silver.sil_ga4_last_click_performance_daily`, `silver.sil_post_channel_performance_daily_rollup`
