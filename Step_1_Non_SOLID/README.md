## جدول تغییرات

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