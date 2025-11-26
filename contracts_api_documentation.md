# Contracts API Documentation

## Endpoint
```
GET https://dev.simaat.sa/api/odoo/v1/contracts/list
```

---

## Response Fields

### Contract Identification

| Field | Type | Description |
|-------|------|-------------|
| `tts_id` | string | معرف العقد الفريد (Contract unique identifier) |
| `tts_tts_id` | string | معرف العقد الأصلي في حالة التجديد (Parent contract ID for renewals) |
| `tts_code` | string | رقم/كود العقد (Contract code/number) |
| `res_uid` | string | المعرف الفريد للنظام (System unique resource identifier) |
| `uuid` | string | المعرف العالمي الفريد (Universal unique identifier) |
| `contract_id` | string | معرف العقد الخارجي (External contract identifier) |

---

### Contract Dates

| Field | Type | Description |
|-------|------|-------------|
| `tts_date_dgr` | timestamp | تاريخ إنشاء العقد (Contract creation date - Unix timestamp) |
| `tts_start_date_dgr` | timestamp | تاريخ بداية العقد (Contract start date - Unix timestamp) |
| `tts_end_date_dgr` | timestamp | تاريخ نهاية العقد (Contract end date - Unix timestamp) |
| `tts_date_hj` | string | تاريخ العقد بالتقويم الهجري (Contract date - Hijri calendar) |
| `tts_start_date_hj` | string | تاريخ البداية بالتقويم الهجري (Start date - Hijri calendar) |
| `tts_end_date_hj` | string | تاريخ النهاية بالتقويم الهجري (End date - Hijri calendar) |
| `dt_start_day` | string | تاريخ البداية بالتنسيق الميلادي (Start date - Gregorian format YYYY-MM-DD) |
| `dt_end_day` | string | تاريخ النهاية بالتنسيق الميلادي (End date - Gregorian format YYYY-MM-DD) |
| `tts_end_view` | string | تاريخ النهاية للعرض (End date for display) |
| `tts_follow_up_date_dgr` | timestamp | تاريخ المتابعة (Follow-up date - Unix timestamp) |
| `tts_renewal_notification_dgr` | timestamp | تاريخ إشعار التجديد (Renewal notification date - Unix timestamp) |
| `tts_payments_start_from_dgr` | timestamp | تاريخ بداية الدفعات (Payments start date - Unix timestamp) |

---

### Contract Duration & Period

| Field | Type | Description |
|-------|------|-------------|
| `tts_days` | string | عدد أيام العقد (Contract duration in days) |
| `tts_duration` | string | مدة العقد بالأشهر (Contract duration in months) |
| `tts_period` | string/null | فترة العقد (Contract period) |
| `free_period` | string | فترة السماح/المجانية (Free grace period) |
| `day_remaining` | string | الأيام المتبقية للعقد (Remaining days until contract ends) |
| `tts_end_type` | string | نوع نهاية العقد (Contract end type: `period`) |
| `cal_type` | string | نوع التقويم المستخدم (Calendar type: `cal_gr` = Gregorian) |

---

### Payment Information

| Field | Type | Description |
|-------|------|-------------|
| `payment_term` | string | شروط الدفع (Payment terms: `monthly`, `quarterly`, `semiannually`, `annually`) |
| `pay_cycle` | string | دورة الدفع (Payment cycle) |
| `tts_num_of_installments` | string | عدد الأقساط (Number of installments) |
| `dt_start_installments` | string | بداية الأقساط (Installments start date) |
| `price_amt` | string | مبلغ الدفعة الواحدة (Single payment amount) |
| `price_annually` | string | السعر السنوي (Annual price) |
| `tts_amt` | string | إجمالي مبلغ العقد (Total contract amount) |
| `amt_tot` | string | المبلغ الإجمالي (Total amount) |
| `amt_collect` | string | المبلغ المحصل (Collected amount) |
| `amt_due` | string | المبلغ المستحق (Due amount) |
| `amt_balance` | string | الرصيد المتبقي (Remaining balance) |
| `amt_payable` | string | المبلغ الواجب دفعه (Payable amount) |
| `pct_tax` | string | نسبة الضريبة (Tax percentage) |
| `tts_insurance` | string/null | مبلغ التأمين (Insurance amount) |
| `tts_add_wt_insurance` | string | التأمين الإضافي (Additional insurance with tax) |
| `tts_tot_additional_item_alc` | string/null | إجمالي البنود الإضافية (Total additional items) |
| `tts_contract_net_price_alc` | string/null | صافي سعر العقد (Contract net price) |
| `tts_base` | string | أساس احتساب العقد (Contract calculation base: `full_inst`) |

---

### Property Information

| Field | Type | Description |
|-------|------|-------------|
| `are_id` | string | معرف الوحدة/العقار (Property/Unit ID) |
| `are_are_id` | string | معرف العقار الأب (Parent property ID) |
| `are_code` | string | كود الوحدة (Unit code) |
| `are_desc_fo` | string | وصف الوحدة بالعربية (Unit description - Arabic) |
| `are_desc_lo` | string/null | وصف الوحدة بالإنجليزية (Unit description - English) |
| `are_owner` | string | معرف مالك العقار (Property owner ID) |
| `lease_area` | string | مساحة الإيجار (Lease area) |
| `prop_img` | string/null | صورة العقار (Property image) |
| `prop_check` | string | حالة فحص العقار (Property check status) |
| `multi_units` | string | وحدات متعددة (Multiple units flag: `0` = No, `1` = Yes) |
| `unit_id` | string | معرف الوحدة (Unit ID) |
| `tts_units` | string | عدد الوحدات في العقد (Number of units in contract) |

---

### Tenant/Customer Information

| Field | Type | Description |
|-------|------|-------------|
| `atr_id` | string | معرف المستأجر (Tenant ID) |
| `atr_code` | string/null | كود المستأجر (Tenant code) |
| `atr_official_name_fo` | string | اسم المستأجر الرسمي (Official tenant name) |
| `atr_official_id` | string | رقم هوية المستأجر (Tenant official ID number) |
| `atr_email` | string/null | البريد الإلكتروني للمستأجر (Tenant email) |
| `atr_mobile_num` | string | رقم جوال المستأجر (Tenant mobile number) |
| `contact_phone` | string/null | رقم هاتف التواصل (Contact phone) |
| `customer_code` | string/null | كود العميل (Customer code) |

---

### Accounting Information

| Field | Type | Description |
|-------|------|-------------|
| `client_acc_id` | string | معرف حساب العميل (Client account ID) |
| `client_acc_code` | string | كود حساب العميل (Client account code) |
| `tts_acc_id` | string | معرف حساب العقد (Contract account ID) |
| `tts_acc_code` | string | كود حساب العقد (Contract account code) |
| `fcu_code` | string/null | كود العملة (Currency code) |
| `fcu_desc_lo` | string/null | وصف العملة بالإنجليزية (Currency description - English) |
| `fcu_desc_fo` | string/null | وصف العملة بالعربية (Currency description - Arabic) |

---

### Contract Status

| Field | Type | Description |
|-------|------|-------------|
| `doc_status` | string | حالة المستند (Document status: `incomplete`, `complete`) |
| `tts_validity` | string | صلاحية العقد (Contract validity: `active`, `expired`, `cancelled`) |
| `acl_status_code` | string | كود حالة النظام (System status code) |
| `staus_desc_en` | string/null | وصف الحالة بالإنجليزية (Status description - English) |
| `staus_desc_ar` | string/null | وصف الحالة بالعربية (Status description - Arabic) |
| `draft` | string | مسودة (Draft status: `0` = Published, `1` = Draft) |
| `archived` | string | مؤرشف (Archived: `0` = No, `1` = Yes) |

---

### Contract Type & Classification

| Field | Type | Description |
|-------|------|-------------|
| `contract_type` | string | نوع العقد (Contract type: `residential`, `commercial`) |
| `contract_type_view` | string | نوع العقد للعرض (Contract type for display) |
| `entry_type` | string | طريقة الإدخال (Entry type: `manual`, `automatic`) |
| `tts_contract_place` | string/null | مكان توقيع العقد (Contract signing place) |
| `contract_date_base_desc_en` | string/null | وصف أساس تاريخ العقد بالإنجليزية |
| `contract_date_base_desc_ar` | string/null | وصف أساس تاريخ العقد بالعربية |

---

### Renewal Information

| Field | Type | Description |
|-------|------|-------------|
| `tts_renew` | string | حالة التجديد (Renewal status: `none`, `renewed`, `pending`) |
| `tts_renew_id` | string | معرف عقد التجديد (Renewal contract ID) |
| `old_tts_id` | string | معرف العقد القديم (Old contract ID) |
| `renew_id` | string | معرف التجديد (Renewal ID) |

---

### Follow-up & Notes

| Field | Type | Description |
|-------|------|-------------|
| `follow_up_desc_en` | string/null | وصف المتابعة بالإنجليزية (Follow-up description - English) |
| `follow_up_desc_ar` | string/null | وصف المتابعة بالعربية (Follow-up description - Arabic) |
| `due_note` | string/null | ملاحظات الاستحقاق (Due notes) |
| `tts_note` | string | ملاحظات العقد (Contract notes) |
| `tts_ref` | string | مرجع العقد (Contract reference) |
| `tts_ref_no` | string | رقم المرجع (Reference number) |

---

### Period Descriptions

| Field | Type | Description |
|-------|------|-------------|
| `peroid_desc_en` | string/null | وصف الفترة بالإنجليزية (Period description - English) |
| `peroid_desc_ar` | string/null | وصف الفترة بالعربية (Period description - Arabic) |
| `payment_term_desc_en` | string/null | وصف شروط الدفع بالإنجليزية (Payment term description - English) |
| `payment_term_desc_ar` | string/null | وصف شروط الدفع بالعربية (Payment term description - Arabic) |

---

### Lookup Descriptions

| Field | Type | Description |
|-------|------|-------------|
| `ddv_desc_lo` | string/null | وصف القيمة من القاموس بالإنجليزية (Dictionary value description - English) |
| `ddv_desc_fo` | string/null | وصف القيمة من القاموس بالعربية (Dictionary value description - Arabic) |
| `cri_desc_fo` | string/null | وصف المعيار (Criteria description) |
| `ecd_desc_fo` | string/null | وصف الكود الخارجي (External code description) |
| `ssu_id` | string | معرف الوحدة الفرعية (Sub-unit ID) |
| `ssu_desc_fo` | string/null | وصف الوحدة الفرعية بالعربية (Sub-unit description - Arabic) |
| `ssu_desc_lo` | string/null | وصف الوحدة الفرعية بالإنجليزية (Sub-unit description - English) |

---

### Audit Trail

| Field | Type | Description |
|-------|------|-------------|
| `create_by` | string | معرف منشئ العقد (Created by user ID) |
| `dt_created` | timestamp | تاريخ الإنشاء (Creation date - Unix timestamp) |
| `update_by` | string | معرف آخر محدث (Updated by user ID) |
| `dt_updated` | timestamp | تاريخ آخر تحديث (Last update date - Unix timestamp) |
| `release_user` | string | معرف مستخدم الإصدار (Release user ID) |
| `release_date` | timestamp | تاريخ الإصدار (Release date - Unix timestamp) |
| `release_list` | string | قائمة الإصدار (Release list) |
| `confirm_user` | string | معرف مستخدم التأكيد (Confirm user ID) |
| `confirm_date` | timestamp | تاريخ التأكيد (Confirm date - Unix timestamp) |
| `dt_checkout` | timestamp | تاريخ إخلاء الوحدة (Checkout date) |

---

### Additional Fields

| Field | Type | Description |
|-------|------|-------------|
| `myo_code` | string | كود السنة المالية (Fiscal year code) |
| `branch_id` | string | معرف الفرع (Branch ID) |
| `sub_seq` | string | التسلسل الفرعي (Sub sequence) |
| `tts_remaining` | string | المتبقي من العقد (Contract remaining) |
| `tts_img` | string/null | صورة العقد (Contract image) |
| `tts_cap` | string | السقف/الحد الأعلى (Cap/ceiling amount) |
| `tts_maint` | string | مبلغ الصيانة (Maintenance amount) |
| `marketer` | string | معرف المسوق (Marketer ID) |

---

### Ejar Integration (إيجار)

| Field | Type | Description |
|-------|------|-------------|
| `ejar_tts_id` | string/null | معرف العقد في نظام إيجار (Ejar contract ID) |
| `is_sync` | string | حالة المزامنة مع إيجار (Sync status with Ejar: `0` = Not synced, `1` = Synced) |

---

## Payment Term Values

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `monthly` | Monthly | شهري |
| `quarterly` | Quarterly | ربع سنوي |
| `semiannually` | Semi-annually | نصف سنوي |
| `annually` | Annually | سنوي |

---

## Contract Validity Values

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `active` | Active | نشط |
| `expired` | Expired | منتهي |
| `cancelled` | Cancelled | ملغي |

---

## Contract Type Values

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `residential` | Residential | سكني |
| `commercial` | Commercial | تجاري |

---

## Notes

- All timestamp fields are Unix timestamps (seconds since 1970-01-01)
- Fields ending with `_fo` typically contain Arabic text (First Official language)
- Fields ending with `_lo` typically contain English text (Local language)
- Fields ending with `_dgr` contain Gregorian dates as timestamps
- Fields ending with `_hj` contain Hijri dates

