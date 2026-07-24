# Setup checklist

## 1. Import the workflows

Import these files into n8n:

1. `workflows/purchase-order-approval-decision-handler.json`
2. `workflows/erp-procurement-approval-agent.json`

## 2. Connect credentials

Reconnect each node to your own credentials:

- Gmail OAuth
- Google Sheets OAuth
- Telegram Bot API
- Groq API

## 3. Replace placeholders

Search both workflows for `YOUR_` and replace:

| Placeholder | Replace with |
|---|---|
| `YOUR_EMAIL@example.com` | Report recipient |
| `YOUR_GOOGLE_SHEET_ID` | Google Sheets document ID |
| `YOUR_TELEGRAM_CHAT_ID` | Telegram chat ID |
| `YOUR_PDFSHIFT_API_KEY` | PDFShift API key |
| `https://YOUR-N8N-DOMAIN` | Public n8n base URL |

## 4. Prepare Google Sheets

Create:

- `Purchase_Order_KPI_Log`
- `Purchase_Order_Approval_Log`

Copy the exact headers from
[`google-sheets-schema.md`](google-sheets-schema.md).

Open every Google Sheets node and select your document and tab again. This
refreshes the n8n column schema.

## 5. Configure the webhook

The decision-handler webhook path is:

```text
purchase-order-approval-decision
```

Set the production URL in the `Prepare Purchase Order Approval` Code node:

```text
https://YOUR-N8N-DOMAIN/webhook/purchase-order-approval-decision
```

## 6. Publish in the correct order

1. Publish `ERP Procurement - Purchase Order Approval Decision Handler`.
2. Publish `ERP Procurement - Purchase Order Approval Agent`.

## 7. Test

Send one CSV from `sample-data` to the connected Gmail inbox.

Required subject:

```text
ERP Purchase Orders
```

Verify:

- KPI row appended in Google Sheets
- Telegram summary received
- PDF report received by Gmail
- Pending approval row created
- Telegram approval links received
- Approve link updates the row to `Approved`
- Reject link updates the row to `Rejected`

## 8. Configure Looker Studio

Connect Looker Studio to `Purchase_Order_KPI_Log`. For scorecards that should
show the latest tested volume, use `Maximum` instead of `Sum`. Keep monetary
amounts separate from order-count metrics when they share an axis.
