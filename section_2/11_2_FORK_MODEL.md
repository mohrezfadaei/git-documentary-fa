## مدل فورک (Fork Model)

### مدل **Fork** در توسعه گیت چیست؟

**Fork Model** یا **مدل فورک** در توسعه گیت به روشی اشاره دارد که در آن توسعه‌دهندگان به جای اینکه مستقیماً در یک مخزن (repository) اصلی مشارکت کنند، ابتدا یک کپی کامل از مخزن را به حساب کاربری خود (معمولاً در GitHub، GitLab یا سایر پلتفرم‌های مشابه) فورک می‌کنند. سپس تغییرات خود را در نسخه فورک شده انجام می‌دهند و در نهایت، برای ادغام این تغییرات در مخزن اصلی درخواست ارسال می‌کنند.

این روش به ویژه در پروژه‌های **منبع‌باز** (Open Source) یا پروژه‌هایی که توسعه‌دهندگان مختلف روی آن کار می‌کنند بسیار مفید است، زیرا به توسعه‌دهندگان اجازه می‌دهد بدون دسترسی مستقیم به مخزن اصلی، روی ویژگی‌های جدید یا رفع مشکلات کار کنند.

## مراحل کار در مدل **Fork**:

1. **فورک کردن مخزن اصلی (Fork the Repository):**

   - اولین قدم این است که توسعه‌دهنده یک **فورک** از مخزن اصلی ایجاد کند. فورک در واقع یک کپی کامل از پروژه است که به مخزن اصلی وابسته نیست و به حساب کاربری توسعه‌دهنده منتقل می‌شود.
   - این فرآیند معمولاً از طریق پلتفرم‌هایی مانند GitHub یا GitLab به سادگی با یک کلیک انجام می‌شود.
   - مثال:
     - شما در مخزن اصلی **project-a** مشارکت می‌کنید، اما ابتدا آن را فورک می‌کنید و به نسخه **your-username/project-a** در حساب کاربری خودتان تبدیل می‌کنید.

2. **کلون کردن مخزن فورک‌شده (Clone the Forked Repository):**

   - بعد از فورک کردن، شما نیاز دارید که مخزن فورک‌شده را به صورت محلی روی سیستم خود **clone** کنید.
   - دستور:
     ```bash
     git clone https://github.com/your-username/project-a.git
     ```
   - این دستور یک نسخه محلی از مخزن فورک‌شده را روی سیستم شما ایجاد می‌کند.

3. **ایجاد یک شاخه (Branch) برای تغییرات:**

   - بعد از کلون کردن، شما باید یک شاخه جدید ایجاد کنید که تغییرات مورد نظر خود را در آن انجام دهید.
   - دستور:
     ```bash
     git checkout -b feature-branch
     ```
   - این شاخه می‌تواند برای رفع یک باگ، اضافه کردن یک ویژگی جدید، یا انجام هر گونه تغییر دیگری باشد.

4. **اعمال تغییرات و کامیت کردن (Commit the Changes):**

   - حالا می‌توانید تغییرات مورد نظر را در کد اعمال کنید و سپس آن‌ها را کامیت کنید.
   - دستور:
     ```bash
     git add .
     git commit -m "Add new feature or fix bug"
     ```

5. **پوش (Push) تغییرات به مخزن فورک‌شده:**

   - پس از کامیت تغییرات، باید آن‌ها را به مخزن فورک‌شده روی GitHub یا GitLab پوش کنید.
   - دستور:
     ```bash
     git push origin feature-branch
     ```

6. **ارسال درخواست کشیدن (Pull Request):**
   - پس از پوش تغییرات به مخزن فورک‌شده، به GitHub یا GitLab بروید و یک **Pull Request** ارسال کنید. در این درخواست، از مالک مخزن اصلی درخواست می‌کنید که تغییرات شما را بازبینی کرده و در صورت تأیید، آن‌ها را در مخزن اصلی ادغام کند.
   - در این مرحله، توسعه‌دهندگان مخزن اصلی تغییرات را بررسی می‌کنند و در صورت تأیید، آن‌ها را در پروژه اصلی ادغام می‌کنند.

## مزایای استفاده از **Fork Model**:

1. **استقلال توسعه‌دهنده:** توسعه‌دهندگان بدون نیاز به داشتن دسترسی مستقیم به مخزن اصلی می‌توانند روی نسخه فورک‌شده کار کنند. این استقلال به خصوص در پروژه‌های منبع‌باز بسیار حیاتی است.
2. **امنیت بیشتر:** مدیران پروژه اصلی نیازی به نگرانی در مورد تغییرات مستقیم افراد دیگر در مخزن اصلی ندارند. تغییرات ابتدا در فورک انجام شده و پس از بررسی و تأیید ادغام می‌شوند.
3. **مشارکت آسان‌تر در پروژه‌های منبع‌باز:** مدل فورک به توسعه‌دهندگان از سراسر جهان این امکان را می‌دهد که به پروژه‌های مختلف بدون نیاز به دسترسی نوشتاری به مخزن اصلی کمک کنند.
4. **تفکیک وظایف:** هر توسعه‌دهنده می‌تواند به صورت مستقل روی شاخه خود کار کند، بدون اینکه شاخه‌های دیگر توسعه‌دهندگان را تحت تأثیر قرار دهد.

## معایب **Fork Model**:

1. **هماهنگ‌سازی مشکل‌تر:** از آنجایی که هر توسعه‌دهنده یک نسخه جداگانه از مخزن اصلی دارد، ممکن است همگام‌سازی نسخه‌های فورک‌شده با مخزن اصلی مشکل‌تر شود. توسعه‌دهنده باید به صورت منظم تغییرات مخزن اصلی را با مخزن فورک‌شده خود همگام کند.
2. **مدیریت بیشتر:** برای پروژه‌های بزرگ، نگه‌داری از فورک‌ها و بازبینی مداوم Pull Request‌ها زمان‌بر و نیازمند مدیریت دقیق است.
3. **حجم داده بیشتر:** فورک کردن یک مخزن به معنای ایجاد یک کپی کامل از پروژه است، که می‌تواند به افزایش حجم داده‌های پروژه منجر شود.

## شیوه‌های پیشنهادی (Best Practices) در **Fork Model**:

1. **همگام‌سازی مرتب با مخزن اصلی:**

   - تغییرات جدیدی که در مخزن اصلی رخ می‌دهد را به‌طور مرتب به مخزن فورک‌شده خود **pull** کنید تا همیشه مخزن شما به‌روز باشد.
   - دستور برای اضافه کردن **remote** مخزن اصلی:
     ```bash
     git remote add upstream https://github.com/original-owner/project-a.git
     ```
   - برای همگام‌سازی:
     ```bash
     git fetch upstream
     git checkout main
     git merge upstream/main
     ```

2. **شاخه‌بندی برای هر تغییر:** برای هر ویژگی جدید یا رفع باگ، یک شاخه مجزا ایجاد کنید و تغییرات مربوط به آن را در همان شاخه نگه دارید. این کار به مدیریت آسان‌تر تغییرات و Pull Request‌ها کمک می‌کند.

3. **نوشتن توضیحات دقیق برای Pull Request:** همیشه توضیحات دقیق و شفاف برای Pull Request خود بنویسید تا توسعه‌دهندگان مخزن اصلی به خوبی تغییرات شما را درک کنند.

4. **انجام تست‌های لازم:** قبل از ارسال Pull Request، مطمئن شوید که کد شما به درستی کار می‌کند و تست‌های لازم را گذرانده است. این کار شانس پذیرش تغییرات شما را افزایش می‌دهد.

### نتیجه‌گیری:

**Fork Model** در گیت یکی از بهترین و رایج‌ترین روش‌ها برای توسعه نرم‌افزار، به ویژه در پروژه‌های منبع‌باز، است. این مدل توسعه‌دهندگان را قادر می‌سازد که به صورت مستقل تغییرات خود را در پروژه اعمال کنند و سپس از طریق Pull Request، آن‌ها را برای ادغام به مخزن اصلی ارسال کنند. با استفاده از شیوه‌های پیشنهادی مانند همگام‌سازی مرتب و استفاده از شاخه‌های مجزا، می‌توان به کارایی بالایی در این مدل دست یافت.