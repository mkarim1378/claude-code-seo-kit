# FILE CATALOG — هر فایل چیست؟

کاربر معمولاً پوشه‌ی **`ai-pack/`** (حداکثر ۸ فایل) از SEO AI Export را در `data/ai-pack/` می‌گذارد. همان نام فایل‌ها ممکن است از `output/json/` هم بیایند. اگر `technical.json` موجود باشد، داده‌های technical جدا (`site_profile` و …) داخل کلیدهای همان فایل‌اند، کامل و نه خلاصه.

اگر فایلی در `data/ai-pack/` نیست، صریح بگو و همان را بخواه. فرض نکن همه‌ی فایل‌ها همیشه وجود دارند.

خروجی Search Console (اگر باشد) در `data/gsc/` است و در این جدول نیست.

| فایل | محتویات | رجوع کن وقتی… |
|------|---------|----------------|
| **`ai_context.json`** | بسته شروع AI: خلاصه site_profile، counts، top findings با `impact_score`، `next_actions`، keyword summary، url_index غنی | **اول این را بخوان** برای overview و اولویت‌ها |
| **`manifest.json`** | خلاصه اجرا / ایندکس پک، تعدادها، `how_to_use`، نقشه فایل‌ها | overview خیلی سریع اگر ai_context نبود |
| **`technical.json`** | ادغام کامل: `site_profile` + `redirect_map` + `hreflang` + `sitemap_coverage` + `media_seo` + `content_duplicates` + `audit_diff` | هر سؤال technical / پیشرفت / تصویر / duplicate / hreflang |
| **`site_profile.json`** | visibility، permalink، robots.txt، sitemaps (+reachable)، صفحات ویژه، پلاگین سئو، `seo_plugin_globals` | crawlability — یا `technical.site_profile` |
| **`keyword_map.json`** | inventory کیوردها، url_targets + coverage، cannibalization، gaps، suggestions، اختیاری GSC | کیورد ریسرچ on-site، پیشنهاد primary/secondary |
| **`audit_diff.json`** | added/resolved/severity_changed نسبت به seo_audit قبلی | پیشرفت قبل/بعد — یا `technical.audit_diff` |
| **`redirect_map.json`** | قوانین redirect + chains/loops | مهاجرت URL — یا `technical.redirect_map` |
| **`hreflang.json`** | زبان‌ها و translation pairs (Polylang/WPML) | سئوی چندزبانه — یا `technical.hreflang` |
| **`sitemap_coverage.json`** | URLهای sitemap در برابر export | شکاف ایندکس — یا `technical.sitemap_coverage` |
| **`media_seo.json`** | alt خالی، oversized، ابعاد بزرگ | تصویر — یا `technical.media_seo` |
| **`content_duplicates.json`** | fingerprint محتوای نزدیک‌به‌تکراری + عنوان تکراری | duplicate — یا `technical.content_duplicates` |
| **`seo_audit.json`** | همه findings با severity و `ai_action` (heuristic؛ امتیاز گوگل نیست) | لیست کامل مشکلات وقتی از سقف ai_context رد شدی |
| **`knowledge.json`** | موجودیت‌های کامل با content/structure/seo (+ `seo.keyword_coverage`) | جزئیات یک URL، بازنویسی، FAQ، نظرات |
| **`site_brain.json`** | آمار، clusters غنی (pillar/keywords)، graph، navigation، link_analysis (+ opportunities)، entity_index | استراتژی، IA، ناوبری |
| **`internal_link_graph.json`** | orphan / hub / unresolved / duplicate anchors / link_opportunities / category nodes | لینک‌سازی داخلی |

## مدل داخل موجودیت‌ها (عمدتاً در `knowledge.json`)

- متریک متن فارسی: `word_count` / `sentence_count` / `char_count`، `html_length`
- `structure`: headings، links، faq_candidates، `images_count` / `images_missing_alt`
- `seo`: title/description/canonical/focus_keyword، robots، `schema_types` (ادعای پلاگین)، **`schema_detected`** (JSON-LD در HTML)، **`schema_claimed_only`**، `keyword_coverage`، `is_cornerstone`، `resolved_*`، lengths، OG/Twitter
- `structure.content_render`: حالت رندر محتوا (`blocks` / `the_content` / raw) — Elementor meta رندر نمی‌شود
- نویسنده پست: `published_posts` (سیگنال EEAT سبک)
- محصول: `identifiers`، `variations`، `reviews`، `breadcrumb`، `total_sales`

## نکته درباره‌ی فایل‌های حجیم

`knowledge.json`، `site_brain.json`، `internal_link_graph.json` و `seo_audit.json` معمولاً سنگین‌اند. کامل نخوان؛ با `jq` یا پایتون فقط کلید یا entity مورد نیاز را بیرون بکش. اگر لازم بود، `/digest` برای ساخت خلاصه‌ی فشرده استفاده می‌شود.
