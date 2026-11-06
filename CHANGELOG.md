# Changelog

تغییرهای خود starter. نسخه‌ی نصب‌شده‌ی هر پروژه در `starter.json` ثبت می‌شود و `/sync-starter` از روی این فایل می‌گوید چه چیزی عوض شده.

## 1.1.0

- **تغییر ساختار (نیازمند مهاجرت در پروژه‌های قدیمی):** قوانین عمومی (نقش، قوانین طلایی، نحوه‌ی پاسخ، KPI، قوانین حافظه، راهنمای فایل‌ها) از `CLAUDE.md` به `docs/core-rules.md` رفتند. `CLAUDE.md` فقط PROJECT CONTEXT را نگه می‌دارد و با `@docs/core-rules.md` آن را import می‌کند. پروژه‌های 1.0 را `/sync-starter` مهاجرت می‌دهد.
- اضافه شد: `/sync-starter` برای آپدیت فایل‌های عمومی پروژه‌ها از روی starter.
- اضافه شد: `/new-project` با مرحله‌ی بررسی جای‌نگهدار.
- اضافه شد: `.claude/settings.json` (ممنوعیت خواندن `.env`، کلیدها و فایل‌های SQL).
- اضافه شد: `starter.json` (نسخه + فهرست مسیرهای قابل sync) و همین `CHANGELOG.md`.
- `.gitignore`: `.omc/` اضافه شد.

## 1.0.0

- نسخه‌ی اولیه: `CLAUDE.md`، `docs/`، `notes/`، دستورهای `/wrapup`، `/memory-cleanup`، `/digest`.
