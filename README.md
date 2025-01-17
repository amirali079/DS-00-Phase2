<div dir='rtl' align="justify">
  
# مینی پروژه دوم
یکی از مهم‌ترین مباحث موجود در علوم کامپیوتر و به خصوص یادگیری ماشینی، مبحث فشرده‌سازی و استفاده‌ی بهینه از فضاهای موجود است. هم‌چنین فشرده‌سازی به شکل مناسب، می‌تواند عملیات‌های پایه نظیر افزودن، حذف کردن، جست و جو و اصلاح یک عنصر را تسریع بخشد.

در علم یادگیری ماشینی، داده ساختار ماتریس، یکی از پرکاربردترین ساختمان‌‌های داده به شما می‌رود و از این روی، در این پروژه کوچک، قرار است به مبحث فشرده‌سازی و نمایش صحیح یک ماتریس در ابعاد بزرگ بپردازیم.

شما تا کنون با داده‌ ساختار‌های آرایه و لیست پیوندی آشنا شده و عملیات‌های مربوط به هر یک و پیچیدگی زمانی هرکدام را به خوبی فرا گرفته‌اید. در ادامه شما بایستی به کمک همین دو ساختار، یک ماتریس خلوت را به شکل مناسبی نمایش داده و با کاهش فضای ذخیره‌سازی، اقدامات خواسته شده را انجام دهید.

منظور از ماتریس خلوت، ماتریسی است که تعداد خانه‌های صفر آن بسیار زیاد بوده و نسبت خانه‌های غیرصفر به صفر در آن عدد کوچکی خواهد شد. به عنوان مثال در شکل زیر می‌توانید یک ماتریس خلوت را مشاهده کنید:

![تصویر ماتریس خلوت](../master/images/matrix1.PNG)

همان‌طور که مشخص است، ذخیره‌سازی ماتریس خلوت، به شکل بالا، کار صحیحی نیست، چرا که مقدار قابل توجهی از داده‌های غیرضروری و ناخواسته (عناصر صفر) نیز در حافظه ثبت خواهند شد؛ به همین دلیل استفاده از یک داده ساختار جایگزین برای ذخیره‌سازی ماتریس‌های خلوت، ضروری به نظر می‌رسد.

## تعریف پروژه

فرض کنید ماتریس خلوت داده شده را M بنامیم. برای تشکیل داده ساختاری که از حافظه به شکلی بهینه بهره ببرد، باید ساختاری اتخاذ شود که تنها خانه‌های غیرصفر را در خود ذخیره کند. به همین دلیل نمایش بهینه‌ی ماتریس خلوت به شکل زیر معرفی می‌شود:

آرایه‌ای ازلیست‌های پیوندی، به‌طوری که به ازای هر ردیف یا ستون از ماتریس، لیستی ازعناصر غیر صفرآن نگه‌داری و در نهایت درآرایه‌ای با اندازه‌ی معین (تعداد سطرها یا ستون‌ها)، ذخیره می‌شوند.

داده ساختار پیشنهادی برای پیاده‌سازی، شامل دو ساختار است: node و matrix

هر گره برای عناصر غیر صفر از چهار بخش اندیس سطر یا ستون، مقدار، اشاره‌گری به عنصر غیر صفر بعدی در همان سطر و اشاره‌گری به عنصر غیر صفر بعدی در آن ستون، تشکیل شده‌ است که برای شکل دادن لینک لیست از آنها استفاده می‌شود.

جزء ماتریسی داده ساختار، یک ساختار است شامل آرایه‌ای ازاشاره‌گرها که هر کدام به اولین عنصرغیر صفر در یک ردیف یا ستون اشاره می کنند.

چنانچه این آرایه روی سطرها تعریف شده باشد، اندیس ستون و اگر آرایه روی ستون ها تعریف شده باشد، اندیس سطر در گره نگهداری می‌شود. در اینجا، ما از آرایه‌ای از گره‌های به هم مرتبط برای ساختن ساختاری استفاده می‌کنیم که امکان پیمایش آن از هراندیس دلخواه از ردیف‌ها و یا ستون‌ها، وجود دارد.

## رویدادها

برای هر ماتریس مجموعه‌ای از اتفاقات (eventها) امکان‌پذیر است. رویدادها با عدد ٠ شروع می‌شوند. این رویدادها از دسته های زیر می‌باشند:

### درج گره (کد ٠)

در اثر این رویداد، یک گره جدید به لیست پیوندی اضافه می‌شود. اضافه شدن یک گره به لیست معادل تغییر مقدار یک درایه از ماتریس از مقدار صفر به مقدار خواسته شده است. این تابع باید با دریافت سطر، ستون و مقدار مورد نظر به عنوان ورودی، گره‌ی جدیدی ساخته و با درج آن در محل مناسب ماتریس را بروز کند.

### حذف گره (کد ۱)

در اثر این رویداد، یک گره از لیست پیوندی حذف می‌شود که معادل تغییر مقدار یکی از درایه‌های غیر صفر ماتریس به صفر است. این تابع نیز با دریافت سطر، ستون و مقدار مورد نظر به عنوان ورودی، گره‌ی موجود را حذف و پیوندها را بروزرسانی می‌کند.

### جست و جو (کد ۲)

در اثر این رویداد، وجود یا عدم وجود یک گره در لیست پیوندی (معادل جست و جوی یک مقدار در ماتریس) تشخیص داده می‌شود. این تابع با دریافت مقدار مورد نظر، پیغام مناسب را در هر سناریو به کاربر نمایش می‌دهد.

### بروزرسانی (کد ۳)

در اثر این رویداد، مقدار یک گره موجود بروزرسانی می‌شود. این تابع باید با دریافت اندیس سطر و ستون مورد نظر و مقدار جدید برای بروزرسانی، عملیات خواسته شده را انجام دهد.

### چاپ (کد ۴)

در اثر این رویداد، ماتریس داده شده با فرمت خواسته شده چاپ و نمایش داده می‌شود.

#### نمایش ماتریس به صورت آرایه دو بعدی

در این نوع نمایش ماتریس، شما می‌بایستی داده ساختار پیاده‌سازی شده را به فرم اولیه آن و به صورت آرایه دو بعدی تبدیل و نمایش دهید.

#### نمایش ماتریس به صورت فشرده شده

در این نوع نمایش، داده‌های غیرضروری و ناخواسته (عناصر صفر) چاپ نخواهند شد و قالب پیشنهادی زیر برای نمایش داده‌ها مورد استفاده قرار می‌گیرد:

</div>
<div dir='ltr' align="justify">
  
##### Format:
  
`[row] [col] [value]`

##### Example:

```
1 1 96
1 2 10
2 1 18
2 2 33
```

</div>
<div dir='rtl' align="justify">

### ذخیره سازی (کد ۵)

در اثر این رویداد، داده‌ها در فایل ذخیره می‌شوند.

## ورودی و خروجی

### ورودی

برنامه شما باید با دریافت مجموعه‌ای از داده‌ها در قالب سی اس وی (csv) بتواند اطلاعات را خوانده و سپس آن‌ها را به صورت آرایه‌ای از لیست‌های پیوندی، ذخیره کند.

### خروجی

پس از اجرای صحیح مجموعه‌ای از رویدادها که پیش‌تر شرح داده شد، برنامه باید قادر به چاپ اطلاعات تحت دو نمایش معرفی شده و همچنین ذخیره‌سازی فایل داده‌ها در قالب سی اس وی (csv) باشد.

## نکات تکمیلی

- از کدهای معرفی شده جهت ساخت منو برای سادگی انتخاب عملیات مورد نظر استفاده کنید.
- برنامه شما باید امکان خواندن داده‌های جدید را از فایل‌های دیگر نیز داشته باشد. زیرا داده‌های آزمایشی که در اختیار شما قرار خواهند گرفت با داده‌هایی که در هنگام تحویل پروژه به شما داده خواهد شد متفاوت است.
</div>
<div dir='ltr' align="justify">

موفق و پیروز باشید

</div>
