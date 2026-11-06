# SEO و Technical SEO

## تحلیل سئو

در تحلیل سئو این موارد را بررسی کن:

Search Intent · Keyword Mapping · Topic Cluster · Semantic SEO · Entity SEO · Internal Linking · Information Architecture · Crawlability · Indexability · Core Web Vitals · Schema · Content Quality · Thin Content · Duplicate Content · Cannibalization · EEAT

همچنین از سیگنال‌های export استفاده کن: orphan URL، weak hub، dead internal link، duplicate title/meta، focus keyword cannibalization، heading hierarchy، thin category، stale content، unexpected noindex، کمبود brand/GTIN/reviews روی محصولات کلیدی.

## Technical SEO

همیشه وضعیت این موارد را نیز بررسی کن:

Core Web Vitals · Page Speed · Index · Canonical · Redirect · 404 · Robots · Sitemap · Structured Data · JavaScript SEO · Image Optimization · Mobile Friendly

- برای موارد قابل استخراج از export (canonical، robots، تصاویر، alt، لینک مرده) به داده استناد کن، با نام فایل و `finding.id`.
- برای موارد غیرموجود در export (Core Web Vitals، Page Speed، JavaScript SEO، وضعیت واقعی ایندکس در گوگل) صریح بگو که به ابزار جداگانه نیاز دارد (PageSpeed Insights، Search Console، crawler). حدس نزن.
- `schema_types` فقط ادعای پلاگین است. وجود واقعی schema را با `schema_detected` بسنج و `schema_claimed_only` را به‌عنوان مشکل علامت بزن.
- محتوای ساخته‌شده با Elementor ممکن است در export رندر نشده باشد (`structure.content_render`). قبل از نتیجه‌گیری درباره‌ی thin content، حالت رندر را چک کن.

## ترتیب اولویت یافته‌ها

`critical` اول، بعد `warning`، بعد `opportunity`.
