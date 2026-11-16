# AI Cartoon Shorts — نسخة بلا API

هاد المشروع كيصايب فيديو كرتوني عمودي بسيط (10 ثواني، 720×1280، 24fps) باستعمال Python/Pillow وFFmpeg. ما كيحتاج حتى API key وما فيهش مصاريف توليد فيديو. الشخصيات الأصلية: Bananito الموزة وFrezita الفريزة.

**مهم:** هادي Animation مرسومة ومتحركة برمجياً، ماشي فيديو مولّد بنموذج AI بحال Veo أو Kling. السيناريوهات الحالية Templates عشوائية، ماشي كتابة AI. هاد هو التنازل اللازم باش نخليو التوليد مجاني بالكامل على GitHub Actions القياسي.

## شنو كيدير؟

- كينتج فيديو MP4 عمودي فكل تشغيل.
- كيختار واحد من قصص قصيرة جاهزة بالدارجة.
- كيشغّل 3 مرات فالنهار: 10:00 و15:00 و20:00 بتوقيت `Africa/Casablanca`.
- كيحفظ الفيديو وملف JSON كـ GitHub Actions Artifact لمدة 7 أيام.
- النشر العمومي مطفأ افتراضياً.

## التركيب

1. أنشئ Repository جديد فـ https://github.com/new
2. فك ضغط `ai-cartoon-shorts-no-api.zip` ورفع محتويات المجلد كاملة إلى جذر المستودع، مع الاحتفاظ بمجلد `.github/workflows`.
3. افتح تبويب **Actions** وفعّل workflows إذا طلب منك GitHub ذلك.
4. شغّل `Generate and publish AI cartoon shorts` يدوياً من **Actions → Run workflow**.
5. من بعد ما يكمل، افتح نتيجة التشغيل وحمّل Artifact باش تلقى MP4 وJSON.

ما محتاج حتى Secret باش تولّد الفيديو.

## كيفاش نبدّل القصص؟

عدّل `app/story.py` وزيد أو بدّل العناصر داخل `EPISODES`. خلي كل قصة فيها `title`, `caption`, `visual_prompt`, و`hashtags`.

## النشر على المنصات

التوليد والنشر حاجتين مختلفتين. النسخة الحالية كتولّد وتحفظ الفيديو فقط. النشر إلى YouTube أو Instagram يحتاج OAuth tokens وصلاحيات API؛ وTikTok يحتاج تطبيقاً معتمداً وتجربة نشر متوافقة فيها معاينة وموافقة صاحب الحساب. ما تحطش أي مفاتيح في الكود.

خلي `PUBLISH_ENABLED=false` حتى تجهز صلاحيات كل منصة وتختبرها. النشر التلقائي ليس مفعلاً في الوضع المجاني بلا API.

## علاش ما كنشغلوش نموذج AI فيديو داخل GitHub Actions؟

الـ GitHub-hosted runner القياسي عندو موارد CPU/RAM عادية وما فيهش GPU مخصص لتوليد الفيديو. النماذج المفتوحة كتحتاج GPU قوي ومساحة كبيرة. مثلاً LTX Desktop يذكر NVIDIA GPU بذاكرة 16GB VRAM على Windows/Linux، وقرابة 160GB مساحة تخزين؛ لذلك ماشي مناسب للـ runner المجاني العادي.

إذا عندك جهاز مناسب وبغيتي توليد AI حقيقي محلياً، شوف LTX Desktop: https://github.com/Lightricks/ltx-desktop

## الملفات

- `.github/workflows/daily-shorts.yml`: الجدولة اليومية.
- `app/story.py`: مكتبة القصص المجانية.
- `app/video.py`: الرسم والتحريك وإخراج MP4 بواسطة FFmpeg.
- `app/main.py`: تشغيل العملية وحفظ البيانات.
- `requirements.txt`: Pillow واحتياجات النشر الاختيارية.

## المصادر الرسمية

- GitHub-hosted runners والموارد: https://docs.github.com/en/actions/reference/runners/github-hosted-runners
- GitHub Actions billing: https://docs.github.com/en/billing/concepts/product-billing/github-actions
- LTX Desktop ومتطلبات الجهاز: https://github.com/Lightricks/ltx-desktop
