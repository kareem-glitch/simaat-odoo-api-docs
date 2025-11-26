# 📚 Simaat Odoo API Documentation

<div align="center">

![Simaat](https://img.shields.io/badge/Simaat-Property%20Management-blue?style=for-the-badge)
![API](https://img.shields.io/badge/API-Odoo%20v1-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Active-success?style=for-the-badge)

**وثائق شرح API نظام سمات لإدارة الأملاك**

[Postman Documentation](https://documenter.getpostman.com/view/22392609/2s9Yyy8y5H) • [API Base URL](https://dev.simaat.sa/api/odoo/v1)

</div>

---

## 🌐 Overview | نظرة عامة

This repository contains detailed documentation for the **Simaat Odoo API** endpoints. The documentation explains each field in the API responses with descriptions in both **Arabic** and **English**.

هذا المستودع يحتوي على توثيق تفصيلي لـ API نظام سمات. التوثيق يشرح كل حقل في استجابات الـ API بالعربي والإنجليزي.

---

## 🔗 Postman Collection

For interactive API testing and examples, visit the official Postman documentation:

**📮 [Simaat Odoo API - Postman Documentation](https://documenter.getpostman.com/view/22392609/2s9Yyy8y5H)**

---

## 📁 Documentation Files | ملفات التوثيق

| File | Endpoint | Description |
|------|----------|-------------|
| [contracts_api_documentation.md](./contracts_api_documentation.md) | `/contracts/list` | العقود - Contracts |
| [clients_api_documentation.md](./clients_api_documentation.md) | `/clients/list` | العملاء - Clients |
| [installments_api_documentation.md](./installments_api_documentation.md) | `/installments/list` | الأقساط - Installments |
| [accounts_api_documentation.md](./accounts_api_documentation.md) | `/accounts/list` | الحسابات - Accounts |
| [cost_centers_api_documentation.md](./cost_centers_api_documentation.md) | `/cost-centers/list` | مراكز التكلفة - Cost Centers |
| [properties_api_documentation.md](./properties_api_documentation.md) | `/properties/list` | العقارات - Properties |
| [units_api_documentation.md](./units_api_documentation.md) | `/units/list` | الوحدات - Units |

---

## 🚀 API Base URL

```
https://dev.simaat.sa/api/odoo/v1
```

---

## 📋 Available Endpoints | نقاط النهاية المتاحة

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/contracts/list` | قائمة العقود |
| `GET` | `/clients/list` | قائمة العملاء |
| `GET` | `/installments/list?contract_id={id}` | قائمة الأقساط لعقد معين |
| `GET` | `/accounts/list` | شجرة الحسابات |
| `GET` | `/cost-centers/list` | مراكز التكلفة |
| `GET` | `/properties/list` | قائمة العقارات |
| `GET` | `/units/list` | قائمة الوحدات |

---

## 📖 Response Format | صيغة الاستجابة

All API responses follow this structure:

```json
{
  "data": [...],
  "status": "OK",
  "count": 10
}
```

| Field | Type | Description |
|-------|------|-------------|
| `data` | array | مصفوفة البيانات |
| `status` | string | حالة الاستجابة (OK / ERROR) |
| `count` | integer | عدد السجلات المسترجعة |

---

## 🏢 About Simaat | عن سمات

**Simaat** is a comprehensive Property Management System (PMS) designed for the Saudi Arabian real estate market. It provides:

- 🏠 Property & Unit Management (إدارة العقارات والوحدات)
- 📝 Contract Management (إدارة العقود)
- 💰 Financial Management (الإدارة المالية)
- 📊 Accounting Integration (التكامل المحاسبي)
- 🔗 Ejar Platform Integration (تكامل منصة إيجار)

---

## 📝 License

This documentation is provided for integration purposes with the Simaat platform.

---

## 📞 Contact | تواصل

For API access and support, please contact the Simaat team.

---

<div align="center">

**Made with ❤️ for Simaat Platform**

</div>

