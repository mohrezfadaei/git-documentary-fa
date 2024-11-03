## دستور `git add`

دستور `git add` برای اضافه کردن تغییرات فایل‌ها به مرحله آماده‌سازی (staging area) در گیت استفاده می‌شود. این دستور به گیت می‌گوید که کدام تغییرات در فایل‌ها برای کامیت بعدی آماده شوند. تنها فایل‌ها یا تغییراتی که با `git add` به مرحله آماده‌سازی اضافه شده‌اند، در کامیت ثبت می‌شوند.

### استفاده‌های معمول از دستور `git add`:

1. **اضافه کردن یک فایل خاص به مرحله آماده‌سازی:**

   ```bash
   git add <filename>
   ```

2. **اضافه کردن تمام تغییرات به مرحله آماده‌سازی:**

   ```bash
   git add .
   ```

3. **اضافه کردن چند فایل یا دایرکتوری به مرحله آماده‌سازی:**

   ```bash
   git add <file1> <file2> <directory/>
   ```

4. **اضافه کردن تغییرات در بخشی از فایل:**
   ```bash
   git add -p
   ```

### دستور `git add` چه کار می‌کند؟

- فایل‌های مشخص شده را به مرحله آماده‌سازی (staging area) اضافه می‌کند.
- به گیت می‌گوید که این فایل‌ها و تغییرات آن‌ها باید در کامیت بعدی ثبت شوند.
- فایل‌های اصلاح‌شده، جدید و یا حذف‌شده را به همراه متادیتا (metadata) مرتبط به گیت معرفی می‌کند.

### چه اتفاقی در پس‌زمینه می‌افتد؟

1. **ایندکس کردن تغییرات:** وقتی دستور `git add` اجرا می‌شود، گیت تغییرات را از فایل‌های کاری شما برمی‌دارد و آن‌ها را در مرحله آماده‌سازی قرار می‌دهد. این مرحله در واقع یک ایندکس از تغییرات است که گیت آن را در حافظه محلی خود ذخیره می‌کند.

2. **ایجاد یک ایندکس جدید (Staging Area):**
   - مرحله آماده‌سازی (staging area) یک ناحیه موقت است که گیت از آن برای جمع‌آوری تغییراتی که قرار است در کامیت بعدی ثبت شوند، استفاده می‌کند.
   - وقتی شما از `git add` استفاده می‌کنید، گیت یک کپی از تغییرات را در این ناحیه ذخیره می‌کند. این تغییرات در واقع یک اسنپ‌شات از فایل‌ها و تغییرات آن‌ها است.
3. **به‌روزرسانی فایل‌های ایندکس در پوشه `.git/`:** در پوشه `.git/`، گیت اطلاعات ایندکس را در فایل‌های مختلف ذخیره می‌کند. به عنوان مثال:
   - **`index`**: این فایل شامل اطلاعات فایل‌هایی است که در مرحله آماده‌سازی قرار دارند.
   - **`objects/`**: این پوشه شامل شیء‌هایی است که نمایانگر اسنپ‌شات‌های مختلف از فایل‌های شما هستند.
4. **فایل‌های اصلاح‌شده یا جدید به ایندکس اضافه می‌شوند:** تغییرات فایل‌های جدید یا اصلاح‌شده در این مرحله ذخیره می‌شوند و آماده می‌شوند تا در کامیت بعدی به مخزن گیت اضافه شوند.

5. **مدیریت فایل‌های حذف‌شده:** اگر فایلی حذف شده باشد و شما از `git add` استفاده کنید، گیت این تغییر را نیز در ایندکس ثبت می‌کند و آماده است تا آن را در کامیت بعدی حذف کند.

### موارد استفاده از `git add`

- اضافه کردن تغییرات جدید یا اصلاح‌شده به مرحله آماده‌سازی.
- جمع‌آوری تغییرات مختلف برای یک کامیت تمیز و منظم.
- مدیریت فایل‌های جدید، تغییرات در فایل‌های موجود و حذف فایل‌ها قبل از ثبت در مخزن.

## ترفندها و نکات کاربردی دستور `git add`

### 1. اضافه کردن فایل‌های خاص با wildcard

می‌توانید از کاراکترهای wildcard برای اضافه کردن مجموعه‌ای از فایل‌ها با الگوی مشابه استفاده کنید. به عنوان مثال، اگر فقط بخواهید فایل‌های با پسوند `.js` را به مرحله آماده‌سازی اضافه کنید، می‌توانید از دستور زیر استفاده کنید:

```bash
git add *.js
```

این دستور تمام فایل‌های جاوااسکریپت موجود در دایرکتوری جاری را اضافه می‌کند.

### 2. اضافه کردن تغییرات بخشی از فایل‌ها (`git add -p`)

اگر فقط بخشی از تغییرات یک فایل را می‌خواهید به مرحله آماده‌سازی اضافه کنید، می‌توانید از گزینه `-p` استفاده کنید. این گزینه به شما اجازه می‌دهد تا تغییرات را به صورت تکه‌های (hunks) کوچک مشاهده کرده و انتخاب کنید که کدام یک به مرحله آماده‌سازی اضافه شوند:

```bash
git add -p
```

این قابلیت برای زمانی مفید است که نمی‌خواهید تمام تغییرات یک فایل در یک کامیت ثبت شوند.

### 3. اضافه کردن تمام فایل‌های تغییر یافته به مرحله آماده‌سازی

برای اضافه کردن تمام فایل‌های جدید، اصلاح‌شده و حذف‌شده به مرحله آماده‌سازی، می‌توانید از دستور زیر استفاده کنید:

```bash
git add .
```

این دستور تمام تغییرات در دایرکتوری جاری و زیرشاخه‌ها را به مرحله آماده‌سازی اضافه می‌کند.

### 4. اضافه کردن فایل‌ها از یک دایرکتوری خاص

اگر بخواهید فقط تغییرات در یک دایرکتوری خاص را به مرحله آماده‌سازی اضافه کنید، می‌توانید به‌طور مستقیم آن دایرکتوری را مشخص کنید:

```bash
git add <directory>/
```

به عنوان مثال، برای اضافه کردن تمام تغییرات در دایرکتوری `src`:

```bash
git add src/
```

### 5. افزودن فایل‌های حذف‌شده به کامیت بعدی

وقتی فایلی را حذف می‌کنید، برای اینکه این حذف در کامیت بعدی ثبت شود، باید از دستور `git add` استفاده کنید. گیت باید بداند که حذف فایل‌ها را نیز پیگیری کند:

```bash
git add -u
```

این دستور تمام فایل‌هایی که حذف شده‌اند و قبلاً تحت پیگیری گیت بودند را به مرحله آماده‌سازی اضافه می‌کند.

### 6. اضافه کردن فایل‌های جدید، بدون لمس فایل‌های حذف‌شده یا اصلاح‌شده

گاهی اوقات فقط می‌خواهید فایل‌های جدید را به مرحله آماده‌سازی اضافه کنید و تغییرات در فایل‌های موجود را نادیده بگیرید. برای این کار از گزینه `-N` استفاده کنید:

```bash
git add -N <filename>
```

این دستور فایل جدید را به مرحله آماده‌سازی اضافه می‌کند، بدون اینکه آن را در کامیت بعدی قرار دهد. این کار به گیت می‌گوید که فایل جدید را در نظر بگیرد اما هنوز به کامیت اضافه نکند.

### 7. بررسی سریع وضعیت پس از `git add`

برای اینکه ببینید چه فایل‌هایی به مرحله آماده‌سازی اضافه شده‌اند و آماده برای کامیت هستند، می‌توانید از دستور زیر استفاده کنید:

```bash
git status
```

این دستور فایل‌های آماده برای کامیت را نمایش می‌دهد و به شما اطمینان می‌دهد که کدام فایل‌ها در مرحله آماده‌سازی قرار دارند.

### 8. اضافه کردن تغییرات فایل‌های اصلاح‌شده بدون فایل‌های جدید

اگر فایل‌هایی اصلاح شده‌اند اما فایل جدیدی اضافه نکرده‌اید و فقط می‌خواهید تغییرات فایل‌های موجود را آماده کامیت کنید، می‌توانید از دستور `git add -u` استفاده کنید:

```bash
git add -u
```

این دستور فقط فایل‌هایی را که تغییر کرده‌اند (و قبلاً در مخزن بوده‌اند) به مرحله آماده‌سازی اضافه می‌کند و فایل‌های جدید را نادیده می‌گیرد.

### 9. استفاده از `git add -A` برای همگانی کردن تغییرات

اگر بخواهید هم فایل‌های جدید، هم فایل‌های اصلاح‌شده و هم فایل‌های حذف‌شده را به یک‌باره به مرحله آماده‌سازی اضافه کنید، از گزینه `-A` استفاده کنید:

```bash
git add -A
```

این دستور تمام تغییرات را در هر فایلی در دایرکتوری‌های شما به مرحله آماده‌سازی اضافه می‌کند.

### 10. استفاده از `git add .` و `git add -A` و تفاوت آن‌ها

- `git add .` فقط تغییرات در دایرکتوری جاری و زیرشاخه‌های آن را اضافه می‌کند، در حالی که تغییرات خارج از این دایرکتوری را نادیده می‌گیرد.
- `git add -A` تمام تغییرات در کل مخزن، از جمله فایل‌های خارج از دایرکتوری جاری را به مرحله آماده‌سازی اضافه می‌کند.

این تفاوت برای مدیریت بهتر پروژه‌های بزرگ و چندین دایرکتوری می‌تواند مفید باشد.