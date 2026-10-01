<div dir="rtl">

# סכמת Airtable — בסיס `ERP-AI`

Base ID: `appxsZIq0qv9Buy9d` (בהקמה חדשה — החלף במזהה שלך).
שמות השדות חייבים להיות **בדיוק** כמו כאן — ה-workflows פונים אליהם בשם. `Status` הוא טקסט חופשי (לא Single select), `Created` מסוג *Created time* — בלעדיהם הטריגרים לא יעבדו.

## Leads — `tblxwV7kZv7UF5wt2`
| שדה | סוג | הערה |
|---|---|---|
| Name | Single line text | שדה ראשי |
| email | Email | מפתח לזיהוי כפילויות ולהתאמת תשובות במייל |
| Company | Single line text | |
| Status | Single line text | `New` · `Contacted` · `הגיב` · `לקוח` · `לא רלוונטי` |
| Created | Created time | טריגרים |
| CustomerId | Autonumber | מפתח זר — `Invoices.CustomerId` מצביע לכאן |

## Invoices — `tblUyOaKSKEgea5wn`
| שדה | סוג | הערה |
|---|---|---|
| InvoiceNumber | Number | שדה ראשי; מספור רץ מ-1001 (workflow 5) |
| CustomerId | Number | = `Leads.CustomerId` |
| Amount | Number | לפני מע"מ |
| VatAmount | Number | 18% (workflow 5) |
| Total | Number | Amount + VatAmount |
| Status | Single line text | `ממתין לאימות` → `ממתין להפקה` → `הופק` → `נשלחה ללקוח` → `שולמה` · `שגיאה: …` |
| PdfUrl | Single line text | קישור למסמך בדרייב (workflow 8) |
| Created | Created time | טריגר של workflow 5 |

## Products — `tblABDbFCYw5lOj8b`
| שדה | סוג | הערה |
|---|---|---|
| Name | Single line text | שדה ראשי |
| Category | Single line text | |
| Price | Number | ₪ כולל מע"מ |
| Description | Single line text | מתחיל ב-"מקט XXX." — הסוכן והחנות מחלצים ממנו מק"ט |
| InStock | Single line text | `checked` = במלאי, ריק = אזל |

## Tasks — `tblxNIfJDHc9uJoTT`
| שדה | סוג | הערה |
|---|---|---|
| Title | Single line text | שדה ראשי |
| Status | Single line text | `לביצוע` · `בתהליך` · `הושלם` |

## הערת מימוש
צומת Airtable ב-n8n (v2.2) מחזיר רשומה בצורה `{ id, createdTime, fields: {…} }`. ה-workflows "משטחים" את זה (`{ id, ...fields }`) לפני שימוש, ו-webhook 10 מחזיר לאפליקציה רשומות שטוחות.

</div>
