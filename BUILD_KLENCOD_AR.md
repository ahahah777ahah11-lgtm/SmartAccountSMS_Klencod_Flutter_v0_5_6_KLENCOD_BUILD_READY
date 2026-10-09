# بناء تطبيق المحاسب الذكي في Klencod IDE

## إعداد المشروع
1. فك ضغط ملف المشروع كاملاً، ثم افتح المجلد الذي يحتوي على `pubspec.yaml` في Klencod IDE.
2. تأكد من أن بيئة البناء تستخدم Flutter حديثاً وقناة stable، وJava 17.
3. شغّل `flutter pub get` لتنزيل الحزم وحل الاعتماديات.
4. شغّل `flutter analyze` لمراجعة أخطاء Dart.
5. شغّل `flutter build apk --release` لإنشاء APK.

## البناء التلقائي عبر GitHub Actions
أُضيف الملف `.github/workflows/android-apk.yml`. بعد رفع المشروع إلى مستودع GitHub، افتح تبويب **Actions** وشغّل **Build Android APK** عبر **Run workflow**. عند نجاح المهمة، نزّل `smart-account-sms-release-apk` من قسم Artifacts.

## إعدادات البناء المضمنة
- Gradle Wrapper: 8.14.3
- Android Gradle Plugin: 8.11.1
- Kotlin Gradle Plugin: 2.2.20
- Java target: 17
- إصدار التطبيق: 0.5.5 (versionCode 10)
- الحزم المباشرة: `webview_flutter` و`url_launcher`، وتُحل إصداراتها بواسطة `flutter pub get` حسب قيود `pubspec.yaml`.

ملاحظة: إضافة إعدادات البناء الآلي لا تعني أن APK تم بناؤه واختباره مسبقاً. يجب تشغيل خطوات البناء في بيئة Flutter فعلية؛ إذا فشلت مهمة CI فاعتمد سجل الخطأ لتحديد أي مشكلة متبقية.
