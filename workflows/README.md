<div dir="rtl">

# ייצוא ה-workflows

קובץ JSON לכל workflow, לייבוא ב-n8n (Create Workflow → ⋯ → Import from File). הקבצים מפנים ל-credentials **לפי שם בלבד** — אין בהם סודות. אחרי ייבוא: בחר credential, בסיס וטבלה בכל צומת Airtable. ב-`09-manager-agent.json` החלף את `OWNER_TELEGRAM_CHAT_ID` ב-Chat ID שלך.

| קובץ | n8n | מסמך מנחה |
|---|---|---|
| 01-leads-to-airtable | 1 - Leads → Airtable | WF2 |
| 02-sales-cold-emails | 2 - Sales Cold Emails | WF3 |
| 03-policies-embedding | 3 - Policies Embedding | WF6 |
| 04-products-embedding | 4 - Products Embedding | WF7 |
| 05-invoice-validation-vat | 5 - אימות חשבונית ומע"מ | WF1 |
| 06-sales-reply-check | 6 - סוכן מכירות - בדיקת תשובות | WF4 |
| 07-customer-service-agent | 7 - סוכן שירות לקוחות (טלגרם) | WF5 |
| 08-invoice-document-to-drive | 8 - הפקת מסמך חשבונית לדרייב | WF8 |
| 09-manager-agent | 9 - סוכן המנהל (טלגרם) | WF9 |
| 10-app-webhook | 10 - Webhook לאפליקציה | WF13 |
| 11-invoice-email-to-customer | 11 - שליחת חשבונית ללקוח במייל | הרחבה: מסלול הזמנה מלא |

</div>
