# CLAUDE.md — ERP-AI (פרויקט גמר)

- שפה: עברית, RTL, ₪, dd/mm/yyyy. קוד/שמות קבצים באנגלית.
- מקור האמת למבנה: `docs/פרויקט-גמר-53500.docx`. סכמה: `docs/schema.md`. הקמה: `docs/setup.md`.
- Airtable base `appxsZIq0qv9Buy9d` — טבלאות Leads/Invoices/Products/Tasks (IDs ב-schema.md). אל תשנה שמות שדות.
- n8n Cloud: `eyalmyers.app.n8n.cloud`, תיקיית `erp`. ייצוא ב-`workflows/` — לעדכן אחרי כל שינוי. Webhook: `POST /webhook/erp-app`.
- צומת Airtable v2.2 מחזיר `{id, fields:{}}` — לשטח לפני שימוש.
- Vector store בזיכרון: memory keys `mypolicies` / `theproducts` (3, 4, 7, 10 חייבים להתאים).
- אפליקציות סטטיות ב-`app/` (store, admin): בלי framework, בלי build, בלי מפתחות בצד הלקוח.
- אין להעלות סודות: טוקנים של טלגרם/Airtable/OpenAI נשארים ב-n8n בלבד.
