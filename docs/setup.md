<div dir="rtl">

# מדריך הקמה — ERP-AI על n8n Cloud

## 0. חשבונות
n8n Cloud · Airtable · OpenAI · שני בוטי טלגרם מ-@BotFather (מנהל + לקוחות) · חשבון Google ל-Gmail ול-Drive. אין מה להתקין.

## 1. Credentials ב-n8n (Credentials → Add)
| שם מומלץ | סוג | משמש ב |
|---|---|---|
| Airtable Personal Access Token | Airtable Personal Access Token | 1, 2, 5, 6, 8, 9, 10, 11 |
| OpenAI account | OpenAI API | 2, 3, 4, 7, 9, 10 |
| Gmail OAuth2 | Gmail OAuth2 | 1, 2, 6, 11 |
| Google Drive OAuth2 | Google Drive OAuth2 | 8 |
| Telegram — בוט המנהל | Telegram API | 9 |
| Telegram — בוט הלקוחות | Telegram API | 7 |

ל-PAT של Airtable: scopes `data.records:read`, `data.records:write`, `schema.bases:read` על הבסיס.

## 2. Airtable
צור בסיס עם 4 הטבלאות לפי [`schema.md`](schema.md). ייבא את [`../data/products.csv`](../data/products.csv) לטבלת Products (CSV import, מיפוי לפי שם עמודה).

## 3. ייבוא ה-workflows
לכל קובץ ב-`workflows/`: n8n → Create Workflow → ⋯ → *Import from File*. אחרי הייבוא, בכל צומת Airtable בחר מהרשימה את הבסיס והטבלה שלך, ובכל צומת בחר את ה-credential המתאים.

## 4. מילוי המאגר הווקטורי (RAG)
- פתח את **3 - Policies Embedding** → *Test workflow* → בטופס שנפתח העלה את 12 הקבצים מ-`policies/` (אפשר אחד-אחד).
- פתח את **4 - Products Embedding** → *Test workflow* → העלה את `data/products.csv`.
- שמות המאגרים (`mypolicies`, `theproducts`) חייבים להתאים לכלי ה-Vector Store ב-7 וב-10 — כבר מוגדרים כך.
- **המאגר בזיכרון של n8n**: אחרי כל הפעלה מחדש של ה-instance — להריץ את 3 ו-4 שוב.

## 5. סוכן המנהל — Chat ID
שלח `/start` ל-@userinfobot בטלגרם וקבל את ה-`Id` שלך. ב-**9 - סוכן המנהל**, צומת "זה הבעלים?", הדבק את המספר במקום `OWNER_TELEGRAM_CHAT_ID`.

## 6. הפעלה
Activate: 1, 2, 5, 6, 7, 8, 9, 10, 11. (3 ו-4 נשארים ידניים.)

## 7. האפליקציות
- ב-**10** העתק את ה-Production URL של ה-Webhook (`…/webhook/erp-app`) → הדבק ב-`WEBHOOK_URL` בראש ה-`<script>` של `app/store/index.html` ו-`app/admin/index.html`.
- ב-**1** העתק את ה-Production URL → `LEADS_WEBHOOK_URL` בחנות.
- פרסום: גרור את תיקיית `app/` ל-Netlify Drop, או פתח את הקבצים מקומית. אין build.

## 8. בדיקה מקצה לקצה
1. בחנות: הוסף מוצר לעגלה → "להזמנה" → שם + אימייל שלך → שלח.
2. ב-Airtable: ליד חדש בסטטוס `לקוח`, חשבונית `ממתין לאימות`, משימה `לביצוע`.
3. תוך ~3 דקות: החשבונית עוברת `ממתין להפקה` → `הופק` (עם PdfUrl) → `נשלחה ללקוח`, והמייל אצלך.
4. באפליקציית הניהול: הדשבורד מראה את ההכנסה; "הסוכן החכם" — "כמה חשבוניות לא שולמו?".
5. בטלגרם: לבוט הלקוחות "מה מדיניות ההחזרות?"; לבוט המנהל "מה ההכנסות?".
6. בטופס "הצעת מחיר" בחנות: ליד חדש ב-`New`; תוך 3 שעות מייל קר יוצא ו-`Contacted`.

כל ריצה — ירוקה או אדומה — נראית ב-Executions של n8n. זה כלי הניפוי היחיד שצריך.

</div>
