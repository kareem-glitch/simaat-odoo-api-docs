# Cost Centers API Documentation

## Endpoint
```
GET https://dev.simaat.sa/api/odoo/v1/cost-centers/list
```

---

## Response Structure

```json
{
  "data": [...],
  "status": "OK",
  "count": 10
}
```

| Field | Type | Description |
|-------|------|-------------|
| `data` | array | مصفوفة بيانات مراكز التكلفة (Array of cost center objects) |
| `status` | string | حالة الاستجابة (Response status) |
| `count` | integer | عدد مراكز التكلفة (Number of cost centers returned) |

---

## Cost Center Object Fields

### Cost Center Identification (معرفات مركز التكلفة)

| Field | Type | Description |
|-------|------|-------------|
| `acc_id` | string | معرف مركز التكلفة الفريد (Unique cost center identifier, starts with 900xxx) |
| `acc_code` | string | كود مركز التكلفة (Cost center code - hierarchical numbering) |

---

### Cost Center Hierarchy (التسلسل الهرمي)

| Field | Type | Description |
|-------|------|-------------|
| `acc_parent` | string | كود مركز التكلفة الأب (Parent cost center code) |
| `acc_level` | string | مستوى مركز التكلفة في الشجرة (Level in hierarchy: 0-3) |
| `acc_sub` | string | عدد مراكز التكلفة الفرعية (Number of sub cost centers) |

---

### Cost Center Description (وصف مركز التكلفة)

| Field | Type | Description |
|-------|------|-------------|
| `acc_name` | string | اسم مركز التكلفة بالعربية (Cost center name - Arabic) |
| `acc_name_en` | string | اسم مركز التكلفة بالإنجليزية (Cost center name - English) |

---

### Cost Center Balances (أرصدة مركز التكلفة)

| Field | Type | Description |
|-------|------|-------------|
| `acc_balance` | string | رصيد مركز التكلفة الحالي (Current cost center balance) |
| `acc_amt_in` | string | إجمالي المبالغ الداخلة (Total incoming/debit amount) |
| `acc_amt_out` | string | إجمالي المبالغ الخارجة (Total outgoing/credit amount) |

---

### Cost Center Settings (إعدادات مركز التكلفة)

| Field | Type | Description |
|-------|------|-------------|
| `active` | string | مركز التكلفة نشط (Active: `0` = No, `1` = Yes) |
| `acc_payable` | string | قابل للدفع (Payable: `0` = No, `1` = Yes) |
| `acc_nature` | string | طبيعة الحساب (Account nature: `credit`, `debit`) |
| `pct_rel` | string | نسبة التوزيع (Distribution percentage) |

---

### Numbering Settings (إعدادات الترقيم)

| Field | Type | Description |
|-------|------|-------------|
| `acc_pad` | string | عدد خانات الكود الفرعي (Sub-code padding length) |
| `acc_increment` | string | مقدار الزيادة (Increment value) |

---

### Resource Linking (ربط الموارد)

| Field | Type | Description |
|-------|------|-------------|
| `set_id` | string | معرف الإعداد/المجموعة (Setting/Group ID) |
| `res_table` | string/null | جدول المورد المرتبط (Linked resource table: `plt_prop`, etc.) |
| `res_id` | string | معرف المورد المرتبط (Linked resource ID) |
| `client_id` | string | معرف العميل المرتبط (Linked client ID) |

---

### Status & Sync (الحالة والمزامنة)

| Field | Type | Description |
|-------|------|-------------|
| `acl_status_code` | string | كود حالة النظام (System status code) |
| `dt_updated` | timestamp | تاريخ آخر تحديث (Last update date - Unix timestamp) |
| `dt_deleted` | timestamp | تاريخ الحذف (Deletion date - `0` = not deleted) |
| `rel_update` | string | تحديث مرتبط (Related update flag) |
| `is_sync` | string | حالة المزامنة (Sync status: `0` = Not synced, `1` = Synced) |

---

## Cost Center Hierarchy Structure (هيكل مراكز التكلفة)

```
6 - مركز التكلفة الرئيسي (Main Cost Center)
├── 6001 - عقارات أملاك الغير (Properties Under Management)
├── 6002 - عقارات إعادة استثمار (Reinvestment Properties)
├── 6003 - عقارات مملوكة (Owned Properties)
│   └── 6003001 - م.تكلفة عقار الياسمين (Yasmin Property Cost Center)
└── 6004 - الفروع (Branches)
    ├── 6004001 - مركز تكلفة الفرع الرئيسي (Headquarter Cost Center)
    ├── 6004002 - م.تكلفة فرع القاهرة (Cairo Branch Cost Center)
    └── 6004003 - م.تكلفة فرع عمان (Amman Branch Cost Center)
```

---

## Cost Center Levels (مستويات مراكز التكلفة)

| Level | Description (EN) | Description (AR) | Example Code |
|-------|-----------------|------------------|--------------|
| 0 | Dynamic/Auto-generated | ديناميكي/تلقائي | `0` |
| 1 | Main Category | الفئة الرئيسية | `6` |
| 2 | Sub Category | الفئة الفرعية | `6001`, `6002`, `6003`, `6004` |
| 3 | Detail | التفصيلي | `6003001`, `6004001` |

---

## Resource Table Values (جداول الموارد المرتبطة)

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `plt_prop` | Property | العقار |
| `null` | No linked resource | بدون مورد مرتبط |

---

## Cost Center Categories (فئات مراكز التكلفة)

| Code | Name (AR) | Name (EN) | Use Case |
|------|-----------|-----------|----------|
| `6001` | عقارات أملاك الغير | Properties Under Management | تتبع تكاليف العقارات المُدارة للغير |
| `6002` | عقارات إعادة استثمار | Reinvestment Properties | تتبع تكاليف عقارات إعادة الاستثمار |
| `6003` | عقارات مملوكة | Owned Properties | تتبع تكاليف العقارات المملوكة للشركة |
| `6004` | الفروع | Branches | تتبع تكاليف فروع الشركة |

---

## Set ID Values (قيم معرف الإعداد)

| Value | Description |
|-------|-------------|
| `0` | مركز تكلفة عام (General cost center - not linked to specific setting) |
| `10` | مرتبط بإعداد عقارات الغير (Linked to properties under management setting) |
| `20` | مرتبط بإعداد عقارات مملوكة (Linked to owned properties setting) |

---

## Notes

- Cost center IDs (`acc_id`) start from `900001` to differentiate from regular accounts
- Cost centers with `acc_level = 0` are typically auto-generated/dynamic
- `res_table` and `res_id` link the cost center to a specific resource (e.g., property)
- `client_id` links the cost center to a specific client (e.g., branch owner)
- Cost centers are used for tracking expenses and revenues by category/location
- `pct_rel` can be used for automatic cost distribution between centers
- `dt_deleted = 0` means the cost center is not deleted (soft delete mechanism)

