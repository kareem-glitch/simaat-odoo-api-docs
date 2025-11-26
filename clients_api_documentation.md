# Clients API Documentation

## Endpoint
```
GET https://dev.simaat.sa/api/odoo/v1/clients/list
```

---

## Response Structure

```json
{
  "data": [...],
  "status": "OK",
  "count": 4
}
```

| Field | Type | Description |
|-------|------|-------------|
| `data` | array | مصفوفة بيانات العملاء (Array of client objects) |
| `status` | string | حالة الاستجابة (Response status) |
| `count` | integer | عدد العملاء المسترجعين (Number of clients returned) |

---

## Client Object Fields

### Client Identification

| Field | Type | Description |
|-------|------|-------------|
| `client_id` | string | معرف العميل الفريد (Unique client identifier) |
| `uuid` | string | المعرف العالمي الفريد (Universal unique identifier) |

---

### Entity Information (معلومات الكيان)

| Field | Type | Description |
|-------|------|-------------|
| `entity_type` | string | نوع الكيان (Entity type: `individual`, `company`) |
| `entity_idtype` | string | نوع وثيقة الهوية (ID document type: `nid`, `iqama`, `passport`, `cr`) |
| `entity_number` | string | رقم الهوية/السجل (ID/Registration number) |
| `entity_name` | string | اسم الكيان بالعربية (Entity name - Arabic) |
| `entity_name_en` | string | اسم الكيان بالإنجليزية (Entity name - English) |
| `entity_dob` | string | تاريخ الميلاد ميلادي (Date of birth - Gregorian: YYYY-MM-DD) |
| `entity_dob_hj` | string | تاريخ الميلاد هجري (Date of birth - Hijri) |
| `companyname` | string | اسم الشركة (Company name - for company entities) |

---

### Contact Information (معلومات التواصل)

| Field | Type | Description |
|-------|------|-------------|
| `contact_name` | string | اسم جهة الاتصال بالعربية (Contact name - Arabic) |
| `contact_name_en` | string | اسم جهة الاتصال بالإنجليزية (Contact name - English) |
| `contact_email` | string | البريد الإلكتروني (Email address) |
| `contact_mobile` | string | رقم الجوال (Mobile number) |
| `contact_phone` | string | رقم الهاتف (Phone number) |

---

### Address Information (معلومات العنوان)

| Field | Type | Description |
|-------|------|-------------|
| `client_address` | string | عنوان العميل (Client address) |
| `client_city` | string | المدينة (City) |
| `client_region` | string | المنطقة (Region) |
| `postcode` | string | الرمز البريدي (Postal code) |
| `client_postal_code` | string | الرمز البريدي للعميل (Client postal code) |
| `client_country` | string | الدولة (Country) |

---

### Accounting Information (المعلومات المحاسبية)

| Field | Type | Description |
|-------|------|-------------|
| `client_acc_id` | string | معرف حساب العميل (Client account ID) |
| `client_acc_code` | string | كود حساب العميل (Client account code) |
| `client_tax_id` | string | معرف الحساب الضريبي (Tax account ID) |
| `client_tax_code` | string | كود الحساب الضريبي (Tax account code) |
| `client_cost` | string | مركز التكلفة (Cost center) |
| `client_credit` | string | رصيد الائتمان (Credit balance) |
| `client_balance` | string | رصيد العميل (Client balance) |
| `vat_number` | string | الرقم الضريبي (VAT number) |

---

### Tax Settings (إعدادات الضرائب)

| Field | Type | Description |
|-------|------|-------------|
| `taxexempt` | string | معفى من الضريبة (Tax exempt: `0` = No, `1` = Yes) |
| `inc_tax` | string | شامل الضريبة (Tax inclusive: `0` = No, `1` = Yes) |
| `tax_onbehalf` | string | ضريبة بالنيابة (Tax on behalf: `0` = No, `1` = Yes) |

---

### Billing Settings (إعدادات الفوترة)

| Field | Type | Description |
|-------|------|-------------|
| `overideduenotices` | string | تجاوز إشعارات التأخر (Override due notices: `0` = No, `1` = Yes) |
| `separateinvoices` | string | فواتير منفصلة (Separate invoices: `0` = No, `1` = Yes) |
| `separate_inv` | string | فصل الفواتير (Separate invoices flag) |
| `disableautocc` | string | تعطيل الخصم التلقائي (Disable auto credit card: `0` = No, `1` = Yes) |
| `billingcid` | string | معرف جهة الفوترة (Billing contact ID) |
| `ign_onbehalf` | string | تجاهل بالنيابة (Ignore on behalf: `0` = No, `1` = Yes) |

---

### Client Classification (تصنيف العميل)

| Field | Type | Description |
|-------|------|-------------|
| `client_class` | string | تصنيف العميل (Client class: `tenant`, `owner`, `broker`) |
| `client_group` | string | مجموعة العميل (Client group ID) |
| `segment` | string | شريحة العميل (Client segment) |

---

### Personal Information (المعلومات الشخصية)

| Field | Type | Description |
|-------|------|-------------|
| `gender` | string | الجنس (Gender: `male`, `female`) |
| `religion` | string/null | الديانة (Religion) |
| `nationality` | string | الجنسية (Nationality) |
| `cal_type` | string | نوع التقويم (Calendar type: `cal_gr` = Gregorian, `cal_hj` = Hijri) |

---

### Employment Information (معلومات العمل)

| Field | Type | Description |
|-------|------|-------------|
| `job_title` | string | المسمى الوظيفي (Job title) |
| `job_address` | string | عنوان العمل (Job address) |
| `job_address_prev` | string | عنوان العمل السابق (Previous job address) |
| `monthly_income` | string | الدخل الشهري (Monthly income) |
| `dependents` | string | عدد المعالين (Number of dependents) |

---

### Representative Information (معلومات الممثل/الوكيل)

| Field | Type | Description |
|-------|------|-------------|
| `rep_himself` | string | يمثل نفسه (Represents himself: `0` = No, `1` = Yes) |
| `rep_entity_idtype` | string | نوع هوية الممثل (Representative ID type) |
| `rep_entity_number` | string | رقم هوية الممثل (Representative ID number) |
| `rep_number` | string | رقم التوكيل (Power of attorney number) |
| `rep_type` | string | نوع التمثيل (Representation type) |
| `rep_issue_date` | timestamp | تاريخ إصدار التوكيل (POA issue date - Unix timestamp) |
| `rep_expiry_date` | timestamp | تاريخ انتهاء التوكيل (POA expiry date - Unix timestamp) |
| `rep_entity_dob` | string | تاريخ ميلاد الممثل (Representative date of birth) |

---

### Bank Information (المعلومات البنكية)

| Field | Type | Description |
|-------|------|-------------|
| `bank_name` | string | اسم البنك (Bank name) |
| `bank_client_name` | string | اسم العميل في البنك (Client name at bank) |
| `bank_iban` | string | رقم الآيبان (IBAN number) |
| `bank_address` | string | عنوان البنك (Bank address) |
| `bank_swift` | string | كود السويفت (SWIFT code) |

---

### Remote E-Invoice Settings (إعدادات الفوترة الإلكترونية عن بعد)

| Field | Type | Description |
|-------|------|-------------|
| `rmt_einv` | string | الفوترة الإلكترونية عن بعد (Remote e-invoice: `0` = Disabled, `1` = Enabled) |
| `rmt_server` | string | خادم الفوترة (E-invoice server URL) |
| `rmt_token` | string | رمز المصادقة (Authentication token) |

---

### Status & System (الحالة والنظام)

| Field | Type | Description |
|-------|------|-------------|
| `acl_status_code` | string | كود حالة النظام (System status code) |
| `lastlogin` | timestamp/null | آخر تسجيل دخول (Last login timestamp) |

---

### Media & Assets (الوسائط)

| Field | Type | Description |
|-------|------|-------------|
| `client_img` | string | صورة العميل (Client image path) |
| `claim_sp_logo` | string | استخدام شعار مقدم الخدمة (Claim service provider logo: `0` = No, `1` = Yes) |

---

### Notes (الملاحظات)

| Field | Type | Description |
|-------|------|-------------|
| `client_notes` | string | ملاحظات العميل (Client notes) |

---

### Ejar Integration (تكامل إيجار)

| Field | Type | Description |
|-------|------|-------------|
| `ejar_client_id` | string | معرف العميل في نظام إيجار (Ejar client UUID) |
| `ejar_iban` | string/null | رقم الآيبان في إيجار (Ejar IBAN) |
| `is_sync` | string | حالة المزامنة (Sync status: `0` = Not synced, `1` = Synced) |

---

### Audit Trail (سجل التدقيق)

| Field | Type | Description |
|-------|------|-------------|
| `create_by` | string | معرف منشئ السجل (Created by user ID) |
| `dt_created` | timestamp | تاريخ الإنشاء (Creation date - Unix timestamp) |
| `update_by` | string | معرف آخر محدث (Updated by user ID) |
| `dt_updated` | timestamp | تاريخ آخر تحديث (Last update date - Unix timestamp) |

---

## Lookup Values

### Entity Type (نوع الكيان)

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `individual` | Individual | فرد |
| `company` | Company | شركة |

---

### Entity ID Type (نوع وثيقة الهوية)

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `nid` | National ID | الهوية الوطنية |
| `iqama` | Iqama (Residence Permit) | الإقامة |
| `passport` | Passport | جواز السفر |
| `cr` | Commercial Registration | السجل التجاري |

---

### Client Class (تصنيف العميل)

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `tenant` | Tenant | مستأجر |
| `owner` | Owner | مالك |
| `broker` | Broker | وسيط |

---

### Gender (الجنس)

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `male` | Male | ذكر |
| `female` | Female | أنثى |

---

### Calendar Type (نوع التقويم)

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `cal_gr` | Gregorian | ميلادي |
| `cal_hj` | Hijri | هجري |

---

## Notes

- All timestamp fields are Unix timestamps (seconds since 1970-01-01)
- Mobile numbers should include country code (e.g., `966` for Saudi Arabia)
- IBAN format for Saudi Arabia: `SA` + 22 characters
- `client_img` contains relative path to the image file
- Empty strings (`""`) indicate no value set
- `null` indicates the field was never set or is not applicable

