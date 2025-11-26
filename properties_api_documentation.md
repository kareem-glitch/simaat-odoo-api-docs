# Properties API Documentation

## Endpoint
```
GET https://dev.simaat.sa/api/odoo/v1/properties/list
```

---

## Response Structure

```json
{
  "data": [...],
  "status": "OK",
  "count": 18
}
```

| Field | Type | Description |
|-------|------|-------------|
| `data` | array | مصفوفة بيانات الوحدات العقارية (Array of property/unit objects) |
| `status` | string | حالة الاستجابة (Response status) |
| `count` | integer | عدد الوحدات (Number of properties returned) |

---

## Property Object Fields

### Property Identification (معرفات الوحدة)

| Field | Type | Description |
|-------|------|-------------|
| `prop_id` | string | معرف الوحدة الفريد (Unique property identifier) |
| `are_id` | string | معرف المنطقة/الوحدة (Area/Unit ID) |
| `are_code` | string | كود الوحدة (Unit code) |
| `res_uid` | string | المعرف الفريد للنظام (System unique resource identifier) |
| `uuid` | string | المعرف العالمي الفريد (Universal unique identifier) |

---

### Property Hierarchy (التسلسل الهرمي للعقار)

| Field | Type | Description |
|-------|------|-------------|
| `are_are_id` | string | معرف العقار الأب (Parent property ID) |
| `parent_code` | string | كود العقار الأب (Parent property code) |
| `parent_desc_ar` | string | اسم العقار الأب بالعربية (Parent property name - Arabic) |
| `parent_desc_en` | string | اسم العقار الأب بالإنجليزية (Parent property name - English) |
| `prop_level` | string | مستوى الوحدة في الشجرة (Property level in hierarchy) |
| `prop_sub` | string | عدد الوحدات الفرعية (Number of sub-units) |

---

### Property Description (وصف الوحدة)

| Field | Type | Description |
|-------|------|-------------|
| `are_desc_fo` | string | اسم الوحدة بالعربية (Unit name - Arabic) |
| `are_desc_en` | string | اسم الوحدة بالإنجليزية (Unit name - English) |
| `are_desc_full` | string | الاسم الكامل للوحدة (Full unit name with parent) |
| `are_en_full` | string/null | الاسم الكامل بالإنجليزية (Full name - English) |
| `prop_note` | string | ملاحظات الوحدة (Property notes) |

---

### Ownership & Management (الملكية والإدارة)

| Field | Type | Description |
|-------|------|-------------|
| `are_owner` | string | معرف المالك (Owner client ID) |
| `are_intermediate` | string | معرف الوسيط (Intermediate/Broker ID) |
| `are_agent` | string | معرف الوكيل (Agent ID) |
| `atr_id` | string | معرف المستأجر الحالي (Current tenant ID, `0` = vacant) |
| `ioe_code` | string | نوع الإدارة (Management type: `manage`, `ownership`) |
| `collector` | string | معرف المحصل (Collector ID) |

---

### Property Details (تفاصيل الوحدة)

| Field | Type | Description |
|-------|------|-------------|
| `unit_no` | string | رقم الوحدة (Unit number) |
| `floor_no` | string | رقم الطابق (Floor number) |
| `rooms` | string | عدد الغرف (Number of rooms) |
| `lease_area` | string | مساحة الإيجار بالمتر المربع (Lease area in sqm) |
| `build_area` | string | مساحة البناء (Building area) |
| `land_area` | string | مساحة الأرض (Land area) |
| `prop_floors` | string | عدد طوابق المبنى (Total building floors) |
| `prop_units` | string | عدد الوحدات (Number of units) |

---

### Location Information (معلومات الموقع)

| Field | Type | Description |
|-------|------|-------------|
| `prop_address` | string | العنوان الكامل (Full address) |
| `prop_district` | string | الحي (District) |
| `prop_city` | string | المدينة (City) |
| `prop_region` | string | المنطقة (Region) |
| `country` | string | الدولة (Country) |
| `street_name` | string | اسم الشارع (Street name) |
| `building_number` | string | رقم المبنى (Building number) |
| `building_postal_code` | string | الرمز البريدي (Postal code) |
| `additional_number` | string | الرقم الإضافي (Additional number) |
| `prop_borders` | string | حدود العقار (Property borders) |

---

### Geographic Coordinates (الإحداثيات الجغرافية)

| Field | Type | Description |
|-------|------|-------------|
| `prop_lat` | string | خط العرض (Latitude) |
| `prop_lng` | string | خط الطول (Longitude) |
| `prop_coord` | string | الإحداثيات متوفرة (Coordinates available: `0` = No, `1` = Yes) |
| `prop_coord_det` | string | تفاصيل الإحداثيات (Coordinate details) |

---

### Occupancy Information (معلومات الإشغال)

| Field | Type | Description |
|-------|------|-------------|
| `prop_child_tot` | string | إجمالي الوحدات الفرعية (Total child units) |
| `prop_child_ava` | string | الوحدات الشاغرة (Available/Vacant units) |
| `prop_child_occ` | string | الوحدات المشغولة (Occupied units) |
| `prop_occ_rate` | string | نسبة الإشغال (Occupancy rate: 0.00 - 1.00) |
| `is_vacancy` | string | شاغر (Is vacant: `0` = No, `1` = Yes) |
| `is_rentable` | string | قابل للإيجار (Is rentable: `0` = No, `1` = Yes) |

---

### Financial Information (المعلومات المالية)

| Field | Type | Description |
|-------|------|-------------|
| `amt_tot` | string/null | إجمالي المبلغ (Total amount) |
| `amt_collect` | string/null | المبلغ المحصل (Collected amount) |
| `amt_due` | string/null | المبلغ المستحق (Due amount) |
| `amt_balance` | string | الرصيد المتبقي (Balance) |
| `amt_payable` | string/null | المبلغ الواجب دفعه (Payable amount) |
| `amt_paid` | string | المبلغ المدفوع (Paid amount) |
| `amt_insur` | string | مبلغ التأمين (Insurance amount) |
| `monthly` | string | الإيجار الشهري (Monthly rent) |
| `px_selling` | string | سعر البيع (Selling price) |
| `fin_situation` | string | الوضع المالي (Financial situation: `paid`, `debit`, `credit`) |

---

### Commission Information (معلومات العمولة)

| Field | Type | Description |
|-------|------|-------------|
| `due_comm` | string | حالة استحقاق العمولة (Commission due status) |
| `pct_comm` | string | نسبة العمولة (Commission percentage) |
| `fxd_comm` | string | عمولة ثابتة (Fixed commission) |
| `amt_comm` | string | مبلغ العمولة (Commission amount) |
| `amt_comm_tot` | string | إجمالي العمولة (Total commission) |
| `amt_expense` | string | المصروفات (Expenses) |

---

### Contract Information (معلومات العقد)

| Field | Type | Description |
|-------|------|-------------|
| `tts_start_date_dgr` | timestamp | تاريخ بداية العقد (Contract start date - Unix timestamp) |
| `tts_end_date_dgr` | timestamp | تاريخ نهاية العقد (Contract end date - Unix timestamp) |
| `contract_type` | string | نوع العقد (Contract type: `residential`, `commercial`) |
| `contract_type_view` | string | نوع العقد للعرض (Contract type for display) |
| `myo_code` | string | كود السنة المالية (Fiscal year code) |

---

### Deed Information (معلومات الصك)

| Field | Type | Description |
|-------|------|-------------|
| `deed_no` | string | رقم الصك (Deed number) |
| `deed_issue` | string | تاريخ إصدار الصك (Deed issue date - Gregorian) |
| `deed_issue_hj` | string | تاريخ إصدار الصك هجري (Deed issue date - Hijri) |
| `deed_type` | string | نوع الوثيقة (Deed type) |
| `deed_name` | string | اسم الوثيقة (Deed name) |
| `issue_place` | string | مكان الإصدار (Issue place) |
| `issued_by` | string | جهة الإصدار (Issued by) |

---

### Utilities & Meters (العدادات والخدمات)

| Field | Type | Description |
|-------|------|-------------|
| `elec_meter` | string/null | عداد الكهرباء (Electricity meter) |
| `gas_meter` | string/null | عداد الغاز (Gas meter) |
| `water_meter` | string/null | عداد المياه (Water meter) |

---

### Guard Information (معلومات الحارس)

| Field | Type | Description |
|-------|------|-------------|
| `guard_name` | string | اسم الحارس (Guard name) |
| `guard_id` | string | هوية الحارس (Guard ID) |
| `guard_mobile` | string | جوال الحارس (Guard mobile) |

---

### Tenant Contact (معلومات التواصل مع المستأجر)

| Field | Type | Description |
|-------|------|-------------|
| `contact_name` | string | اسم المستأجر (Tenant name) |
| `contact_mobile` | string | جوال المستأجر (Tenant mobile) |
| `contact_phone` | string/null | هاتف المستأجر (Tenant phone) |

---

### Accounting Codes (أكواد الحسابات)

| Field | Type | Description |
|-------|------|-------------|
| `client_cost` | string | مركز تكلفة العميل/المالك (Client/Owner cost center) |
| `prop_cost` | string | مركز تكلفة الوحدة (Property cost center) |
| `prop_income` | string | حساب الإيرادات (Income account code) |
| `prop_debts` | string | حساب الذمم (Debts account code) |
| `prop_tax` | string | حساب الضريبة (Tax account code) |
| `prop_insur` | string | حساب التأمين (Insurance account code) |
| `prop_expense` | string | حساب المصروفات (Expense account code) |
| `branch_id` | string | معرف الفرع (Branch ID) |
| `branch_cost` | string | مركز تكلفة الفرع (Branch cost center) |

---

### Classification (التصنيف)

| Field | Type | Description |
|-------|------|-------------|
| `ree_code` | string | كود نوع العقار (Real estate type code) |
| `ree_desc_fo` | string | وصف نوع العقار بالعربية (Property type - Arabic) |
| `ree_desc_lo` | string | وصف نوع العقار بالإنجليزية (Property type - English) |
| `prop_usage` | string | استخدام العقار (Property usage: `commercial`, `residential`) |
| `is_asset` | string | أصل ثابت (Is fixed asset: `0` = No, `1` = Yes) |

---

### Media & Attachments (الوسائط والمرفقات)

| Field | Type | Description |
|-------|------|-------------|
| `prop_img` | string/null | صورة الوحدة (Property image path) |
| `prop_att` | string/null | المرفقات (Attachments) |
| `prop_adv` | string/null | الإعلانات (Advertisements) |

---

### Status & Sync (الحالة والمزامنة)

| Field | Type | Description |
|-------|------|-------------|
| `acl_status_code` | string | كود حالة الوحدة (Unit status code) |
| `draft` | string | مسودة (Draft: `0` = Published, `1` = Draft) |
| `is_sync` | string | حالة المزامنة (Sync status: `0` = Not synced, `1` = Synced) |

---

### Ejar Integration (تكامل إيجار)

| Field | Type | Description |
|-------|------|-------------|
| `ejar_prop_id` | string/null | معرف العقار في إيجار (Ejar property ID) |
| `ejar_ownership_number` | string/null | رقم ملكية إيجار (Ejar ownership number) |
| `prop_number` | string/null | رقم العقار (Property number) |

---

### Additional Fields (حقول إضافية)

| Field | Type | Description |
|-------|------|-------------|
| `qitea` | string/null | القطعة (Plot) |
| `scheme` | string/null | المخطط (Scheme/Plan) |
| `cal_type` | string | نوع التقويم (Calendar type: `cal_gr` = Gregorian) |

---

### Audit Trail (سجل التدقيق)

| Field | Type | Description |
|-------|------|-------------|
| `create_by` | string | معرف المنشئ (Created by user ID) |
| `dt_created` | timestamp | تاريخ الإنشاء (Creation date - Unix timestamp) |
| `update_by` | string | معرف المحدث (Updated by user ID) |
| `dt_updated` | timestamp | تاريخ آخر تحديث (Last update date - Unix timestamp) |
| `rel_update` | timestamp | تحديث مرتبط (Related update timestamp) |

---

## Lookup Values

### IOE Code (نوع الإدارة)

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `manage` | Under Management | إدارة أملاك الغير |
| `ownership` | Owned Property | عقار مملوك |

---

### Due Commission (حالة العمولة)

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `nocomm` | No Commission | بدون عمولة |
| `oncollect` | On Collection | عند التحصيل |
| `ondue` | On Due | عند الاستحقاق |

---

### Financial Situation (الوضع المالي)

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `paid` | Paid / No Outstanding | مسدد / لا مستحقات |
| `debit` | Debit / Has Outstanding | مدين / عليه مستحقات |
| `credit` | Credit / Overpaid | دائن / دفع زيادة |

---

### Contract Type (نوع العقد)

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `residential` | Residential | سكني |
| `commercial` | Commercial | تجاري |

---

### Property Usage (استخدام العقار)

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `residential` | Residential | سكني |
| `commercial` | Commercial | تجاري |
| `mixed` | Mixed Use | استخدام متعدد |

---

### ACL Status Codes (أكواد الحالة)

| Code | Description (EN) | Description (AR) |
|------|-----------------|------------------|
| `41920` | Vacant | شاغر |
| `41930` | Occupied | مشغول |

---

### Deed Type (نوع الوثيقة)

| Value | Description (EN) | Description (AR) |
|-------|-----------------|------------------|
| `deed` | Title Deed | صك ملكية |
| `contract` | Contract | عقد |
| `other` | Other Document | وثيقة أخرى |

---

## Property Hierarchy Example (مثال على تسلسل العقارات)

```
عقار الزهور (A000008) - Parent Property
├── شقة 1 (A000008001) - Unit
├── شقة 2 (A000008002) - Unit
├── شقة 3 (A000008003) - Unit
├── شقة 4 (A000008004) - Unit
├── شقة 5 (A000008005) - Unit
├── محل 1 (A000008006) - Unit
├── محل 2 (A000008007) - Unit
├── محل 3 (A000008008) - Unit
├── محل 4 (A000008009) - Unit
└── محل 5 (A000008010) - Unit

عقار الياسمين (A000009) - Parent Property
├── شقة 1 (A000009001) - Unit
├── شقة 2 (A000009002) - Unit
├── شقة 3 (A000009003) - Unit
├── شقة 4 (A000009004) - Unit
├── مكتب 1 (A000009005) - Unit
├── مكتب 2 (A000009006) - Unit
├── مكتب 3 (A000009007) - Unit
└── مكتب 4 (A000009008) - Unit
```

---

## Notes

- All timestamp fields are Unix timestamps (seconds since 1970-01-01)
- `atr_id = 0` indicates the unit is vacant
- `prop_occ_rate` is a decimal between 0.00 (0%) and 1.00 (100%)
- Coordinates are in decimal degrees format (WGS84)
- Amount fields may be `null` for vacant units with no active contracts
- `tts_start_date_dgr = 0` and `tts_end_date_dgr = 0` indicate no active contract
- `prop_level = 2` indicates a unit level (child of a building/property)
- Financial fields reflect the current outstanding amounts for active contracts

