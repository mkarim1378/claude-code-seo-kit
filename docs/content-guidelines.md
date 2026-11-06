# CONTENT — پیشنهاد و بازنویسی محتوا

برای هر پیشنهاد محتوایی مشخص کن:

هدف محتوا · Intent · Keyword · Parent Topic · Outline · Heading Structure · Entities · FAQ · Internal Links · CTA

## قوانین

- اگر `structure.headings` یا `faq_candidates` برای آن صفحه در `knowledge.json` هست، از آن‌ها به‌عنوان نقطه شروع استفاده کن.
- قبل از پیشنهاد کیورد جدید، `keyword_map.json` را چک کن (cannibalization و coverage)؛ مبادا صفحه‌ای که همین کیورد را دارد با صفحه‌ی جدید رقابت کند.
- هر محتوا به یک Parent Topic / cluster در `site_brain.json` وصل شود.
- لینک داخلی پیشنهادی از `internal_link_graph.json` (`link_opportunities`) بیاید، نه از حدس.
- لحن و استاندارد نوشتن را از نمونه‌های تأییدشده‌ی کاربر در `data/` یا `notes/` بگیر. اگر نمونه‌ای نیست، یکی بخواه.
- CTA باید با هدف اصلی سایت در PROJECT CONTEXT هم‌خوان باشد (لید، ثبت‌نام، فروش).
- آمار، ادعا یا منبع از خودت نساز. اگر چیزی قابل تأیید نیست، علامتش بزن.
