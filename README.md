# বাংলা হিসাব খাতা — Android project

বাংলা ইন্টারফেসের অফলাইন-ফার্স্ট দোকান হিসাব অ্যাপের Android Studio প্রজেক্ট।

## বর্তমানে যা আছে
- দৈনিক বিক্রি এন্ট্রি
- ক্রেতার নাম ও ফোন নম্বর
- একাধিক বাকি এন্ট্রি
- আংশিক টাকা আদায়
- নাম/ফোন দিয়ে সার্চ
- ক্রেতাভিত্তিক লেনদেনের ইতিহাস ও বকেয়া হিসাব
- দৈনিক ও মাসিক সারাংশ
- SQLite-এ লোকাল অফলাইন স্টোরেজ

## গুরুত্বপূর্ণ সীমাবদ্ধতা
এই প্রজেক্টে **অনলাইন ব্যাকআপ এখনো চালু করা হয়নি**। স্ক্রিনে সেটআপের ব্যাখ্যা আছে, কিন্তু প্রকৃত cloud sync নয়। অনলাইন ব্যাকআপ চালু করতে Firebase Authentication ও Cloud Firestore যুক্ত করতে হবে, `google-services.json` যোগ করতে হবে, এবং প্রতি ব্যবহারকারীর ডেটা সুরক্ষিত রাখার জন্য Firestore Security Rules সেট করতে হবে। ভুল কনফিগারেশনে ব্যক্তিগত ব্যবসার হিসাব অন্যের কাছে প্রকাশ হতে পারে।

## APK বানানোর ধাপ
1. কম্পিউটারে Android Studio ইনস্টল করুন।
2. Android Studio থেকে `HisabKhataBangla` ফোল্ডার Open করুন।
3. Gradle sync সম্পন্ন হতে দিন (ইন্টারনেট লাগবে)।
4. `Build > Build Bundle(s) / APK(s) > Build APK(s)` নির্বাচন করুন।
5. APK সাধারণত `app/build/outputs/apk/debug/app-debug.apk`-এ তৈরি হবে।

## নোট
- টাকা `Double` দিয়ে সংরক্ষণ করা হয়েছে; বড় পরিসরে ব্যবহার করার আগে অর্থের হিসাব integer poisha/decimal ভিত্তিতে উন্নত করা উচিত।
- উৎপাদনে ব্যবহারের আগে ব্যাকআপ, ডেটা এক্সপোর্ট/ইমপোর্ট, টেস্ট এবং নিরাপত্তা যাচাই করুন।
- এটি একটি প্রাথমিক প্রোটোটাইপ, সম্পূর্ণ যাচাইকৃত বাণিজ্যিক সফটওয়্যার নয়।

## ফোন থেকে ক্লাউডে APK বিল্ড (GitHub Actions)
1. GitHub-এ সাইন আপ/লগইন করে নতুন repository তৈরি করুন।
2. এই ZIP Extract করে ফাইলগুলো repository-তে upload করুন; `.github/workflows/android.yml`-সহ সব ফাইল upload করতে হবে।
3. `Actions` ট্যাবে যান এবং `Build Android APK` workflow নির্বাচন করে `Run workflow` চাপুন।
4. বিল্ড সফল হলে run-এর নিচে `Artifacts` থেকে `HisabKhataBangla-debug-apk` ডাউনলোড করুন।
5. ZIP artifact extract করে `app-debug.apk` ইনস্টল করুন। Android চাইলে Settings থেকে ওই ফাইল/ব্রাউজারের জন্য install permission দিন।

সতর্কতা: প্রথমবারে GitHub repository-তে সব ফাইল ঠিকমতো upload করতে হবে। এটি debug APK; Play Store release signing নয়। এই প্রকল্পের অনলাইন ব্যাকআপ ফিচার এখনো বাস্তবায়িত নয়।
