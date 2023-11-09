# آشنایی با اصول شئ‌گرایی (موسوم به اصول SOLID)

## گام ۱

<table dir='rtl'>
<tbody>
<tr>
<td width="64">
<p><strong>ردیف</strong></p>
</td>
<td width="198">
<p><strong>محل اعمال تغییرات (کلاس/واسط)</strong></p>
</td>
<td width="141">
<p><strong>عنوان تغییر</strong></p>
</td>
<td width="292">
<p><strong>شرحی کوتاه از تغییر</strong></p>
</td>
</tr>
<tr>
<td width="64">
<p><strong>۱</strong></p>
</td>
<td width="198">
<p>Order Service</p>
</td>
<td width="141">
<p>افزودن تابع پرداخت تلفنی</p>
</td>
<td width="292">
<p>افزودن یک تابع void با عنوان phoneOrderPayment</p>
</td>
</tr>
<tr>
<td width="64">
<p><strong>۲</strong></p>
</td>
<td width="198">
<p>Order Service</p>
</td>
<td width="141">
<p>افزودن تابع ثبت سفارش تلفتی</p>
</td>
<td width="292">
<p>افزودن یک تابع void با عنوان phoneOrderRegister</p>
</td>
</tr>
<tr>
<td width="64">
<p><strong>۳</strong></p>
</td>
<td width="198">
<p>Phone Order Service</p>
</td>
<td width="141">
<p>ایجاد کلاس سفارش تلفنی</p>
</td>
<td width="292">
<p>ایجاد کلاس PhoneOrderService که واسط OrderService را پیاده‌سازی می‌کند</p>
</td>
</tr>
<tr>
<td width="64">
<p><strong>۴</strong></p>
</td>
<td width="198">
<p>In Site Order Service</p>
</td>
<td width="141">
<p>اضافه کردن توابع جدید به سفارش حضوری</p>
</td>
<td width="292">
<p>implement کردن توابع پرداخت تلفنی و ثبت سفارش تلفنی در In Site Order Service</p>
</td>
</tr>
<tr>
<td width="64">
<p><strong>۵</strong></p>
</td>
<td width="198">
<p>Online Order Service</p>
</td>
<td width="141">
<p>اضافه کردن توابع جدید به سفارش آنلاین</p>
</td>
<td width="292">
<p>implement کردن توابع پرداخت تلفنی و ثبت سفارش تلفنی در Online Order Service</p>
</td>
</tr>
<tr>
<td width="64">
<p><strong>۶</strong></p>
</td>
<td width="198">
<p>Main</p>
</td>
<td width="141">
<p>اضافه کردن سفارش تلفنی به شیوه‌های ثبت سفارش</p>
</td>
<td width="292">
<p>ثبت سفارش با فراخوانی تابع Phone Order Register از کلاس Phone Order Service در صورت وارد کردن عدد 3</p>
</td>
</tr>
<tr>
<td width="64">
<p><strong>۷</strong></p>
</td>
<td width="198">
<p>Main</p>
</td>
<td width="141">
<p>انجام پرداخت تلفنی</p>
</td>
<td width="292">
<p>ثبت سفارش با فراخوانی تابع Phone Order Payment از کلاس Phone Order Service در صورت ثبت سفارش تلفنی</p>
</td>
</tr>
</tbody>
</table>

مجموع تعداد تغییرات: ۷

## گام ۲

جدول موارد نقض و تحقق اصول SOLID:

<table dir='rtl'>
<tbody>
<tr>
<td rowspan="2" width="240">
<p>اصل 1</p>
<p>Single Responsibility</p>
</td>
<td width="95">
<p><strong>موارد تحقق</strong></p>
</td>
<td width="454">
<p>ثبت و پرداخت هزینه سفارش در کلاس Order انجام نمی شود و در OrderService به آن پرداخته می شود.</p>
</td>
</tr>
<tr>
<td>
<p><strong>موارد نقض</strong></p>
</td>
<td>
<p>کلاس order علاوه بر ذخیره یک سفارش هزینه آن را نیز حساب می کند - تعداد سفارش هر غذا در کلاس Food ذخیره می شود.</p>
</td>
</tr>
<tr>
<td rowspan="2">
<p>اصل 2</p>
<p>Open-Close Principle (OCP)</p>
</td>
<td>
<p><strong>موارد تحقق</strong></p>
</td>
<td>
<p>در صورت نیاز به اضافه کردن یه روش پرداخت جدید نیازی به تغییر توابع موجود نیست و تنها توابع مربوط به روش پرداخت جدید را به Order Service اضافه می‌کنیم.</p>
</td>
</tr>
<tr>
<td>
<p><strong>موارد نقض</strong></p>
</td>
<td>
<p>در صورتی که واسط OrderService را در کلاس جدیدی پیاده سازی کنیم، مجبور به تغییر تابع main و اضافه کردن روش پرداخت جدید به دو سلسله if هستیم.</p>
</td>
</tr>
<tr>
<td rowspan="2">
<p>اصل 3</p>
<p>Liskov Substitution Principle</p>
</td>
<td>
<p><strong>موارد تحقق</strong></p>
</td>
<td>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td>
<p><strong>موارد نقض</strong></p>
</td>
<td>
<p>نمی‌توان روش‌های مختلف پرداخت را جایگزین یکدیگر کرد. در کلاس onlineOrderService تابع OnlineOrderRegister سفارش را ثبت می‌کند و در PhoneOrderService تابع PhoneOrderRegister. در نتیجه تابعی که برای یکی از پیاده‌سازی‌های orderService سفارش را ثبت می‌کند، برای پیاده‌سازی دیگر کاری نمی‌کند.</p>
</td>
</tr>
<tr>
<td rowspan="2">
<p>اصل 4</p>
<p>Interface Segregation Principle</p>
</td>
<td>
<p><strong>موارد تحقق</strong></p>
</td>
<td>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td>
<p><strong>موارد نقض</strong></p>
</td>
<td>
<p>هر کدام از کلاس‌هایی که واسط Order Service را پیاده‌سازی می‌کردند مجبور بودند تمامی توابع آن را voerride کنند. در حالی که بدنه توابعی که مربوط به آن نوع از پرداخت نبودند خالی می‌ماندند.</p>
</td>
</tr>
<tr>
<td rowspan="2">
<p>اصل 5</p>
<p>Dependency Inversion Principle</p>
</td>
<td>
<p><strong>موارد تحقق</strong></p>
</td>
<td>
<p>هر سه کلاس شیوه پرداخت آنلاین، حضوری و تلفنی یک واسط انتزاعی را پیاده‌سازی می‌کنند.</p>
</td>
</tr>
<tr>
<td>
<p><strong>موارد نقض</strong></p>
</td>
<td>
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>

جدول راهکارهای موارد نقض:

<table dir='rtl'>
<tbody>
<tr>
<td width="168">
<p><strong>اصل مربوطه (از اصول </strong><strong>SOLID</strong><strong>)</strong></p>
</td>
<td width="246">
<p><strong>علت نقض</strong></p>
</td>
<td width="284">
<p><strong>راه حل پیشنهادی</strong></p>
</td>
</tr>
<tr>
<td width="168">
<p>Liskov Substitution Principle</p>
</td>
<td width="246">
<p>نمی‌توان روش‌های مختلف پرداخت را جایگزین یکدیگر کرد.</p>
</td>
<td width="284">
<p>در واسط OrderService تنها دو تابع RegisterService و pay را انتزاع می‌کنیم. هر روش پرداخت تنها این دو تابع را پیاده‌سازی می‌کند.</p>
</td>
</tr>
<tr>
<td width="168">
<p>Interface Segregation Principle</p>
</td>
<td width="246">
<p>هر کدام از کلاس‌هایی که واسط Order Service را پیاده‌سازی می‌کردند مجبور بودند تمامی توابع آن را voerride کنند. در حالی که بدنه توابعی که مربوط به آن نوع از پرداخت نبودند خالی می‌ماندند.</p>
</td>
<td width="284">
<p>در واسط OrderService تنها دو تابع RegisterService و pay را انتزاع می‌کنیم. هر روش پرداخت تنها این دو تابع را پیاده‌سازی می‌کند.</p>
</td>
</tr>
<tr>
<td width="168">
<p>Single Responsibility</p>
</td>
<td width="246">
<p>تابع main وظایف زیادی را هندل می کند که این برخلاف اصل است</p>
</td>
<td width="284">
<p>به منظور رفع این موضوغ می توان توابع جداگانه ای تعریف کرد که در فایل main صدا زده شوند.</p>
</td>
</tr>
<tr>
<td width="168">
<p>&nbsp;</p>
</td>
<td width="246">
<p>&nbsp;</p>
</td>
<td width="284">
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>
### گام ۴: بررسی مجدد تغییرات مورد نیاز
فرض کنید که گام 1 را برای کد اصلاح شده (پس از انجام گام‌های ۲ و ۳) اجرا کرده‌اید.
1. در این صورت از انجام کدام یک از تغییرات ثبت شده در جدول گام ۱ معاف خواهید شد؟
از آنجایی که OrderServices به عنوان interface تغییر قابل توجی پیدا کرد و فقط دو تابع registerService و pay فقط در نظر گرفته شد، کلیه تغییراتی که در سایر روش های پرداخت در خصوص پرداخت تلفنی انجام شد، قابل عرضه نمی‌باشد.  
2. تعداد تغییرات مورد نیاز، چند تغییر خواهد شد؟
2

### گام ۵: جمع بندی
در این بخش، بیان کنید که از این گام چه نتیجه‌ای گرفته‌اید؟ و به نظر شما به کارگیری صحیح اصول SOLID در گام‌های ۳ و ۴ چه مزایایی را نسبت به حالتی دارد که این اصول رعایت نشده‌بود؟
همانطور که از سوالات گام ۴ می توان درک کرد، زمانی که ما اصول SOLID را بکار میگیریم، در صورت نیاز به تغییر هایی چه در جزئی و چه در سطح منطق پروژه(افزودن روش تلفتی) دچار سردرگمی کمتر خواهیم شد و نیاز کمتری به تغییرات متعدد خواهیم داشت، همچنین با در نظر گیری آن توانستیم بار functionality های کلاس ها و توابع را بهتر مدیریت کنیم که این مورد به خودی خود مزایای زیادی خواهد داشت. به طور کلی هر یک از این اصول به ما کمک می‌کند تا پروژه ای با قابلیت های مناسب تر به منظور سهولت در نگهداری، تغییر و به روز رسانی داشته باشیم. گرچه در بطن هر یک از این اصول مزایای فراوانی وجود دارد که پیش تر به آن پرداخته ایم و توضیح آن تکرار مکررات خواهد بود. در کل این آزمایش در زمان کم و پروژه ای قابل درک و مختصر توانست به وضوح قدرت رعایت این اصول را نشان دهد و این امکان را داد که بدانیم برای رعایت این اصول به دنبال رفتار پیچیده ای نباید بود و نه تنها این موارد در دنیای واقعی کاملا tangible است بلکه می تواند پروژه را از مشکلات احتمالی در آبنده تا حد خوبی بیمه کند.
