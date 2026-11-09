تحرير إجهادات السكة — حزمة PWA

الملفات:
  index.html            التطبيق
  manifest.json         بيانات التثبيت
  sw.js                 العمل بدون إنترنت
  icon-*.png, apple-touch-icon.png   الأيقونات

التثبيت على الجوال (PWA):
  1) ارفع كل الملفات إلى استضافة HTTPS (GitHub Pages / Netlify / Cloudflare Pages).
  2) افتح الرابط من الجوال.
     أندرويد (Chrome): القائمة ← تثبيت التطبيق.
     آيفون (Safari): مشاركة ← إضافة إلى الشاشة الرئيسية.
  3) بعد أول فتح يعمل التطبيق بدون إنترنت.

ملاحظة: لا يعمل service worker عند فتح الملف مباشرة من الجهاز (file://)، يلزم HTTPS أو localhost.
للتجربة محليًا:  python3 -m http.server 8000  ثم افتح http://localhost:8000

عند تعديل أي ملف، غيّر رقم الإصدار في sw.js (rail-stress-v1 ← v2) ليصل التحديث للمستخدمين.

APK عبر Capacitor:
  mkdir rail-app && cd rail-app && npm init -y
  npm i @capacitor/core @capacitor/cli @capacitor/android
  npx cap init "إجهادات السكة" com.example.railstress --web-dir=www
  mkdir www && cp ../index.html ../manifest.json ../*.png www/
  npx cap add android && npx cap sync && npx cap open android
