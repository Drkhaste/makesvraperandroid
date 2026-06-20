# راهنمای نصب و ساخت APK در دبین (Debian)

این راهنما برای سیستم‌عامل دبین و توزیع‌های مبتنی بر آن (مثل اوبونتو) تهیه شده است.

## ۱. نصب پیش‌نیازها

ابتدا سیستم را به‌روزرسانی کرده و ابزارهای مورد نیاز را نصب کنید:

```bash
sudo apt update
sudo apt install -y curl git unzip xz-utils zip libglu1-mesa
```

## ۲. نصب Java (OpenJDK 21)

فلاتر برای اندروید به جاوا نیاز دارد:

```bash
sudo apt install -y openjdk-21-jdk
```

## ۳. نصب Flutter

فلاتر را از مخزن رسمی دریافت کنید:

```bash
git clone https://github.com/flutter/flutter.git -b stable ~/flutter
```

سپس فلاتر را به مسیر سیستم (PATH) اضافه کنید:

```bash
echo 'export PATH="$PATH:$HOME/flutter/bin"' >> ~/.bashrc
source ~/.bashrc
```

اجرای دستور زیر برای اطمینان از نصب:
```bash
flutter doctor
```

## ۴. نصب Android SDK

ساده‌ترین راه نصب Android Studio است، اما برای خط فرمان:
۱. Command Line Tools را از سایت اندروید دریافت کنید.
۲. لایسنس‌ها را تایید کنید:
```bash
flutter doctor --android-licenses
```

## ۵. ساخت پروژه (Build)

وارد پوشه پروژه شوید:

```bash
cd medofast_android/medofast_android
```

دریافت بسته‌ها:
```bash
flutter pub get
```

ساخت فایل APK:
```bash
flutter build apk --release
```

فایل خروجی در مسیر زیر قرار می‌گیرد:
`build/app/outputs/flutter-apk/app-release.apk`
