## راهنمای جامع `.gitignore`

فایل `.gitignore` یکی از فایل‌های کلیدی در هر پروژه‌ای است که با گیت (Git) مدیریت می‌شود. این فایل به شما امکان می‌دهد مشخص کنید کدام فایل‌ها و دایرکتوری‌ها نباید توسط گیت پیگیری شوند. این موضوع مخصوصاً زمانی اهمیت پیدا می‌کند که فایل‌هایی وجود دارند که نیازی به اشتراک‌گذاری یا ذخیره در مخزن ندارند (مثل فایل‌های خروجی، موقت یا فایل‌های حاوی اطلاعات شخصی).

در این راهنما، به ساختار فایل `.gitignore`، نحوه نوشتن آن، و نکات و ترفندهای مهم برای استفاده بهتر از این فایل می‌پردازیم.

### ساختار و اصول اولیه `.gitignore`

فایل `.gitignore` یک فایل متنی ساده است که هر خط آن یک الگو برای نادیده گرفتن فایل‌ها یا دایرکتوری‌ها تعریف می‌کند. این الگوها می‌توانند شامل نام فایل‌ها، دایرکتوری‌ها یا ترکیب‌های پیچیده‌تری باشند.

### قوانین کلی:

- **هر خط یک الگو:** هر خط از فایل `.gitignore` نشان‌دهنده‌ی یک الگوی نادیده گرفتن است.
- **خط‌های خالی و کامنت‌ها:** خطوط خالی و خطوطی که با `#` شروع می‌شوند به عنوان کامنت در نظر گرفته می‌شوند و گیت آن‌ها را نادیده می‌گیرد.
- **علامت `!`:** اگر یک خط با `!` شروع شود، به گیت گفته می‌شود که آن فایل یا پوشه را پیگیری کند حتی اگر قبلاً با یک الگوی دیگر نادیده گرفته شده باشد.
- **دایرکتوری‌ها با `/`:** اضافه کردن `/` در انتهای یک نام دایرکتوری باعث می‌شود گیت تمام فایل‌های داخل آن دایرکتوری را نادیده بگیرد.

### مثال‌های ساده:

```plaintext
# نادیده گرفتن فایل‌های خروجی
*.log

# نادیده گرفتن دایرکتوری node_modules/
node_modules/

# نادیده گرفتن فایل‌های کش پایتون
__pycache__/

# نادیده گرفتن فایل‌های کامپایل‌شده C
*.o
```

### کاراکترهای ویژه و الگوها در `.gitignore`

#### 1. **الگوهای عمومی با `*`:**

`*` به عنوان کاراکتر wildcard (جانشین) استفاده می‌شود و به معنای تطبیق با هر تعداد کاراکتر است.

- `*.log`: تمام فایل‌هایی با پسوند `.log` را نادیده می‌گیرد.
- `build/*`: تمام فایل‌های داخل دایرکتوری `build/` را نادیده می‌گیرد.

#### 2. **الگوهای سطحی با `/`:**

- `test/`: فقط دایرکتوری `test/` در سطح جاری را نادیده می‌گیرد.
- `/*.log`: فقط فایل‌های `.log` در ریشه‌ی پروژه را نادیده می‌گیرد و فایل‌های مشابه در دایرکتوری‌های فرعی را نادیده نمی‌گیرد.

#### 3. **نادیده گرفتن یک فایل مشخص:**

اگر بخواهید فقط یک فایل خاص را نادیده بگیرید:

- `config/settings.json`: فقط این فایل را در مسیر مشخص نادیده می‌گیرد.

#### 4. **علامت `!` برای پیگیری فایل خاص:**

گاهی اوقات ممکن است بخواهید یک فایل خاص را از بین فایل‌های نادیده گرفته‌شده استثناء کنید.

- `*.log`: همه فایل‌های `.log` را نادیده بگیر.
- `!important.log`: اما فایل `important.log` را پیگیری کن.

#### 5. **الگوهای recursive:**

- `**/temp`: همه‌ی دایرکتوری‌های `temp/` را در هر سطحی از پروژه نادیده می‌گیرد.
- `**/*.log`: همه فایل‌های `.log` را در تمام دایرکتوری‌ها و زیرشاخه‌ها نادیده می‌گیرد.

### نکات و ترفندها

#### 1. **تنظیم `.gitignore` به‌طور خاص برای سیستم‌عامل‌ها**

فایل‌های موقتی یا خروجی مربوط به سیستم‌عامل‌های مختلف را می‌توانید به `.gitignore` اضافه کنید تا این فایل‌ها در مخزن گیت ذخیره نشوند. مثال‌هایی برای سیستم‌عامل‌ها:

**macOS:**

```plaintext
# macOS specific ignores
.DS_Store
.AppleDouble
```

**Windows:**

```plaintext
# Windows specific ignores
Thumbs.db
ehthumbs.db
```

#### 2. **الگوهای خاص زبان‌های برنامه‌نویسی**

بسیاری از زبان‌ها فایل‌های موقتی و خروجی خاص خود را دارند. اضافه کردن این فایل‌ها به `.gitignore` از ذخیره شدن فایل‌های غیرضروری جلوگیری می‌کند.

**JavaScript (Node.js):**

```plaintext
# Node.js dependencies
node_modules/
npm-debug.log
yarn-error.log
```

**Python:**

```plaintext
# Byte-compiled / optimized / DLL files
__pycache__/
*.py[cod]

# Virtual environment
.venv/
```

**Java:**

```plaintext
# Compiled class file
*.class

# Log files
*.log
```

#### 3. **ایجاد یک فایل `.gitignore` جهانی**

اگر پروژه‌های مختلفی دارید و می‌خواهید برخی فایل‌ها را برای همه پروژه‌ها نادیده بگیرید، می‌توانید یک فایل `.gitignore` جهانی بسازید. این کار می‌تواند برای فایل‌های سیستم‌عامل، ویرایشگر متن یا ابزارهای توسعه بسیار مفید باشد.

**ایجاد فایل `.gitignore` جهانی:**

```bash
git config --global core.excludesfile ~/.gitignore_global
```

**نمونه‌ای از `.gitignore` جهانی:**

```plaintext
# macOS
.DS_Store

# Vim
*.swp

# Logs
*.log
```

#### 4. **پاک کردن فایل‌های نادیده گرفته شده از مخزن**

اگر فایلی قبلاً به مخزن اضافه شده و حالا می‌خواهید آن را از مخزن حذف کنید و به `.gitignore` اضافه کنید، ابتدا باید آن را از مخزن حذف کنید (بدون حذف آن از دیسک):

```bash
git rm --cached <filename>
```

سپس فایل را به `.gitignore` اضافه کنید تا از این پس پیگیری نشود.

#### 5. **استفاده از `.git/info/exclude` برای نادیده گرفتن فایل‌های محلی**

اگر بخواهید به‌طور موقت و فقط در سیستم خودتان فایل‌هایی را نادیده بگیرید، می‌توانید به‌جای استفاده از `.gitignore` از فایل `.git/info/exclude` استفاده کنید. این فایل برای نادیده گرفتن فایل‌ها به‌صورت محلی و بدون اشتراک‌گذاری با دیگران استفاده می‌شود.

#### 6. **بررسی وضعیت فایل‌های نادیده گرفته**

برای مشاهده اینکه کدام فایل‌ها توسط `.gitignore` نادیده گرفته شده‌اند، می‌توانید از دستور زیر استفاده کنید:

```bash
git status --ignored
```

این دستور لیستی از تمام فایل‌هایی که توسط `.gitignore` نادیده گرفته شده‌اند را نمایش می‌دهد.

#### 7. **نکته مهم: به روزرسانی .gitignore در میانه پروژه**

اگر پس از مدتی متوجه شوید که باید فایل‌هایی را به `.gitignore` اضافه کنید، مطمئن شوید که فایل‌هایی که از قبل به مخزن اضافه شده‌اند، با استفاده از `git rm --cached` از مخزن حذف شوند و سپس به `.gitignore` اضافه شوند. در غیر این صورت، گیت آن‌ها را همچنان پیگیری خواهد کرد.

### نتیجه‌گیری

فایل `.gitignore` یکی از ابزارهای قدرتمند گیت برای مدیریت بهینه فایل‌ها و جلوگیری از ورود فایل‌های غیرضروری به مخزن است. با استفاده از الگوهای مناسب و ترفندهای گفته‌شده، می‌توانید پروژه خود را تمیز و منظم نگه دارید و از بارگذاری فایل‌های نامرتبط جلوگیری کنید.