# Talk to dx mouh — ملف جاهز للنشر (شرح بالعربية الجزائرية)

هذي نسخة بسيطة وجاهزة للموقع تاعك "Talk to dx mouh".
فيها:
- واجهة أمامية static (index.html) بلون فخم.
- صفحة إدارة بسيطة (admin.html) باش تشوف الرسائل لو فعلت backend.
- backend صغير (server.js) اختياري لو تحب تخزن الرسائل مع موافقة المستخدم.

## تحميل ورفع المشروع
1. نزّل هذي الّآرشيف (zip) و فكّ الضغط:
   - في الجهاز: `unzip talk-to-dx-mouh.zip -d talk-to-dx-mouh`
2. افتح حساب GitHub إذا ماعندكش: https://github.com
3. أنشئ Repository جديد: `talk-to-dx-mouh` (اجعله Public أو Private)
4. ادخل للمجلد و حمّل الملفات بالــ Git:
   ```bash
   cd talk-to-dx-mouh
   git init
   git add .
   git commit -m "initial commit - Talk to dx mouh"
   git branch -M main
   git remote add origin https://github.com/<your-username>/talk-to-dx-mouh.git
   git push -u origin main
   ```

## نشر الواجهة بسرعة (الخيار الأسهل: GitHub Pages)
1. بعد ما تدفع الكود للـ GitHub repo:
   - افتح صفحة repository على GitHub -> Settings -> Pages
   - Source: اختار branch `main` و folder `/(root)` -> Save
   - بعد شوية (دقيقة-دقيقتين) الموقع يظهر في https://<your-username>.github.io/talk-to-dx-mouh

**بديل**: تقدر تنشر عبر Vercel أو Netlify لو تحب ميزات أكثر.

## ربط نموذج AI (Hugging Face Space)
- افتح صفحة Space تاعك في Hugging Face (أو اختار Space جاهز).
- اضغط Share -> Embed -> انسخ رابط الـ iframe/embed.
- افتح `index.html` وغيّر قيمة `HF_IFRAME_EMBED` في أعلى السكريبت و ضع الرابط.
- احفظ وادفع التغييرات (git commit + push) و GitHub Pages يعطيك النسخة الجديدة.

## لو ترغب بتجميع الرسائل (قانونياً)
- في `index.html` راهي توجد checkbox "نوافق أن نسجل الرسالة..." لازم المستخدم يوافق.
- لو حبّيت تخزن الرسائل في سيرفر:
  1. في ملف `server.js` موجود API بسيط POST /api/log و GET /admin/messages.
  2. أنشر السيرفر على Render.com أو Railway أو أي خدمة تدعم Node.
  3. قبل النشر عيّن متغير البيئة `ADMIN_KEY` إلى كلمة سر قوية.
  4. بعد النشر: حط رابط الـ BACKEND_URL في `index.html` (المتغير BACKEND_URL).
  5. افتح `admin.html` و دخّل رابط backend و مفتاح المدير باش تشوف الرسائل.
- **ملاحظة مهمة:** لازم تظهر للمستخدمين إشعار الخصوصية وتطلب موافقتهم قبل الاحتفاظ بالرسائل. ما تستعملش طريقة تخفية لمراقبة الناس بدون علمهم — هذا ممنوع وقانونيًا خطر.

## نشر backend على Render (مثال سريع)
1. افتح https://render.com و أنشئ حساب مجاني.
2. New -> Web Service -> Connect to GitHub repo -> اختر `talk-to-dx-mouh`
3. Branch: `main`
4. Build Command: leave empty
5. Start Command: `npm start`
6. Add Environment Variable `ADMIN_KEY` = `your-secret-key`
7. Deploy — و بعد ما يخلص، خذ رابط الخدمة و حطه في `index.html` في `BACKEND_URL`.

## نص سياسة خصوصية قصيرة (حطها في صفحة خاصة أو footer)
> نحب نصرّح بوضوح: الرسائل اللي يكتبها المستخدمون يمكن تخزينها **بموافقتهم فقط** وبشكل **مجهول** (بدون أسماء أو عناوين IP) لتحسين الخدمة. المستخدمين يقدروا يرفضوا التخزين ويستعملوا الموقع بدون تسجيل. ما نستعملش أو نشارك البيانات مع أطراف ثالثة بدون إذن صريح.

---

إذا تحب، نقدر نعمل معا:
- نرفع المشروع مباشرة على GitHub وننشره نيابة عنك (ما نبغي تاكّد من صلاحيات الوصول تاعك).
- نساعدك تنشر backend على Render خطوة بخطوة.
- نعدّلك تصميم الواجهة ولا نضيف موديل جاهز وندمجه.

قول لي واش تبغي دير دابا: **نمدلك الملف مضغوط تحمّلو؟ ولا نرفع كلشي على GitHub وندير نشر على Vercel؟**
