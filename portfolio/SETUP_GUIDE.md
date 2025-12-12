# 🚀 Complete Setup Guide for Beginners

هذا الدليل سيساعدك على تشغيل المشروع بالكامل خطوة بخطوة.

---

## 📌 Overview - ما الذي ستحتاجه؟

لتشغيل المشروع بكل المميزات، تحتاج إلى إنشاء حسابات مجانية في:

| الخدمة | الاستخدام | الرابط |
|--------|-----------|--------|
| **MongoDB Atlas** | قاعدة البيانات | https://cloud.mongodb.com |
| **Clerk** | تسجيل الدخول | https://clerk.com |
| **Stripe** | الدفع | https://stripe.com |
| **OpenAI** | الذكاء الاصطناعي | https://platform.openai.com |

---

## الخطوة 1: تثبيت Node.js 🟢

إذا لم يكن Node.js مثبتاً على جهازك:

1. اذهب إلى: https://nodejs.org
2. حمّل النسخة **LTS** (الموصى بها)
3. ثبتها على جهازك
4. للتأكد من التثبيت، افتح PowerShell واكتب:
   ```
   node --version
   ```
   يجب أن ترى رقم نسخة مثل `v20.x.x`

---

## الخطوة 2: فتح المشروع في Terminal 📂

1. افتح **PowerShell** أو **Command Prompt**
2. اذهب إلى مجلد المشروع بكتابة:
   ```powershell
   cd "c:\Users\محمد سلطان\Desktop\مجلد جديد\css\csss\special\portfolio"
   ```

---

## الخطوة 3: تثبيت الحزم 📦

في نفس النافذة، اكتب:
```powershell
npm install
```

**انتظر حتى ينتهي** (قد يستغرق 5-10 دقائق حسب سرعة الإنترنت)

---

## الخطوة 4: إنشاء ملف الإعدادات 📝

1. في مجلد المشروع، ستجد ملف اسمه `.env.example`
2. انسخه وسمّه `.env.local`
3. يمكنك فعل ذلك بالأمر:
   ```powershell
   copy .env.example .env.local
   ```

---

## الخطوة 5: إعداد MongoDB Atlas (قاعدة البيانات) 🗄️

### 5.1 إنشاء الحساب:
1. اذهب إلى: https://cloud.mongodb.com
2. اضغط **Try Free** و أنشئ حساباً مجانياً

### 5.2 إنشاء Cluster:
1. بعد تسجيل الدخول، اضغط **Build a Database**
2. اختر **M0 FREE** (المجاني)
3. اختر أقرب منطقة لك
4. اضغط **Create**

### 5.3 إنشاء مستخدم قاعدة البيانات:
1. ستظهر شاشة **Security Quickstart**
2. أدخل اسم مستخدم (مثلاً: `admin`)
3. أدخل كلمة مرور قوية (مثلاً: `MyPassword123`)
4. **احفظها في مكان آمن!**
5. اضغط **Create User**

### 5.4 السماح بالوصول:
1. في نفس الشاشة، اختر **My Local Environment**
2. اضغط **Add My Current IP Address**
3. أو اكتب `0.0.0.0/0` للسماح من أي مكان
4. اضغط **Finish and Close**

### 5.5 الحصول على Connection String:
1. اضغط **Connect** بجانب Cluster الخاص بك
2. اختر **Drivers**
3. انسخ الرابط الذي يبدو هكذا:
   ```
   mongodb+srv://admin:<password>@cluster0.xxxxx.mongodb.net/?retryWrites=true&w=majority
   ```
4. **استبدل `<password>` بكلمة المرور اللي اخترتها**
5. **أضف اسم قاعدة البيانات** قبل `?`:
   ```
   mongodb+srv://admin:MyPassword123@cluster0.xxxxx.mongodb.net/ai-portfolio?retryWrites=true&w=majority
   ```

### 5.6 أضفها للإعدادات:
افتح ملف `.env.local` وأضف:
```
MONGODB_URI="mongodb+srv://admin:MyPassword123@cluster0.xxxxx.mongodb.net/ai-portfolio?retryWrites=true&w=majority"
```

---

## الخطوة 6: إعداد Clerk (تسجيل الدخول) 🔐

### 6.1 إنشاء الحساب:
1. اذهب إلى: https://clerk.com
2. اضغط **Get started free**
3. أنشئ حساباً

### 6.2 إنشاء Application:
1. بعد تسجيل الدخول، اضغط **Add application**
2. اكتب اسم (مثلاً: `AI Portfolio Builder`)
3. اختر طرق تسجيل الدخول (Email, Google, إلخ)
4. اضغط **Create application**

### 6.3 الحصول على المفاتيح:
1. ستظهر لك صفحة فيها **API Keys**
2. انسخ:
   - `NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY` - يبدأ بـ `pk_test_`
   - `CLERK_SECRET_KEY` - يبدأ بـ `sk_test_`

### 6.4 أضفها للإعدادات:
في ملف `.env.local`:
```
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY="pk_test_xxxxxxxxxxxxxxxx"
CLERK_SECRET_KEY="sk_test_xxxxxxxxxxxxxxxx"
```

---

## الخطوة 7: إعداد Stripe (الدفع) 💳

### 7.1 إنشاء الحساب:
1. اذهب إلى: https://stripe.com
2. اضغط **Start now**
3. أنشئ حساباً

### 7.2 الحصول على المفاتيح:
1. بعد تسجيل الدخول، ستكون في **Test mode** (الوضع التجريبي)
2. اضغط **Developers** في القائمة العلوية
3. اضغط **API keys**
4. انسخ:
   - `Publishable key` - يبدأ بـ `pk_test_`
   - `Secret key` - يبدأ بـ `sk_test_` (اضغط **Reveal** لرؤيته)

### 7.3 أضفها للإعدادات:
في ملف `.env.local`:
```
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY="pk_test_xxxxxxxxxxxxxxxx"
STRIPE_SECRET_KEY="sk_test_xxxxxxxxxxxxxxxx"
```

---

## الخطوة 8: إعداد OpenAI (الذكاء الاصطناعي) 🤖

### 8.1 إنشاء الحساب:
1. اذهب إلى: https://platform.openai.com
2. أنشئ حساباً أو سجل دخول

### 8.2 الحصول على API Key:
1. اذهب إلى: https://platform.openai.com/api-keys
2. اضغط **Create new secret key**
3. اكتب اسم (مثلاً: `portfolio-app`)
4. اضغط **Create secret key**
5. **انسخ المفتاح فوراً** (لن تراه مرة أخرى!)
   - يبدأ بـ `sk-`

### 8.3 أضفه للإعدادات:
في ملف `.env.local`:
```
OPENAI_API_KEY="sk-xxxxxxxxxxxxxxxxxxxxxxxx"
```

**ملاحظة مهمة:** OpenAI ليس مجانياً تماماً، ستحتاج إلى إضافة بطاقة دفع وشحن رصيد ($5-10 كافي للبداية)

---

## الخطوة 9: التحقق من ملف الإعدادات ✅

ملف `.env.local` يجب أن يبدو هكذا:

```env
# MongoDB
MONGODB_URI="mongodb+srv://admin:MyPassword123@cluster0.xxxxx.mongodb.net/ai-portfolio?retryWrites=true&w=majority"

# Clerk
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY="pk_test_xxxxxxxx"
CLERK_SECRET_KEY="sk_test_xxxxxxxx"
NEXT_PUBLIC_CLERK_SIGN_IN_URL="/sign-in"
NEXT_PUBLIC_CLERK_SIGN_UP_URL="/sign-up"
NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL="/dashboard"
NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL="/dashboard"

# Stripe
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY="pk_test_xxxxxxxx"
STRIPE_SECRET_KEY="sk_test_xxxxxxxx"

# OpenAI
OPENAI_API_KEY="sk-xxxxxxxx"

# App
NEXT_PUBLIC_APP_URL="http://localhost:3000"
```

---

## الخطوة 10: تشغيل المشروع 🎉

1. في Terminal، اكتب:
   ```powershell
   npm run dev
   ```

2. انتظر حتى ترى:
   ```
   ▲ Next.js 15.x.x
   - Local: http://localhost:3000
   ```

3. **افتح المتصفح** واذهب إلى: http://localhost:3000

---

## 🎊 تهانينا! المشروع يعمل الآن!

### ماذا يمكنك فعله الآن:
- ✅ تصفح الصفحة الرئيسية
- ✅ تسجيل حساب جديد (عبر Clerk)
- ✅ تسجيل الدخول
- ✅ إنشاء ملفات شخصية (Portfolios)
- ✅ استخدام الذكاء الاصطناعي لتوليد المحتوى

---

## ❓ مشاكل شائعة وحلولها

### المشكلة: `npm install` بطيء جداً
**الحل:** تأكد من اتصال الإنترنت، أو استخدم:
```
npm install --legacy-peer-deps
```

### المشكلة: خطأ في الاتصال بقاعدة البيانات
**الحل:** تأكد من:
- كتابة كلمة المرور صحيحة
- إضافة IP الخاص بك في MongoDB Atlas
- عدم وجود مسافات في الرابط

### المشكلة: Clerk لا يعمل
**الحل:** تأكد من نسخ المفاتيح كاملة بدون مسافات

### المشكلة: الموقع لا يفتح
**الحل:** تأكد أن Terminal يعرض رسالة `Ready in X ms`

---

## 📞 تحتاج مساعدة؟

إذا واجهت أي مشكلة، أخبرني بالخطأ الذي يظهر وسأساعدك!
