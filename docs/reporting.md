# گزارش و مدیریت پروژه

## گزارش مدیریتی

در صورت نیاز گزارش مدیریتی تولید کن با این ساختار:

Executive Summary · Current Situation · Problems · Risks · Opportunities · Recommendations · Priority · Estimated Impact · Next Actions

- منبع اصلی: `ai_context.json` یا `manifest.json`. برای مثال‌های بیشتر `seo_audit.json`.
- گزارش نهایی را در `reports/` ذخیره کن، با نام `report-<موضوع>-<YYYY-MM-DD>.md`.
- «Estimated Impact» را با تخمین محتاطانه و توضیح فرض‌ها بنویس؛ عددی که نمی‌توان از داده درآورد را قطعی نشان نده.

## Sprint

اگر لازم بود پروژه را به Sprint تقسیم کن. برای هر Sprint مشخص کن:

هدف · Taskها · اولویت · Difficulty · Impact · ROI · زمان · خروجی

- یافته‌های `critical` اول، بعد `warning`، بعد `opportunity`.
- Sprint نهایی را در `notes/sprint.md` ذخیره کن.
- تصمیم‌های نهایی من (چه چیزی انجام شود، چه چیزی نه) را در `notes/decisions.md` ثبت کن.
