# 🤖 ContentMaster Bot – AI‑Powered Channel Content Generator

**A complete bot for Rubika platform (similar to Telegram) to manage channels, generate AI captions, create images, edit texts, and handle paid subscriptions.**  
This project demonstrates professional skills in Python, async programming, database design, bot development, and AI integration.

---

## 🚀 Key Features

- **Channel Management** – Register channels with two‑step verification (`/install` inside the channel), generate admin tokens, list/remove admins.
- **AI Content Generation**  
  - Text captions from user input (start with `Creating` or forward a message).  
  - Image generation from text prompts (OpenAI‑compatible).  
  - Auto or custom captions for generated images.  
  - Forward any media (photo, video, GIF, audio, file) – bot downloads, generates caption, reposts.
- **Subscription Plans** – Free tier (10 texts/day + 1 image total) and multiple paid plans with monthly quotas.
- **Payment Flow** – Bank card receipt upload + manual admin verification.
- **Admin Panel** – Stats, payment verification, broadcasts, logs (accessible only to developers).
- **Text Editor** – Polish any text (spelling, punctuation, emojis) – consumes daily text quota.
- **Persistent User State** – Multi‑step interactions stored in SQLite.

## 🧱 Architecture Overview

| Component          | Technology / Approach                                    |
| ------------------ | -------------------------------------------------------- |
| Bot Framework      | `rubpy` (Rubika Bot API)                                 |
| Language           | Python 3.10+ (async/await)                               |
| Database           | SQLite with custom `FlexibleDB` wrapper (thread‑safe, WAL mode) |
| AI Integration     | OpenAI‑compatible API (text & image generation)          |
| Payment Handling   | Manual receipt upload + admin verification               |
| Scheduling         | Asyncio tasks for daily quota reset & subscription expiry |
| Logging            | Rotating file + console logger                           |

## 🔒 Security & Best Practices

- **SQL injection prevention** – Parameterised queries + identifier quoting.  
- **State isolation** – Each user’s state stored as JSON.  
- **Quota enforcement** – Every request checks remaining limits before calling AI APIs.  
- **Idempotent operations** – Daily reset uses `last_text_reset` date.  
- **Async scheduling** – Background tasks without blocking the bot.

## ⚙️ Setup (for your own deployment)

1. Install dependencies: `pip install rubpy openai beautifulsoup4`  
2. Set environment variables:  
   - `BOT_TOKEN` – Rubika Bot token  
   - `OPENAI_API_KEY` – API key for text/image generation  
   - `DEV_IDS` – comma‑separated Rubika user IDs  
   - `CARD_NUMBER`, `CARD_OWNER` – payment information  
3. Run `python main.py`

## 🎯 Skills Showcased

- Asynchronous Python (asyncio, retry logic)  
- Object‑oriented design (handlers, DB, AI, keyboards)  
- State machine for multi‑step user interactions  
- SQLite schema design, indexing, optimisation (WAL, foreign keys)  
- Integration with external AI APIs  
- Event‑driven bot architecture (filters, callbacks)  
- Payment flow with receipt upload and manual verification  
- Clean, maintainable, commented code

---

## 🤖 ربات محتواگر – تولید محتوای هوشمند برای کانال‌های روبیکا

**ربات کامل برای مدیریت کانال، تولید کپشن با هوش مصنوعی، ساخت عکس، ویرایش متن و اشتراک ماهانه.**  
این پروژه مهارت‌های حرفه‌ای در پایتون، برنامه‌نویسی ناهمگام، طراحی دیتابیس، توسعه ربات و یکپارچه‌سازی با هوش مصنوعی را نشان می‌دهد.

---

## 🚀 ویژگی‌های اصلی

- **مدیریت کانال** – ثبت کانال در دو مرحله (ارسال `/install` داخل کانال)، ساخت توکن برای ادمین‌ها، لیست و حذف ادمین.
- **تولید محتوا با AI**  
  - کپشن متنی از ورودی کاربر (شروع با `Creating` یا فوروارد پیام).  
  - تولید عکس از توضیحات متنی.  
  - کپشن خودکار یا دستی برای عکس‌های تولید شده.  
  - فوروارد هر رسانه (عکس، ویدیو، گیف، صدا، فایل) – ربات دانلود می‌کند، کپشن می‌سازد و همراه فایل ارسال می‌کند.
- **پلن‌های اشتراک** – رایگان (۱۰ متن در روز + ۱ عکس کل) و چند پلن پولی ماهانه.
- **پرداخت** – آپلود رسید کارت به کارت + تأیید دستی توسط ادمین.
- **پنل ادمین** – آمار، تأیید پرداخت، ارسال همگانی، مشاهده لاگ (فقط برای توسعه‌دهندگان).
- **ویرایش متن** – اصلاح غلط‌ها، نشانه‌گذاری، ایموجی – مصرف سهمیه متن روزانه.
- **حفظ وضعیت کاربر** – مراحل چندمرحله‌ای در SQLite ذخیره می‌شود.

## 🧱 نمای کلی معماری

| جزء                 | فناوری / روش                                         |
| ------------------- | ---------------------------------------------------- |
| فریمورک ربات        | `rubpy` (API ربات روبیکا)                            |
| زبان                | Python 3.10+ (async/await)                           |
| پایگاه داده         | SQLite با `FlexibleDB` سفارشی (thread‑safe, حالت WAL) |
| هوش مصنوعی          | API سازگار با OpenAI (متن و تصویر)                   |
| پرداخت              | آپلود رسید + تأیید دستی ادمین                        |
| زمان‌بندی وظایف     | تسک‌های asyncio برای بازنشانی سهمیه و انقضای اشتراک  |
| لاگ‌گیری            | فایل چرخشی + کنسول                                    |

## 🔒 امنیت و بهترین روش‌ها

- **پیشگیری از تزریق SQL** – کوئری‌های پارامتری + نقل قول شناسه‌ها.  
- **جداسازی وضعیت** – وضعیت هر کاربر در JSON ذخیره می‌شود.  
- **اجرای سهمیه** – هر درخواست قبل از فراخوانی API، سهمیه باقی‌مانده را بررسی می‌کند.  
- **عملیات Idempotent** – بازنشانی روزانه با استفاده از تاریخ `last_text_reset`.  
- **زمان‌بندی ناهمگام** – وظایف پس‌زمینه بدون مسدود کردن ربات.

## ⚙️ راه‌اندازی (برای استفاده شخصی)

1. نصب وابستگی‌ها: `pip install rubpy openai beautifulsoup4`  
2. تنظیم متغیرهای محیطی:  
   - `BOT_TOKEN` – توکن ربات روبیکا  
   - `OPENAI_API_KEY` – کلید API برای تولید متن و تصویر  
   - `DEV_IDS` – آیدی عددی کاربران توسعه‌دهنده (با کاما جدا شوند)  
   - `CARD_NUMBER`, `CARD_OWNER` – اطلاعات کارت بانکی  
3. اجرا: `python main.py`

## 🎯 مهارت‌های به نمایش گذاشته شده

- پایتون ناهمگام (asyncio، منطق تلاش مجدد)  
- طراحی شیءگرا (هندلرها، دیتابیس، هوش مصنوعی، کیبوردها)  
- ماشین حالت برای تعاملات چندمرحله‌ای کاربر  
- طراحی اسکیما و ایندکس در SQLite، بهینه‌سازی (WAL، کلیدهای خارجی)  
- یکپارچه‌سازی با APIهای خارجی هوش مصنوعی  
- معماری رویدادمحور ربات (فیلترها، کالبک‌ها)  
- جریان پرداخت با آپلود رسید و تأیید دستی  
- کد تمیز، قابل نگهداری و کامنت‌گذاری شده

---

**Created by / ساخته شده توسط:** [https://github.com/m-Researcher-Dev/]  
**Platform / پلتفرم:** Rubika (similar to Telegram)  
**Purpose / هدف:** Portfolio demonstration – complete channel management and AI caption bot / نمایش نمونه‌کار – ربات کامل مدیریت کانال و کپشن‌نویس هوشمند
