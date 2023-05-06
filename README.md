# اسکنر آیپی کلادفلر (اختصاصی صفا صفری)

برای این اسکنر زحمات زیادی کشیده شده است
ساعت ها مهندسی معکوس بر روی کلاینت های مختلف انجام شده


# مهم
## در حال حاضر، اسکنر روی اپراتور های ایرانسل و ~~همراه اول~~ با اشکالاتی رو به رو هست، در حال بررسی و رفع مشکل هستم
---
## اپراتور ایرانسل به کلی تمام آیپی های کلادفلر رو محدود کرده
---
## همراه اول با حالت personal server بهترین عملکرد را دارد
---
## راهنما
* [نصب](#نصب)
    * [اندروید](#اندروید)
    * [ویندوز](#ویندوز)
    * [مک](#مک)
* [اجرای برنامه](#اجرای-برنامه)
    * [حالت speed](#حالت-speed)
    * [حالت vmess](#حالت-vmess)
    * [حالت vless](#حالت-vless)
    * [حالت personal server](#حالت-personal-server)
* [حمایت مالی](#حمایت-مالی)
* [شبکه های اجتماعی](#شبکه-های-اجتماعی)

# نصب
## اندروید

برای نصب روی سیستم عامل اندروید، نیاز به برنامه ای تحت عنوان ترموکس (Termux) میباشد

[لینک دانلود ترموکس از گیتهاب](https://github.com/termux/termux-app/releases/)

در اینجا با چندین فایل apk مواجه میشوید. اگر نوع دستگاه اندرویدی خود را نمیدانید، نسخه armeabi-v7a را دانلود و نصب کنید

نکته: ترموکس را فقط از لینک رسمی گیتهاب این پروژه دانلود کنید، نسخه ای که در گوگل پلی قرار دارد، نسخه قدیمی است و ممکن است در نصب پکیج ها به مشکل بخورید

در ادامه با باز کردن برنامه ترموکس، خط فرمان به شما نشان داده میشود
به ترتیب دستورات زیر را وارد کنید

```bash
pkg update -y; pkg install -y python python-pip openssl python-cryptography
```

در هنگام نصب، تمام پرسش ها را با `y` جواب دهید

```bash
curl -sLo main.zip https://github.com/SafaSafari/ss-cloud-scanner/archive/refs/heads/main.zip && unzip -qq main.zip && rm main.zip`

cd ss-cloud-scanner-main

pip install -r ./requirements.txt
```

در صورتی که پیش نیاز ها با موفقیت نصب شوند، کار تمام است و وقت آن رسیده که برنامه را [اجرا](#اجرای-برنامه) کنید

---
## ویندوز

برای نصب پایتون بر روی ویندوز، از طریق لینک زیر و با توجه به نسخه سیستم عامل، نسبت به دانلود نسخه مناسب اقدام فرمایید

[دانلود پایتون نسخه ویندوز از سایت رسمی](https://www.python.org/downloads/windows/)

در هنگام نصب پایتون، تیک مربوط به نصب pip و اضافه کردن پایتون به PATH را فراموش نکنید

حال [این فایل](https://github.com/SafaSafari/ss-cloud-scanner/archive/refs/heads/main.zip) فشرده را دانلود کنید و آن را از حالت فشرده خارج کنید

اکنون وقت آن رسیده یک ترمینال (cmd) در مسیر اکسترکت پروژه اجرا کنید و برای نصب پیش نیاز ها دستور زیر را اجرا کنید

```bash
pip install -r ./requirements.txt
```

در صورتی که پیش نیاز ها با موفقیت نصب شوند، کار تمام است و وقت آن رسیده که برنامه را [اجرا](#اجرای-برنامه) کنید

---
## مک
به زودی :))

---
# اجرای برنامه
با دستور زیر، عملکرد برنامه آغاز میشود

```bash
python main.py
```

به محض اجرا، برنامه از شما تعداد آیپی مورد نیاز را درخواست میکند

در مرحله بعد نوع اسکن مشخص میشود

---
## حالت speed
این نوع از اسکن، با توحه به وایت لیست بودن sni در ایران ([منبع](https://twitter.com/safasafari3/status/1643154352326975488)) از یک ورکر جایگزین استفاده میکند که بازدهی این مدل اسکن را بشدت بالا میبرد

---
## حالت vmess
این مدل اسکن با ساخت پکت vmess و ارسال آن به سمت سرور با websocket عملا یک ارتباط پروکسی را شبیه سازی میکند
اسکنر های جایگزین، این کار با استفاده از هسته های v2ray یا xray انجام میدهند، اما این اسکنر این اقدام را بصورت خالص با پایتون پیاده سازی نموده است
برای استفاده از این حالت، بعد از انتخاب این حالت، لینک یک پروکسی vmess از شما درخواست میشود (با vmess:// شروع میشود) و پس از جایگذاری و ثبت، عملیات اسکن آغاز میشود

---
## حالت vless
این حالت نیز مانند vmess میباشد و بعد از انتخاب حالت، از شما درخواست لینک vless میکند (با vless://) و عملیات اسکن شروع میشود

---
## حالت personal server
این حالت بهترین و قابل اتکا ترین حالت هست، بدین صورت که اسکریپت upload.py را روی سرور خودتون دانلود و اجرا میکنید و در کلادفلر یک سابدامین بهش اختصاص می دهید و بعد از انتخاب این حالت، آدرس دامنه را وارد کرده و حالت اسکن (http/https) را انتخاب میکنید و فرآیند اسکن آغاز میشود

---
# حمایت مالی
Rial: [نکست پی](https://nextpay.org/nx/irp/safa)

Btc: `bc1qgrlfzelx6dn6hym7c73jpp2w2p4hdy7lgftudr`

Ltc: `ltc1ql02lg3yrtgy7xfnnl5jvgrwv2ffxkhyn54qyj0`

Usdt(trc20): `TH8PcLF25uGhT4joJy7K5YQP43oYxs7ouY`

Tron: `TH8PcLF25uGhT4joJy7K5YQP43oYxs7ouY`

---
# شبکه های اجتماعی
[Twitter](https://twitter.com/SafaSafari3)

[Telegram](https://SafaSafari.t.me)

[Youtube](https://youtube.com/@SafaSafari)

[Instagram](https://instagram.com/SafaSafari.ss)