<!DOCTYPE html><html lang="fa" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>HACER ZX</title><style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:tahoma;
}

body{
    background:linear-gradient(135deg,#0a0a0a,#111,#1a1a1a);
    color:white;
    min-height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
}

body.light{
    background:linear-gradient(135deg,#ffffff,#f0f0f0,#dddddd);
    color:#111;
}

body.light .page{
    background:#ffffff;
    color:#111;
}

.container{
    width:90%;
    max-width:450px;
    text-align:center;
}

.settings-icon{
    font-size:32px;
    cursor:pointer;
    margin-bottom:15px;
    user-select:none;
}

.logo{
    font-size:38px;
    font-weight:bold;
    margin-bottom:25px;
    background:linear-gradient(90deg,#ff0000,#00ffff,#00ff00,#ff00ff);
    background-size:400%;
    -webkit-background-clip:text;
    -webkit-text-fill-color:transparent;
    animation:rgb 5s linear infinite;
}

@keyframes rgb{
    0%{background-position:0%}
    100%{background-position:400%}
}

.btn{
    display:block;
    width:100%;
    margin:12px 0;
    padding:15px;
    border:none;
    border-radius:15px;
    color:white;
    font-size:18px;
    cursor:pointer;
    background:linear-gradient(90deg,#ff0000,#ff00ff,#00ffff);
    background-size:300%;
    animation:rgb 4s linear infinite;
    box-shadow:0 0 15px rgba(255,255,255,0.3);
}

.page{
    display:none;
    background:#111;
    padding:20px;
    border-radius:15px;
    text-align:right;
}

.back{
    margin-top:20px;
    background:red;
}
</style></head>
<body><div class="container"><div id="main"><div class="settings-icon" onclick="openSettings()"></div><h1 class="logo">HACER ZX</h1><button class="btn"
onclick="window.open('https://rubika.ir/page/HACER908','_blank')">
📱 کانال روبیکا
</button>

<button class="btn"
onclick="window.location.href='https://t.me/MMDO56bot'">
🤖 ربات تلگرام
</button>

<button class="btn"
onclick="window.open('https://www.aparat.com/shorts/user/HACERZX345/shorts','_blank')">
🎬 کانال آپارات
</button>

<button class="btn"
onclick="openPage()">
💖 حمایت از ما و آموزش ربات
</button>

<button class="btn"
onclick="window.open('https://rubika.ir/page/HACER908','_blank')">
👑 پنل سازنده
</button>

<button class="btn" onclick="toggleTheme()">
🎨 تغییر تم
</button><button class="btn"
onclick="window.location.href='mailto:chjvjknvhj@gmail.com'">
📧 ارتباط با ما
</button>

</div><div id="page" class="page"><h2>💖 حمایت از ما</h2><p>
لینک حمایت از ما:
<br><br>
https://daramet.com/HACERZX
<br><br>
راهنمای ساخت ربات:
<br>
logo
بات روبیکا
معرفی


logoبات روبیکا
معرفی
فهرست موضوعات
مراحل استفاده
توضیحات
receiveUpdate
receiveInlineMessage
متد ها
مدل ها
گروه ها و کانال ها
معرفی
روبیکا مجموعه‌ای از APIها را در اختیار توسعه‌دهندگان قرار می‌دهد که با استفاده از آن‌ها می‌توان بات ایجاد و مدیریت کرد. برای استفاده از این APIها، مراحل زیر را دنبال کنید.

مراحل استفاده¶
۱. با استفاده از BotFather به آدرس BotFather@ در روبیکا، یک بات ایجاد کنید.
۲. توکن دریافتی را ذخیره کرده و در مراحل بعدی از آن استفاده کنید.
۳. با استفاده از توکن مرحله‌ی قبل و متد مورد نظر، یک URL با قالب زیر ایجاد کرده و درخواست خود را با متد POST ارسال کنید.

https://botapi.rubika.ir/v3/{token}/{method}
توضیحات¶
پس از ساخت بات در BotFather، برای اینکه بات شما از اقدامات کاربران (ارسال پیام، کلیک روی دکمه‌ها و …) مطلع شود، دو روش اصلی وجود دارد:



روش ۱: فراخوانی متد getUpdates
(Long Polling)
در این روش، بات شما به‌صورت دوره‌ای از سرور روبیکا بررسی می‌کند که آیا رویداد یا پیام جدیدی دریافت شده است یا خیر.
برای پیاده‌سازی، باید در بازه‌های زمانی مشخص (برای مثال هر ۵ ثانیه) و با استفاده از مقدار start_id که از فراخوانی قبلی دریافت کرده‌اید، متد getUpdates را صدا بزنید.
در این روش ممکن است از رویدادها با تأخیر مطلع شوید، زیرا تا زمانی که درخواست جدیدی ارسال نکنید، پیام‌ها دریافت نمی‌شوند و به همان میزان نیز پاسخ بات به کاربر با تأخیر همراه خواهد بود.


روش ۲: دریافت اطلاعات از طریق تعریف Endpoint
(Webhook)
در این روش، با تنظیم یک Endpoint روی سرور خود، به‌محض وقوع هر رویداد مرتبط با بات (مانند ارسال پیام یا کلیک روی دکمه)، روبیکا اطلاعات رویداد را به آدرسی که مشخص کرده‌اید ارسال می‌کند.
برای فعال‌سازی این روش، با استفاده از متدی مانند updateBotEndpoint، آدرس سرور خود را به پلتفرم معرفی می‌کنید. پس از تنظیم Endpoint، در هر رویداد، هر زمان کاربر پیامی ارسال کند، پلتفرم یک درخواست POST شامل اطلاعات رویداد را (بر اساس نوع آن) در قالب‌هایی مانند Update، InlineMessage و … به Endpoint شما ارسال خواهد کرد.
توجه:

این روش نیازمند یک سرور با دامنه عمومی و پشتیبانی از SSL (HTTPS) است، زیرا پلتفرم تنها به آدرس‌های امن متصل می‌شود.
در صورت بروز خطا یا عدم دریافت پاسخ معتبر از Endpoint، امکان توقف موقت ارسال رویدادها توسط پلتفرم وجود دارد.


برای انواع مختلف رویدادها، لازم است Endpointهای مجزایی تعریف شود که مهم‌ترین آن‌ها در ادامه معرفی شده‌اند.
receiveUpdate¶
هر زمان کاربر پیامی ارسال کند یا دکمه‌های ChatKeypad (دکمه‌های پایین صفحه چت) را لمس کند، شما یک درخواست POST دریافت می‌کنید که بدنه آن شامل شیء Update است.


نمونه body :


{
  "update": {
      "type": "NewMessage",
      "chat_id": "{chat_id}",
      "new_message": {
          "message_id": "{message_id}",
          "text": "custom text",
          "time": "1643122902",
          "is_edited": false,
          "sender_type": "User",
          "sender_id": "{sender_id}",
          "aux_data": {
              "start_id": null,
              "button_id": "{button_id}"
          }
      }
  }
}


receiveInlineMessage¶
هرگاه کاربر روی InlineKeypad (دکمه‌های شیشه‌ای زیر پیام‌ها) کلیک کند، یک درخواست POST دریافت می‌کنید که بدنه‌ی آن شامل شیء POST دریافت می‌کنید که بدنه (body) آن شامل شیء InlineMessage است.


نمونه body :


{
    "inline_message": {
        "sender_id": "{sender_id}",
        "text": "custom text",
        "location": null,
        "aux_data": {
            "start_id": null,
            "button_id": "{button_id}"
        },
        "message_id": "{message_id}",
        "chat_id": "{chat_id}"
    }
}
به‌طور کلی، انتخاب بین دو روش دریافت رویداد به شرایط زیر بستگی دارد:

روش getUpdates
مناسب برای پروژه‌های ساده، محیط‌های توسعه یا زمانی که امکان راه‌اندازی سرور عمومی و HTTPS وجود ندارد. این روش پیاده‌سازی ساده‌تری دارد، اما به‌دلیل ماهیت دوره‌ای درخواست‌ها، دریافت رویدادها با تأخیر همراه است.
روش تعریف Endpoint
مناسب برای پروژه‌های پایدار و در مقیاس productionاست. در این روش، رویدادها به‌صورت آنی و بدون تأخیر به سرور شما ارسال می‌شوند. استفاده از این روش مستلزم داشتن سرور با دامنه عمومی و پشتیبانی از SSL است.
در محیط‌های عملیاتی، استفاده از Webhook به‌دلیل کارایی بالاتر و دریافت بلافاصله رویدادها توصیه می‌شود.
زمانی که شما از طرف بات به شکل بالا Request را دریافت و پردازش کردید، می‌توانید با استفاده از این متد‌ها به آن پاسخ دهید.
</p><button class="btn back" onclick="closePage()">
بازگشت
</button></div><div id="settingsPage" class="page"><h2>⚙️ تنظیمات</h2><p>
نسخه سایت: HACER ZX
<br><br>
سازنده: HACER908
</p><button class="btn" onclick="toggleTheme()">
🌙 / ☀️ تغییر تم
</button><button class="btn back" onclick="closeSettings()">
بازگشت
</button></div></div><script>
function openPage(){
document.getElementById("main").style.display="none";
document.getElementById("page").style.display="block";
}

function closePage(){
document.getElementById("page").style.display="none";
document.getElementById("main").style.display="block";
}

function openSettings(){
document.getElementById("main").style.display="none";
document.getElementById("settingsPage").style.display="block";
}

function closeSettings(){
document.getElementById("settingsPage").style.display="none";
document.getElementById("main").style.display="block";
}

function toggleTheme(){
document.body.classList.toggle("light");
}

window.onload = function(){
setTimeout(function(){
alert("🎉 خوش آمدید به سایت HACER ZX 🎉");
},500);
}
</script></body>
</html>
