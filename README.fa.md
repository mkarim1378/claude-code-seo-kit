[English](README.md) · **فارسی**

# claude-code-seo-kit — پروژه‌ی سئو با Claude Code

## راه‌اندازی

1. داخل همین پوشه `claude` را اجرا کن.
2. `/new-project` را بزن تا بخش **PROJECT CONTEXT** در `CLAUDE.md` پر شود.
3. خروجی SEO AI Export را در `data/ai-pack/` بگذار. خروجی Search Console را (اگر داری) در `data/gsc/`.
4. اولین پیام پیشنهادی: «از کجا شروع کنم؟»

## استفاده به‌عنوان Starter (قالب پروژه)

نسخه‌ی starter در `starter.json` و تغییرها در `CHANGELOG.md` ثبت می‌شوند.

1. این پوشه را به‌عنوان یک ریپوی **private** در گیت‌هاب بگذار و در Settings گزینه‌ی **Template repository** را فعال کن. هیچ داده‌ی واقعی پروژه‌ای را در starter commit نکن.
2. برای هر پروژه‌ی جدید:
   ```
   gh repo create <نام-پروژه> --template <username>/<نام-starter> --private --clone
   ```
   یا در وب: **Use this template ← Create a new repository**.
3. داخل پوشه‌ی پروژه‌ی جدید `claude` را اجرا کن و `/new-project` بزن تا PROJECT CONTEXT را از تو بپرسد و پر کند.
4. هر پروژه یک پوشه و یک ریپوی جدا دارد. `claude` را همیشه داخل پوشه‌ی خود پروژه اجرا کن، نه پوشه‌ی والد، تا کانتکست و حافظه‌ی پروژه‌ها قاطی نشوند.
5. بهبودهای starter خودکار به پروژه‌های قبلی نمی‌رسند؛ با `/sync-starter` آپدیت می‌شوند (بخش پایین).

## آپدیت پروژه‌های قبلی از روی starter

داخل پوشه‌ی پروژه `claude` را اجرا کن و `/sync-starter` بزن. این دستور:

- starter را به‌عنوان remote با نام `template` اضافه و fetch می‌کند و `CHANGELOG.md` را از نسخه‌ی پروژه تا آخرین نسخه خلاصه می‌کند.
- فقط مسیرهای `sync_paths` در `starter.json` را مقایسه می‌کند: `docs/`، `.claude/commands/`، `.claude/settings.json` و `.gitignore`.
- **هرگز** `CLAUDE.md`، `notes/`، `data/` و `reports/` را بازنویسی نمی‌کند (مگر مهاجرت یک‌باره‌ی 1.0 به 1.1، با نشان دادن نتیجه و تأیید تو).
- اگر هم starter و هم خودت یک فایل را تغییر داده باشید، ادغام سه‌طرفه می‌کند و در صورت تعارض می‌پرسد.
- فایل به فایل تأیید می‌گیرد، یک کامیت `chore: sync starter ...` می‌زند و push نمی‌کند.

**نکته‌ی یک‌باره برای پروژه‌های قدیمی:** پروژه‌هایی که قبل از 1.1 ساخته شده‌اند `/sync-starter` را ندارند. یک بار فایل `.claude/commands/sync-starter.md` را از ریپوی starter در همان پوشه کپی کن، بعد دستور کار می‌کند.

**برای نگه‌داشتن starter قابل‌آپدیت:** بعد از هر تغییر مهم، نسخه را در `starter.json` و `CHANGELOG.md` بالا ببر و روی همان کامیت تگ بزن (مثلاً `git tag vX.Y.Z && git push --tags`). با تگ، `/sync-starter` می‌تواند تغییر starter را از تغییر محلی تفکیک کند.

## ساختار

| مسیر | کاربرد |
|------|--------|
| `CLAUDE.md` | فقط مخصوص پروژه: PROJECT CONTEXT و حافظه. قوانین عمومی را import می‌کند و هیچ‌وقت sync نمی‌شود |
| `docs/core-rules.md` | قوانین عمومی (نقش، قوانین طلایی، KPI، قوانین حافظه). از `CLAUDE.md` import می‌شود، یعنی همیشه لود است |
| `docs/` | بقیه‌ی مرجع‌ها، فقط وقتی موضوعشان پیش بیاید خوانده می‌شوند |
| `starter.json` · `CHANGELOG.md` | نسخه‌ی starter و فهرست مسیرهای قابل sync |
| `notes/MEMORY.md` | حافظه‌ی کوتاه پروژه (سقف ۸۰ خط)، خودکار لود می‌شود |
| `notes/decisions.md` · `sprint.md` · `digests/` · `archive/` | جزئیات تصمیم‌ها، Sprint، خلاصه‌ی فایل‌های حجیم، آرشیو |
| `data/` | exportها (داخل git هستند، پس ریپو باید private باشد): `ai-pack/` افزونه، `gsc/` Search Console، `competitors/` رقبا، `archive/` قدیمی‌ها |
| `reports/` | گزارش‌های نهایی |
| `.claude/settings.json` | دسترسی‌های مشترک پروژه: خواندن `.env`، کلیدها و فایل‌های SQL ممنوع است (تنظیمات شخصی در `settings.local.json`، خارج از git) |
| `.claude/commands/` | دستورهای `/new-project`، `/competitors`، `/sync-starter`، `/wrapup`، `/memory-cleanup`، `/digest` |

## کار روی چند سیستم

همه‌ی چیزهای پروژه (`data/`، `notes/`، `reports/`، `CLAUDE.md`) داخل git است، پس روی سیستم دیگر با `git clone` یا `git pull` ادامه می‌دهی. `.gitignore` فقط این‌ها را کنار می‌گذارد: رمز و کلید (`.env`، `*.key`، `*.pem`)، بکاپ دیتابیس (`*.sql*`) و فایل‌های مخصوص هر سیستم (`.claude/settings.local.json`، `CLAUDE.local.md`، `.omc/`).

- **ریپوی هر پروژه را همیشه private نگه دار.** exportها محتوای سایت و داده‌ی رقبا را دارند. `/new-project` قبل از دست‌زدن به `data/` وضعیت ریپو را چک می‌کند.
- **قبل از شروع `pull`، بعد از پایان `push`** (`/wrapup` یادآوری می‌کند).
- **حجم فایل:** GitHub فایل بالای ۱۰۰ مگابایت را رد می‌کند. برای export بزرگ‌تر از [Git LFS](https://git-lfs.com) استفاده کن یا فایل را تکه کن.
- **`data/archive/` با گذشت زمان بزرگ می‌شود.** exportهای قدیمی در تاریخچه‌ی git هم می‌مانند؛ اگر ریپو سنگین شد، این پوشه را گاهی پاک‌سازی کن.
- تأییدهای دسترسی شخصی (`settings.local.json`) بین سیستم‌ها منتقل نمی‌شوند؛ روی سیستم جدید دوباره تأیید کن.

## روال کار

- **هر export جدید:** فایل قبلی را به `data/archive/<تاریخ>/` ببر، فایل جدید را در `data/ai-pack/` بگذار، بعد `/memory-cleanup` بزن تا خط‌های وابسته به export قدیمی دوباره بررسی شوند.
- **فایل خیلی حجیم:** `/digest data/ai-pack/seo_audit.json`
- **تحلیل رقبا:** exportهای رقبا را در `data/competitors/` بگذار و `/competitors` بزن.
- **آخر هر جلسه:** `/wrapup`
- **هر چند وقت:** `/memory-cleanup` و بعد `git diff notes/MEMORY.md` برای بازبینی سریع.

## نکته‌ها

- دسترسی‌های Claude Code را فقط به همین پوشه محدود کن.
- رمز، کلید API و بکاپ دیتابیس را در این پوشه نگذار.
- قانون به‌روزرسانی حافظه (در `docs/core-rules.md`) راهنماست، نه اجبار. اگر کلاد فراموش کرد، `/wrapup` را خودت بزن.
- هوک (hook) خودکار برای پایان جلسه عمداً اضافه نشده: هوک Stop بعد از هر پاسخ فعال می‌شود، نه فقط آخر جلسه، و آزاردهنده است. اگر خواستی، جداگانه تنظیمش می‌کنیم.
