# MikroBase — رابط کاربری Vue 3 (بدون نصب و بدون build)

همین پروژه‌ی قبلی است؛ فقط **فرانت‌اند با Vue 3 بازنویسی شده**. بک‌اند PHP (`private/`، `api/`، `login.php`،
`servers.php`، `settings.php`، `admins.php`، `shareuser.php`) منطقش دست نخورده است.

نیازی به Node، npm یا هر نصب دیگری نیست؛ فقط Apache/PHP (مثل XAMPP) و یک مرورگر جدید.

## ساختار
```
index.php  login.php          صفحه‌ها (فقط پوسته‌ی HTML عوض شده؛ منطق PHP همان است)
api/ private/ servers.php ... بک‌اند قبلی (بدون تغییر)
vue/                          کل برنامه‌ی Vue
  main.js login.js router.js  شروع برنامه و مسیریاب
  api/  stores/  composables/ utils/
  components/ui/              AppModal, ConfirmHost, ToastHost, DropdownMenu, AppTabs ...
  components/users/           فرم و دیالوگ‌های کاربران
  views/                      Dashboard, Users, OnlineUsers, Servers, Admins, Settings, Login
legacy/                       فایل‌های jQuery قدیمی (دیگر لود نمی‌شوند)
res/                          CSS/فونت‌های قبلی (بدون تغییر)
```

## فایل Vue (فقط یک بار)
برنامه به `vue.esm-browser.prod.js` نیاز دارد:

* **با اینترنت:** هیچ کاری لازم نیست؛ خودکار از CDN (jsDelivr) لود می‌شود.
* **کاملاً آفلاین (پرتابل):** این فایل را یک‌بار دانلود کنید و در پوشه‌ی `res/` بگذارید:
  https://cdn.jsdelivr.net/npm/vue@3.5.13/dist/vue.esm-browser.prod.js
  (نام فایل دقیقاً `res/vue.esm-browser.prod.js` باشد.)

## اجرا
پوشه‌ی پروژه را در `htdocs` بگذارید و `http://127.0.0.1/mikrobase/` را باز کنید.
بعد از هر تغییر در فایل‌ها یک بار `Ctrl+F5` بزنید.

## جایگزین‌ها
| قبلی | الان |
|---|---|
| `ShowModal.js` | `AppModal.js` + `useConfirm()` (با `await`) |
| toastr / Notyf | `ToastHost.js` + `useNotify()` |
| دراپ‌داون/تب Bootstrap JS | `DropdownMenu.js`, `AppTabs.js` |
| jQuery و ساخت HTML با رشته | قالب‌های Vue (خودکار escape) |

## نکات
* پورتال کاربران (`getClientDetails.php`) در پروژه نبود؛ پس در این نسخه نیست.
* پسورد API میکروتیک در `private/*.db` است؛ این فایل‌ها را هرگز در گیت‌هاب نگذارید (`.gitignore` اضافه شده).
