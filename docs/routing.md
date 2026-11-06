# ROUTING — برای هر سؤال اول کجا را بخوان

همه‌ی فایل‌ها در `data/ai-pack/` هستند، مگر اینکه خلافش نوشته شده باشد. توضیح هر فایل: `docs/file-catalog.md`.

**قانون طلایی:** فقط فایل(های) مرتبط با همان سؤال را باز کن. همه‌ی فایل‌ها را از اول تا آخر اسکن نکن. اگر جواب در فایل اول پیدا شد، همان را بده؛ فقط در صورت نیاز یک سطح عمیق‌تر برو. فایل بزرگ را با `jq` یا پایتون بخوان، نه کامل.

| نوع سؤال / هدف | اول بخوان | بعداً فقط اگر لازم شد |
|----------------|------------|------------------------|
| اولویت کار، Sprint، «از کجا شروع کنم؟» | `ai_context.json` (`next_actions` + top_findings) | اگر نبود: `seo_audit.json` + `manifest.json`؛ جزئیات → `knowledge.json` |
| گزارش مدیریتی / KPI / وضعیت کلی | `ai_context.json` یا `manifest.json` | `seo_audit` برای مثال‌های بیشتر |
| crawlability / robots / sitemap / visibility / noindex سراسری | `ai_context.site_profile_summary` یا `technical.site_profile` / `site_profile.json` | — |
| پیشنهاد کیورد / inventory / gap / cannibalization نرم | `keyword_map.json` یا `ai_context.keyword_intelligence` | تأیید coverage روی entity در `knowledge.json` |
| پیشرفت قبل/بعد / چه چیزهایی حل شد؟ | `technical.audit_diff` یا `audit_diff.json` یا `ai_context.audit_diff_summary` | — |
| redirect chain / loop / قوانین ریدایرکت | `technical.redirect_map` یا `redirect_map.json` | findingهای redirect در `seo_audit` |
| hreflang / ترجمه / چندزبانه | `technical.hreflang` یا `hreflang.json` | — |
| پوشش sitemap / URL جاافتاده از sitemap | `technical.sitemap_coverage` یا `sitemap_coverage.json` | — |
| تصویر حجیم / alt کتابخانه رسانه | `technical.media_seo` یا `media_seo.json` | — |
| محتوای تکراری / near-duplicate | `technical.content_duplicates` یا `content_duplicates.json` | findingهای `near_duplicate_content` در audit |
| یک محصول / پست / صفحه مشخص (محتوا، title، meta، H1، FAQ، coverage) | `knowledge.json` (همان entity) | اگر finding مرتبط می‌خواهی → `seo_audit.json` |
| Topic Cluster / IA / pillar / استراتژی محتوایی | `site_brain.json` (clusters غنی) | نمونه موجودیت‌ها در `knowledge.json` |
| منو، ناوبری، مسیر کاربر در سایت | `site_brain.json` (navigation) | breadcrumb محصول در `knowledge.json` |
| orphan / weak hub / لینک مرده / پیشنهاد لینک داخلی | `internal_link_graph.json` | اگر نبود → `site_brain.link_analysis` یا findingهای لینک در `seo_audit.json` |
| cannibalization / duplicate title-meta / noindex / thin category | `seo_audit.json` (+ `keyword_map` برای کیورد) | تأیید روی entity در `knowledge.json` |
| برند / GTIN / نظرات / تصویر / schema essentials محصول | `seo_audit.json` (findingهای commerce) یا مستقیم entity در `knowledge.json` | — |
| عملکرد جستجو (کلیک، ایمپرشن، CTR، جایگاه) | فایل‌های `data/gsc/` | تطبیق با `keyword_map.json` |
| فقط `knowledge.json` موجود است | همان | محدودیت را بگو؛ برای orphan/Sprint/کیورد دقیق بخواه بقیه فایل‌ها را هم بگذارد |

اگر فایل مناسب در `data/` نبود، جواب کلی و بی‌مدرک نساز. بنویس: «برای این سؤال به `[نام فایل]` نیاز دارم.»

اگر برای موضوعی Digest وجود دارد (`notes/digests/`)، اول آن را بخوان. فقط اگر جزئیات یک URL یا entity لازم بود سراغ فایل خام برو.
