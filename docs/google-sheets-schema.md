# Google Sheets schema

Use the exact tab names and headers below.

## `Purchase_Order_KPI_Log`

```text
report_date
total_purchase_orders
total_amount_mad
high_value_orders
risky_supplier_orders
urgent_orders
duplicate_orders
approval_required_count
highest_order_id
highest_order_supplier
highest_order_amount_mad
risk_level
```

## `Purchase_Order_Approval_Log`

```text
approval_id
report_date
risk_level
total_amount_mad
approval_required_count
decision_status
requested_at
decided_at
decision_by
action_result
notes
ai_alert
```

Recommended date formats:

- `report_date`: `YYYY-MM-DD`
- `requested_at`: ISO date and time
- `decided_at`: ISO date and time
