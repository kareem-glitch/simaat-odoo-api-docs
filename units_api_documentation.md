# Units API Documentation

## Endpoint
```
GET https://dev.simaat.sa/api/odoo/v1/units/list
```

---

## Overview

The Units API returns rental units (الوحدات الإيجارية) that are part of properties/buildings. This endpoint returns the same data structure as the Properties API, but specifically filtered to show **only rentable units** (level 2 in the property hierarchy).

> **Note:** For complete field documentation, please refer to **[Properties API Documentation](properties_api_documentation.md)**. This document highlights the key differences and unit-specific usage.

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
| `data` | array | مصفوفة بيانات الوحدات (Array of unit objects) |
| `status` | string | حالة الاستجابة (Response status) |
| `count` | integer | عدد الوحدات (Number of units returned) |

---

## Difference: Properties vs Units

| Aspect | Properties API | Units API |
|--------|----------------|-----------|
| **Endpoint** | `/properties/list` | `/units/list` |
| **Returns** | All properties & units | Only rentable units |
| **Level** | Level 1 (Buildings) + Level 2 (Units) | Level 2 only (Units) |
| **Use Case** | Full property tree | List of rentable units |

---

## Unit Types Examples (أنواع الوحدات)

### Residential Units (الوحدات السكنية)

| Arabic | English | Description |
|--------|---------|-------------|
| شقة | Apartment | وحدة سكنية |
| استوديو | Studio | استوديو |
| فيلا | Villa | فيلا |
| دوبلكس | Duplex | شقة دوبلكس |
| غرفة | Room | غرفة |

### Commercial Units (الوحدات التجارية)

| Arabic | English | Description |
|--------|---------|-------------|
| محل | Store | محل تجاري |
| مكتب | Office | مكتب |
| معرض | Showroom | معرض |
| مستودع | Warehouse | مخزن/مستودع |
| ورشة | Workshop | ورشة |

---

## Key Fields for Units

### Unit Identification (معرفات الوحدة)

| Field | Type | Description |
|-------|------|-------------|
| `prop_id` | string | معرف الوحدة الفريد (Unique unit identifier) |
| `are_id` | string | معرف المنطقة/الوحدة (Area/Unit ID) |
| `are_code` | string | كود الوحدة (Unit code: e.g., `A000008001`) |
| `unit_no` | string | رقم الوحدة (Unit number: e.g., `1`, `2`, `3`) |
| `floor_no` | string | رقم الطابق (Floor number) |

### Unit Description (وصف الوحدة)

| Field | Type | Description |
|-------|------|-------------|
| `are_desc_fo` | string | اسم الوحدة بالعربية (e.g., `شقة 1`, `محل 2`, `مكتب 3`) |
| `are_desc_en` | string | اسم الوحدة بالإنجليزية (e.g., `Apartment 1`, `Store 2`) |
| `are_desc_full` | string | الاسم الكامل (e.g., `عقار الزهور شقة 1`) |
| `lease_area` | string | مساحة الوحدة بالمتر المربع |

### Parent Property (العقار الأب)

| Field | Type | Description |
|-------|------|-------------|
| `are_are_id` | string | معرف العقار الأب (Parent property ID) |
| `parent_code` | string | كود العقار الأب (e.g., `A000008`) |
| `parent_desc_ar` | string | اسم العقار بالعربية (e.g., `عقار الزهور`) |
| `parent_desc_en` | string | اسم العقار بالإنجليزية |

### Occupancy Status (حالة الإشغال)

| Field | Type | Description |
|-------|------|-------------|
| `is_vacancy` | string | شاغر (`0` = مشغول, `1` = شاغر) |
| `atr_id` | string | معرف المستأجر (`0` = لا يوجد مستأجر) |
| `acl_status_code` | string | كود الحالة (`41920` = شاغر, `41930` = مشغول) |
| `contact_name` | string | اسم المستأجر الحالي |
| `contact_mobile` | string | جوال المستأجر |

### Contract Info (معلومات العقد)

| Field | Type | Description |
|-------|------|-------------|
| `tts_start_date_dgr` | timestamp | بداية العقد (`0` = لا يوجد عقد) |
| `tts_end_date_dgr` | timestamp | نهاية العقد (`0` = لا يوجد عقد) |
| `contract_type` | string | نوع العقد (`residential`, `commercial`) |

### Financial Summary (ملخص مالي)

| Field | Type | Description |
|-------|------|-------------|
| `amt_tot` | string/null | إجمالي المبلغ (`null` = شاغر) |
| `amt_due` | string/null | المستحق (`null` = شاغر) |
| `amt_collect` | string/null | المحصل (`null` = شاغر) |
| `fin_situation` | string | الوضع المالي (`paid`, `debit`) |

---

## Units Hierarchy Example (مثال على الوحدات)

```
📁 عقار الزهور (A000008) - Parent Building
│
├── 🏠 شقة 1 (A000008001) - Floor 1, Unit 1 - مشغول ✓
├── 🏠 شقة 2 (A000008002) - Floor 1, Unit 2 - مشغول ✓
├── 🏠 شقة 3 (A000008003) - Floor 1, Unit 3 - شاغر ○
├── 🏠 شقة 4 (A000008004) - Floor 1, Unit 4 - شاغر ○
├── 🏠 شقة 5 (A000008005) - Floor 1, Unit 5 - مشغول ✓
├── 🏪 محل 1 (A000008006) - Floor 2, Unit 1 - شاغر ○
├── 🏪 محل 2 (A000008007) - Floor 2, Unit 2 - شاغر ○
├── 🏪 محل 3 (A000008008) - Floor 2, Unit 3 - شاغر ○
├── 🏪 محل 4 (A000008009) - Floor 2, Unit 4 - شاغر ○
└── 🏪 محل 5 (A000008010) - Floor 2, Unit 5 - شاغر ○

📁 عقار الياسمين (A000009) - Parent Building
│
├── 🏠 شقة 1 (A000009001) - Floor 1, Unit 1 - مشغول ✓
├── 🏠 شقة 2 (A000009002) - Floor 1, Unit 2 - شاغر ○
├── 🏠 شقة 3 (A000009003) - Floor 1, Unit 3 - شاغر ○
├── 🏠 شقة 4 (A000009004) - Floor 1, Unit 4 - مشغول ✓
├── 🏢 مكتب 1 (A000009005) - Floor 2, Unit 1 - شاغر ○
├── 🏢 مكتب 2 (A000009006) - Floor 2, Unit 2 - مشغول ✓
├── 🏢 مكتب 3 (A000009007) - Floor 2, Unit 3 - شاغر ○
└── 🏢 مكتب 4 (A000009008) - Floor 2, Unit 4 - شاغر ○
```

---

## Unit Status Quick Reference

### Occupied Unit (وحدة مشغولة)

```json
{
  "is_vacancy": "0",
  "atr_id": "77",
  "acl_status_code": "41930",
  "contact_name": "رغد نصر",
  "contact_mobile": "966551511551",
  "fin_situation": "debit",
  "tts_start_date_dgr": "1706798740",
  "tts_end_date_dgr": "1738334741",
  "amt_tot": "12000.00",
  "amt_due": "12000.00"
}
```

### Vacant Unit (وحدة شاغرة)

```json
{
  "is_vacancy": "1",
  "atr_id": "0",
  "acl_status_code": "41920",
  "contact_name": "",
  "contact_mobile": "0",
  "fin_situation": "paid",
  "tts_start_date_dgr": "0",
  "tts_end_date_dgr": "0",
  "amt_tot": null,
  "amt_due": null
}
```

---

## Management Type (نوع الإدارة)

| `ioe_code` | Description | Use Case |
|------------|-------------|----------|
| `manage` | إدارة أملاك الغير | وحدات مُدارة لصالح المالك (عمولة على التحصيل) |
| `ownership` | ملكية مباشرة | وحدات مملوكة للشركة (بدون عمولة) |

---

## Common Filtering Scenarios

### 1. Get Vacant Units (الوحدات الشاغرة)
Filter where: `is_vacancy = "1"` OR `atr_id = "0"`

### 2. Get Occupied Units (الوحدات المشغولة)
Filter where: `is_vacancy = "0"` AND `atr_id != "0"`

### 3. Get Residential Units (الوحدات السكنية)
Filter where: `contract_type = "residential"`

### 4. Get Commercial Units (الوحدات التجارية)
Filter where: `contract_type = "commercial"`

### 5. Get Units by Building (وحدات عقار معين)
Filter where: `are_are_id = "{parent_property_id}"`

### 6. Get Units with Outstanding Balance (وحدات بمستحقات)
Filter where: `fin_situation = "debit"` AND `amt_due > 0`

---

## Notes

- All fields are identical to the Properties API
- Units always have `prop_level = "2"`
- The `are_code` follows pattern: `{parent_code}{unit_sequence}`
- Example: Parent `A000008` → Units `A000008001`, `A000008002`, etc.
- `tts_start_date_dgr = 0` indicates no active contract
- Amount fields are `null` for vacant units
- Commission applies only to `ioe_code = "manage"` units

