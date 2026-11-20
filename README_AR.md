# Infinity MEN2 – تطبيق Android

هذا المشروع مخصص لبناء تطبيق Android تلقائيًا من خلال GitHub Actions. لا تحتاج إلى تثبيت Node.js أو Android Studio على جهازك، ولا تحتاج إلى فتح Terminal.

## الملفات

- `index.html` و`app.js`: واجهة البرنامج ووظائفه.
- `pwa.js` و`sw.js`: الكاميرا/التذكيرات والنسخ الاحتياطي ودعم الويب.
- `native-features.js`: ربط كاميرا Android وإشعارات الهاتف الأصلية.
- `package.json`: تعريف المكتبات وأوامر البناء.
- `capacitor.config.json`: إعدادات تطبيق Android.
- `assets/` و`resources/`: شعار Infinity MEN2 والأيقونات وصورة البداية.
- `.github/workflows/android.yml`: الملف الذي يشغّل بناء APK تلقائيًا عند كل رفع ملفات إلى GitHub.

## خطوات الاستخدام – بدون Terminal

1. فك ضغط ملف ZIP على الكمبيوتر. لا ترفع ملف ZIP نفسه إلى GitHub؛ ارفع محتوياته.
2. أنشئ مستودعًا جديدًا على GitHub باسم `Infinity-MEN2-Law-Office`.
3. من صفحة المستودع اضغط **Add file → Upload files**، ثم ارفع جميع ملفات المشروع إلى جذر المستودع.
4. تأكد من رفع المجلد المخفي `.github` وبداخله `workflows/android.yml`. في Windows فعّل **View → Show → Hidden items** قبل تحديد الملفات.
5. اضغط **Commit changes**. سيبدأ GitHub Actions تلقائيًا ببناء التطبيق بعد حفظ الملفات.
6. افتح تبويب **Actions**، ثم افتح أحدث تشغيل باسم **Build Infinity MEN2 Android APK**.
7. انتظر حتى تظهر علامة النجاح الخضراء. في أسفل صفحة التشغيل ستجد **Artifacts**.
8. نزّل `Infinity-MEN2-Law-Office-Android-APK.zip`، وفك ضغطه؛ ستجد داخله `app-debug.apk`.

## إذا لم يظهر Actions

تأكد أن هذا الملف موجود بالمسار نفسه داخل المستودع:

`.github/workflows/android.yml`

إذا لم تستطع رفع المجلد المخفي من جهازك، أنشئه يدويًا من GitHub: **Add file → Create new file**، واكتب اسم الملف أعلاه، ثم انسخ محتوى ملف `android.yml` الموجود داخل ZIP والصقه، واضغط **Commit changes**.

## بعد ذلك

كل مرة ترفع فيها تعديلًا جديدًا وتضغط **Commit changes**، سيبدأ بناء APK جديد تلقائيًا. يمكنك أيضًا إعادة البناء يدويًا من **Actions → Build Infinity MEN2 Android APK → Run workflow**.

## ملاحظات مهمة

- الناتج هو APK تجريبي موقّع بمفتاح Debug الخاص ببيئة GitHub، ومناسب للتثبيت والاختبار على Android. نشر إصدار تجاري ثابت يحتاج إعداد توقيع Release بمفتاح خاص محفوظ في GitHub Secrets.
- تذكيرات الجلسات المحلية والكاميرا الأصلية تعتمد على أذونات الهاتف.
- إشعارات FCM الخارجية تحتاج مشروع Firebase وملف `google-services.json` وخادم إرسال ومفاتيح آمنة؛ لا تُفعّل بمجرد بناء APK وحده.
- تخزين بيانات المكتب في هذا المصدر محلي على الجهاز، ولا توجد مزامنة تلقائية بين عدة هواتف. لا تستخدم بيانات حقيقية حساسة قبل استكمال الخادم الآمن والمزامنة والحماية.
