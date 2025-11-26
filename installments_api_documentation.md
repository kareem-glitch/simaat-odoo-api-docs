# Installments API Documentation

## Endpoint
```
GET https://dev.simaat.sa/api/odoo/v1/installments/list?contract_id={contract_id}
```

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `contract_id` | integer | Yes | معرف العقد (Contract ID to get installments for) |

---

## Response Structure

```json
{
  "data": [...],
  "status": "OK",
  "count": 2
}
```

| Field | Type | Description |
|-------|------|-------------|
| `data` | array | مصفوفة بيانات الأقساط (Array of installment objects) |
| `status` | string | حالة الاستجابة (Response status) |
| `count` | integer | عدد الأقساط (Number of installments returned) |

---

## Installment Object Fields

### Installment Identification (معرفات القسط)

| Field | Type | Description |
|-------|------|-------------|
| `tmt_uid` | string | المعرف الفريد للقسط (Unique installment identifier) |
| `tmt_id` | string | معرف القسط في النظام (System installment ID) |
| `tmt_seq` | string | تسلسل القسط (Installment sequence number) |
| `yr_seq` | string | تسلسل القسط في السنة (Year sequence number) |
| `srv_cat` | string | تصنيف الخدمة (Service category: `srv_inst` = Installment) |
| `srv_id` | string | معرف الخدمة (Service ID) |

---

### Contract Reference (مرجع العقد)

| Field | Type | Description |
|-------|------|-------------|
| `tts_id` | string | معرف العقد (Contract ID) |
| `tts_tts_id` | string | معرف العقد الأصلي (Parent contract ID) |
| `tts_code` | string | كود العقد (Contract code) |
| `tts_status` | string | حالة العقد (Contract status code) |
| `tts_validity` | string | صلاحية العقد (Contract validity: `active`, `expired`) |

---

### Property Reference (مرجع العقار)

| Field | Type | Description |
|-------|------|-------------|
| `are_id` | string | معرف الوحدة (Unit ID) |
| `are_are_id` | string | معرف العقار الأب (Parent property ID) |
| `are_owner` | string | معرف المالك (Owner ID) |
| `are_status` | string | حالة الوحدة (Unit status code) |
| `atr_id` | string | معرف المستأجر (Tenant ID) |

---

### Period Information (معلومات الفترة)

| Field | Type | Description |
|-------|------|-------------|
| `dt_from` | timestamp | تاريخ بداية الفترة (Period start date - Unix timestamp) |
| `dt_to` | timestamp | تاريخ نهاية الفترة (Period end date - Unix timestamp) |
| `day_tot` | string | إجمالي أيام الفترة (Total days in period) |
| `day_cost` | string | تكلفة اليوم الواحد (Daily cost rate) |

---

### Due Date Information (معلومات تاريخ الاستحقاق)

| Field | Type | Description |
|-------|------|-------------|
| `dt_due` | timestamp | تاريخ الاستحقاق (Due date - Unix timestamp) |
| `dt_due_day` | string | تاريخ الاستحقاق (Due date - YYYY-MM-DD format) |
| `dt_due_hj` | string | تاريخ الاستحقاق هجري (Due date - Hijri) |
| `view_due` | string | تاريخ الاستحقاق للعرض (Due date for display) |
| `dt_issue` | timestamp | تاريخ الإصدار (Issue date - Unix timestamp) |
| `is_due` | string | مستحق الآن (Is currently due: `0` = No, `1` = Yes) |
| `days_due` | string | أيام حتى/منذ الاستحقاق (Days to/since due date, negative = overdue) |

---

### Due Date Grouping (تجميع الاستحقاق)

| Field | Type | Description |
|-------|------|-------------|
| `mo_due` | string | شهر الاستحقاق (Due month: YYMM format) |
| `qtr_due` | string | ربع السنة (Due quarter: 1-4) |
| `yr_due` | string | سنة الاستحقاق (Due year) |
| `due_aging` | string | فئة التقادم (Aging category) |
| `due_aging_group` | string | مجموعة التقادم بالأيام (Aging group in days: 0, 30, 60, 90, etc.) |

---

### Installment Description (وصف القسط)

| Field | Type | Description |
|-------|------|-------------|
| `tmt_ar` | string | اسم القسط بالعربية (Installment name - Arabic) |
| `tmt_en` | string | اسم القسط بالإنجليزية (Installment name - English) |
| `tmt_desc` | string | وصف تفصيلي للقسط (Detailed description with period info) |

---

### Amount Information (معلومات المبالغ)

| Field | Type | Description |
|-------|------|-------------|
| `amt_st` | string | المبلغ الأساسي (Base amount / Subtotal) |
| `amt_disc` | string | مبلغ الخصم (Discount amount) |
| `amt_untax` | string | المبلغ قبل الضريبة (Amount before tax) |
| `amt_tax` | string | مبلغ الضريبة (Tax amount) |
| `amt_tot` | string | المبلغ الإجمالي (Total amount) |
| `amt_collect` | string | المبلغ المحصل (Collected amount) |
| `amt_due` | string | المبلغ المستحق (Due amount) |
| `amt_due_later` | string | المبلغ المستحق لاحقاً (Amount due later / Deferred) |
| `amt_balance` | string | الرصيد المتبقي (Remaining balance) |
| `amt_payable` | string | المبلغ الواجب دفعه (Payable amount) |
| `pct_tax` | string | نسبة الضريبة (Tax percentage) |
| `inc_vat` | string | شامل ضريبة القيمة المضافة (VAT inclusive: `0` = No, `1` = Yes) |

---

### Commission Information (معلومات العمولة)

| Field | Type | Description |
|-------|------|-------------|
| `inc_comm` | string | يشمل عمولة (Includes commission: `0` = No, `1` = Yes) |
| `due_comm` | string | حالة استحقاق العمولة (Commission due status: `nocomm`, `pending`, `paid`) |
| `pct_comm` | string | نسبة العمولة (Commission percentage) |
| `amt_comm` | string | مبلغ العمولة (Commission amount) |
| `pct_comm_tax` | string | نسبة ضريبة العمولة (Commission tax percentage) |
| `amt_comm_tax` | string | مبلغ ضريبة العمولة (Commission tax amount) |
| `amt_comm_tot` | string | إجمالي العمولة (Total commission with tax) |

---

### Accounting Codes (أكواد المحاسبة)

| Field | Type | Description |
|-------|------|-------------|
| `post_account` | string | نوع ترحيل الحساب (Posting account type: `specific_acc`, `default`) |
| `post_acc_code` | string | كود حساب الترحيل (Posting account code - Credit) |
| `dr_acc_code` | string | كود حساب المدين (Debit account code) |
| `post_tax_code` | string | كود حساب الضريبة (Tax account code - Credit) |
| `dr_tax_code` | string | كود حساب ضريبة المدين (Debit tax account code) |
| `post_comm_acc` | string | كود حساب العمولة (Commission account code) |
| `post_comm_tax` | string | كود حساب ضريبة العمولة (Commission tax account code) |
| `myo_code` | string | كود السنة المالية (Fiscal year code) |

---

### Flags & Settings (الإعدادات والعلامات)

| Field | Type | Description |
|-------|------|-------------|
| `skip_calc` | string | تخطي الحساب (Skip calculation: `0` = No, `1` = Yes) |
| `ign_einv` | string | تجاهل الفوترة الإلكترونية (Ignore e-invoice: `0` = No, `1` = Yes) |
| `ign_due` | string | تجاهل الاستحقاق (Ignore due: `0` = No, `1` = Yes) |
| `evac_id` | string | معرف الإخلاء (Evacuation ID, `0` = No evacuation) |
| `entry_type` | string | نوع الإدخال (Entry type: `auto`, `manual`) |
| `cal_type` | string | نوع التقويم (Calendar type: `cal_gr` = Gregorian) |

---

### Sync & Update (المزامنة والتحديث)

| Field | Type | Description |
|-------|------|-------------|
| `rel_update` | string | تم التحديث بعد الإصدار (Updated after release: `0` = No, `1` = Yes) |
| `is_sync` | string | حالة المزامنة (Sync status: `0` = Not synced, `1` = Synced) |

---

### Audit Trail (سجل التدقيق)

| Field | Type | Description |
|-------|------|-------------|
| `create_by` | string | معرف المنشئ (Created by user ID) |
| `dt_created` | timestamp | تاريخ الإنشاء (Creation date - Unix timestamp) |
| `update_by` | string | معرف المحدث (Updated by user ID) |
| `dt_updated` | timestamp | تاريخ آخر تحديث (Last update date - Unix timestamp) |

---

## Lookup Values

### Service Category (تصنيف الخدمة)

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `srv_inst` | Installment | قسط |
| `srv_maint` | Maintenance | صيانة |
| `srv_util` | Utilities | خدمات |

---

### Due Commission (حالة العمولة)

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `nocomm` | No Commission | بدون عمولة |
| `pending` | Pending | معلقة |
| `paid` | Paid | مدفوعة |

---

### Entry Type (نوع الإدخال)

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `auto` | Automatic | تلقائي |
| `manual` | Manual | يدوي |

---

### Due Aging Groups (مجموعات التقادم)

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `0` | Current / Not Due | حالي / غير مستحق |
| `30` | 1-30 Days Overdue | متأخر 1-30 يوم |
| `60` | 31-60 Days Overdue | متأخر 31-60 يوم |
| `90` | 61-90 Days Overdue | متأخر 61-90 يوم |
| `120` | 91-120 Days Overdue | متأخر 91-120 يوم |
| `180` | 121-180 Days Overdue | متأخر 121-180 يوم |
| `365` | Over 180 Days Overdue | متأخر أكثر من 180 يوم |

---

## Amount Calculation Flow

```
amt_st (Base Amount)
    ↓
- amt_disc (Discount)
    ↓
= amt_untax (Amount Before Tax)
    ↓
+ amt_tax (Tax Amount based on pct_tax)
    ↓
= amt_tot (Total Amount)

amt_tot = amt_collect + amt_balance
amt_balance = amt_due + amt_due_later
```

---

## Notes

- All timestamp fields are Unix timestamps (seconds since 1970-01-01)
- `days_due` negative value indicates overdue days
- `days_due` positive value indicates days until due
- `tmt_desc` contains human-readable period description in Arabic
- `mo_due` format is YYMM (e.g., `2402` = February 2024)
- Installments are auto-generated based on contract payment terms
- `day_cost` = `amt_tot` / `day_tot` (daily rate calculation)

