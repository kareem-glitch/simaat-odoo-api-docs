# Accounts API Documentation

## Endpoint
```
GET https://dev.simaat.sa/api/odoo/v1/accounts/list
```

---

## Response Structure

```json
{
  "data": [...],
  "status": "OK",
  "count": 202
}
```

| Field | Type | Description |
|-------|------|-------------|
| `data` | array | مصفوفة بيانات الحسابات (Array of account objects) |
| `status` | string | حالة الاستجابة (Response status) |
| `count` | integer | عدد الحسابات (Number of accounts returned) |

---

## Account Object Fields

### Account Identification (معرفات الحساب)

| Field | Type | Description |
|-------|------|-------------|
| `acc_id` | string | معرف الحساب الفريد (Unique account identifier) |
| `acc_code` | string | كود الحساب (Account code - hierarchical numbering) |
| `old_acc_code` | string/null | كود الحساب القديم (Old account code for migration) |

---

### Account Hierarchy (التسلسل الهرمي للحساب)

| Field | Type | Description |
|-------|------|-------------|
| `acc_parent_id` | string | معرف الحساب الأب (Parent account ID) |
| `acc_parent` | string | كود الحساب الأب (Parent account code) |
| `acc_level` | string | مستوى الحساب في الشجرة (Account level in hierarchy: 1-6) |
| `acc_sub` | string | عدد الحسابات الفرعية (Number of sub-accounts) |
| `sequence` | string | ترتيب الحساب (Account sequence for sorting) |

---

### Account Description (وصف الحساب)

| Field | Type | Description |
|-------|------|-------------|
| `acc_name` | string | اسم الحساب بالعربية (Account name - Arabic) |
| `acc_name_en` | string | اسم الحساب بالإنجليزية (Account name - English) |
| `acc_desc` | string | وصف الحساب (Account description) |
| `acc_ref` | string | مرجع الحساب (Account reference) |

---

### Account Classification (تصنيف الحساب)

| Field | Type | Description |
|-------|------|-------------|
| `acc_type` | string/null | نوع الحساب (Account type) |
| `acc_nature` | string | طبيعة الحساب (Account nature: `debit`, `credit`) |
| `acc_cat` | string | فئة الحساب (Account category: `assets`, `liabilities`, `capital`, `revenues`, `expenses`) |
| `acc_dis` | string/null | تصنيف العرض (Display classification: `balance_sheet`, `profit_loss`) |

---

### Account Balances (أرصدة الحساب)

| Field | Type | Description |
|-------|------|-------------|
| `acc_balance` | string | رصيد الحساب الحالي (Current account balance) |
| `acc_amt_in` | string | إجمالي المبالغ الداخلة/المدينة (Total debit/incoming amount) |
| `acc_amt_out` | string | إجمالي المبالغ الخارجة/الدائنة (Total credit/outgoing amount) |

---

### Account Settings (إعدادات الحساب)

| Field | Type | Description |
|-------|------|-------------|
| `active` | string | الحساب نشط (Account active: `0` = No, `1` = Yes) |
| `acc_payable` | string | حساب مدفوعات (Payable account: `0` = No, `1` = Yes) |
| `is_dim` | string | حساب أبعاد/تحليلي (Dimensional account: `0` = No, `1` = Yes) |
| `is_deleted` | string | محذوف (Deleted: `0` = No, `1` = Yes) |

---

### Numbering Settings (إعدادات الترقيم)

| Field | Type | Description |
|-------|------|-------------|
| `acc_pad` | string | عدد خانات الكود الفرعي (Sub-code padding length) |
| `acc_number_next` | string | الرقم التالي للحساب الفرعي (Next sub-account number) |
| `acc_increment` | string | مقدار الزيادة (Increment value) |

---

### Sync & Update (المزامنة والتحديث)

| Field | Type | Description |
|-------|------|-------------|
| `dt_updated` | timestamp | تاريخ آخر تحديث (Last update date - Unix timestamp) |
| `rel_update` | string | تحديث مرتبط/تاريخ التحديث (Related update timestamp or flag) |
| `is_sync` | string | حالة المزامنة (Sync status: `0` = Not synced, `1` = Synced) |

---

## Lookup Values

### Account Nature (طبيعة الحساب)

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `debit` | Debit | مدين |
| `credit` | Credit | دائن |

---

### Account Category (فئة الحساب)

| Value | Description (EN) | Description (AR) | Code Prefix |
|-------|-----------------|------------------|-------------|
| `assets` | Assets | الأصول | 1 |
| `liabilities` | Liabilities | الالتزامات | 2 |
| `capital` | Capital/Equity | حقوق الملكية | 3 |
| `revenues` | Revenues | الإيرادات | 4 |
| `expenses` | Expenses | المصروفات | 5 |

---

### Display Classification (تصنيف العرض)

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `balance_sheet` | Balance Sheet | الميزانية العمومية |
| `profit_loss` | Profit & Loss | قائمة الأرباح والخسائر |

---

### Account Level (مستوى الحساب)

| Level | Description (EN) | Description (AR) | Example Code |
|-------|-----------------|------------------|--------------|
| 1 | Main Category | الفئة الرئيسية | `1`, `2`, `3`, `4`, `5` |
| 2 | Sub Category | الفئة الفرعية | `11`, `12`, `21`, `22` |
| 3 | Group | المجموعة | `1101`, `1102`, `2201` |
| 4 | Sub Group | المجموعة الفرعية | `110101`, `110201` |
| 5 | Account | الحساب | `110101001`, `110201001` |
| 6 | Sub Account | الحساب الفرعي | `22010100201` |

---

## Chart of Accounts Structure (هيكل شجرة الحسابات)

### Main Categories (الفئات الرئيسية)

```
1 - الأصول (Assets)
├── 11 - الأصول المتداولة (Current Assets)
│   ├── 1101 - النقدية والبنوك (Cash and Banks)
│   ├── 1102 - ذمم مدينة (Accounts Receivable)
│   ├── 1103 - ذمم مدينة أخرى (Other Receivables)
│   └── 1104 - مصروفات مدفوعة مقدماً (Prepaid Expenses)
└── 12 - الأصول الغير متداولة (Non-current Assets)
    └── 1201 - الأصول الثابتة (Fixed Assets)

2 - الالتزامات (Liabilities)
├── 21 - الالتزامات الغير متداولة (Non-current Liabilities)
│   └── 2101 - مخصصات (Provisions)
└── 22 - الالتزامات المتداولة (Current Liabilities)
    ├── 2201 - ذمم دائنة (Payables)
    └── 2202 - المخصصات (Allocations)

3 - حقوق الملكية (Equity)
└── 31 - حقوق الملكية (Equity)
    ├── 3101 - رأس المال (Capital)
    └── 3102 - الاحتياطيات (Reserves)

4 - الإيرادات (Revenues)
└── 41 - إيرادات الإدارات التشغيلية (Operating Revenues)
    ├── 4101 - إيرادات إدارة الأملاك (Property Management Income)
    ├── 4102 - إيرادات عقارات مملوكة (Owned Properties Income)
    └── 4103 - إيرادات إعادة استثمار (Reinvestment Income)

5 - المصروفات (Expenses)
├── 51 - تكاليف الإيراد (Cost of Revenue)
│   └── 5101 - تكلفة إيرادية (Revenue Cost)
└── 52 - المصروفات (Expenses)
    └── 5201 - مصروفات عمومية وإدارية (General & Administrative)
```

---

## Balance Calculation (حساب الرصيد)

```
For Debit Accounts (Assets, Expenses):
acc_balance = acc_amt_in - acc_amt_out

For Credit Accounts (Liabilities, Capital, Revenues):
acc_balance = acc_amt_out - acc_amt_in
```

---

## Common Account Codes (أكواد الحسابات الشائعة)

### Assets (الأصول)

| Code | Name (AR) | Name (EN) |
|------|-----------|-----------|
| `110101` | النقدية في الصندوق | Cash in Fund |
| `110103` | البنوك | Banks |
| `110201` | عملاء إدارة الأملاك | Property Management Clients |
| `110201001` | عملاء سكني - تجاري | Residential - Commercial Clients |

### Liabilities (الالتزامات)

| Code | Name (AR) | Name (EN) |
|------|-----------|-----------|
| `220101001` | إيجارات مستحقة للمالك - تحت التحصيل | Rents Due - Under Collection |
| `220101002` | إيجارات مستحقة للمالك - واجبة السداد | Rents Due - Payable |
| `220101003` | إيجارات مقدمة - مستأجرين | Advance Rents - Tenants |
| `220101005` | تأمينات مستحقة للمستأجرين | Insurance Due to Tenants |
| `220104002` | ضريبة قيمة مضافة - إدارة الأملاك | VAT - Property Management |

### Revenues (الإيرادات)

| Code | Name (AR) | Name (EN) |
|------|-----------|-----------|
| `410101001` | إيرادات إدارة الأملاك | Property Management Income |
| `410101002` | إيرادات سعي العقود الجديدة | New Contract Pursuit Income |
| `410101003` | إيرادات توثيق عقود إيجار | Lease Documentation Income |

### Expenses (المصروفات)

| Code | Name (AR) | Name (EN) |
|------|-----------|-----------|
| `510101001` | الراتب الأساسي | Base Salary |
| `510101002` | بدل السكن | Housing Allowance |
| `510105001` | رسوم برنامج إيجار | Ejar Program Fees |

---

## Notes

- Account codes follow a hierarchical numbering system
- `acc_level` indicates the depth in the account hierarchy (1 = root, higher = more detailed)
- Accounts with `acc_sub > 0` have child accounts and are typically summary accounts
- Accounts with `is_dim = 1` are dimensional/analytical accounts used for detailed tracking
- `acc_payable = 1` indicates the account can be used for payment transactions
- Balance sheet accounts (`acc_dis = "balance_sheet"`) appear in the Balance Sheet report
- Profit & Loss accounts (`acc_dis = "profit_loss"`) appear in the Income Statement
- `sequence` field is used for sorting accounts in reports and displays

