## راهنمای کامل و جامع برای دستور `git merge` در گیت (Git)

**دستور `git merge`** یکی از پرکاربردترین دستورات در گیت است که برای ادغام تغییرات شاخه‌های مختلف به کار می‌رود. این دستور به شما این امکان را می‌دهد که دو یا چند شاخه را با هم ترکیب کرده و تغییرات انجام شده در هر شاخه را در شاخه اصلی (معمولاً `main` یا `master`) یا یک شاخه دیگر ادغام کنید. از این دستور معمولاً برای ترکیب تغییرات شاخه‌های توسعه‌یافته‌ی جداگانه با شاخه اصلی استفاده می‌شود.

در این داکیومنت، توضیح خواهیم داد که چگونه از `git merge` استفاده کنید، چه اتفاقی در پس‌زمینه آن رخ می‌دهد و با استفاده از **Gitgraph در Mermaid** گراف‌هایی برای نمایش فرآیند ادغام ارائه می‌کنیم.

### دستور `git merge` چیست؟

دستور `git merge` برای ترکیب تغییرات شاخه‌ها استفاده می‌شود. زمانی که شما در شاخه‌ای کار کرده‌اید و می‌خواهید تغییرات آن را در شاخه دیگری اعمال کنید، از `git merge` استفاده می‌کنید. این دستور تغییرات هر دو شاخه را ترکیب می‌کند و به شما اجازه می‌دهد پروژه را با شاخه اصلی یا شاخه دیگری هماهنگ کنید.

#### نحوه استفاده از `git merge`:

```bash
git checkout <target-branch>
git merge <source-branch>
```

- **`target-branch`**: شاخه‌ای که می‌خواهید تغییرات را در آن ادغام کنید.
- **`source-branch`**: شاخه‌ای که تغییرات آن باید ادغام شود.

### چه اتفاقی در پس‌زمینه `git merge` می‌افتد؟

1. **مقایسه تغییرات**:

   - گیت تغییرات بین دو شاخه (شاخه مبدأ و شاخه مقصد) را مقایسه می‌کند و بررسی می‌کند که چه تغییراتی باید ادغام شوند.

2. **تولید یک کامیت ادغام (Merge Commit)**:

   - اگر در شاخه مقصد تغییراتی انجام شده باشد، گیت یک کامیت ادغام ایجاد می‌کند که نشان‌دهنده ترکیب تغییرات دو شاخه است. این کامیت ادغام شامل تمامی تغییرات هر دو شاخه می‌باشد و تاریخچه هر دو شاخه را با هم ترکیب می‌کند.

3. **حل تعارضات (Conflict Resolution)**:
   - اگر تغییرات ناسازگاری بین دو شاخه وجود داشته باشد، گیت قادر نخواهد بود به صورت خودکار آن‌ها را ادغام کند و شما باید به صورت دستی تعارضات را حل کنید. پس از حل تعارضات، باید تغییرات را کامیت کنید.

### انواع ادغام‌ها در `git merge`:

#### 1. **Fast-forward Merge**:

- اگر شاخه مقصد هیچ تغییری نداشته باشد و شاخه مبدأ مستقیماً از آن گرفته شده باشد، گیت می‌تواند شاخه مقصد را بدون ایجاد یک کامیت ادغام، به سادگی به جلو حرکت دهد. این نوع ادغام **fast-forward** نامیده می‌شود.

- **مثال**:
  اگر شما یک شاخه ویژگی جدید ایجاد کنید و فقط روی آن کار کنید بدون اینکه در شاخه اصلی تغییری ایجاد شود، ادغام به صورت **fast-forward** انجام می‌شود و فقط اشاره‌گر شاخه اصلی به جلو حرکت می‌کند.

#### 2. **Three-way Merge**:

- اگر هر دو شاخه تغییراتی داشته باشند، گیت از یک روش **three-way merge** استفاده می‌کند. در این حالت، گیت سه نسخه از تاریخچه را بررسی می‌کند:
  1.  **نسخه شاخه مبدأ**
  2.  **نسخه شاخه مقصد**
  3.  **کامیت مشترک اصلی (ancestor commit)**
- گیت سپس این سه نسخه را با هم مقایسه می‌کند و تغییرات را ادغام می‌کند.

### نمایش گراف با Gitgraph در Mermaid

#### مثال ۱: **Fast-forward Merge**

##### قبل از `git merge`:

```mermaid
gitGraph
   commit id: "Initial Commit"
   branch main
   commit id: "Add feature X"
   branch feature-branch
   commit id: "Work on feature-branch"
```

##### بعد از `git merge` (Fast-forward):

```mermaid
gitGraph
   commit id: "Initial Commit"
   branch main
   commit id: "Add feature X"
   commit id: "Work on feature-branch"
```

#### توضیح:

- در اینجا، شاخه `feature-branch` از `main` گرفته شده است و چون هیچ تغییری در `main` رخ نداده، ادغام به صورت **fast-forward** انجام می‌شود و فقط اشاره‌گر `main` به جلو حرکت می‌کند.

#### مثال ۲: **Three-way Merge**

##### قبل از `git merge`:

```mermaid
gitGraph
   commit id: "Initial Commit"
   branch main
   commit id: "Add feature A"
   commit id: "Fix bug in main"
   branch feature-branch
   commit id: "Work on feature-branch"
   commit id: "Improve feature-branch"
```

##### بعد از `git merge` (Three-way Merge):

```mermaid
gitGraph
   commit id: "Initial Commit"
   branch main
   commit id: "Add feature A"
   commit id: "Fix bug in main"
   checkout main
   commit id: "Merge feature-branch"
   commit id: "Work on feature-branch"
   commit id: "Improve feature-branch"
```

#### توضیح:

- در اینجا شاخه `main` تغییراتی داشته است (اضافه شدن یک ویژگی و رفع باگ) و همچنین شاخه `feature-branch` نیز تغییرات خود را دارد. بنابراین، گیت یک **three-way merge** انجام می‌دهد و یک کامیت ادغام ایجاد می‌کند که تغییرات هر دو شاخه را در خود جای می‌دهد.

### مراحل استفاده از `git merge`:

#### 1. جابه‌جایی به شاخه مقصد:

ابتدا به شاخه‌ای که می‌خواهید تغییرات را در آن ادغام کنید بروید. برای مثال، شاخه اصلی (`main`):

```bash
git checkout main
```

#### 2. اجرای دستور `git merge`:

سپس دستور `git merge` را اجرا کنید تا تغییرات شاخه دیگر (مثلاً `feature-branch`) در شاخه فعلی ادغام شود:

```bash
git merge feature-branch
```

#### 3. حل تعارضات (در صورت وجود):

اگر گیت در طول فرآیند ادغام به تعارضی برخورد کند، آن را به شما گزارش می‌دهد. شما باید این تعارضات را به صورت دستی حل کنید. پس از حل تعارضات، تغییرات را به شاخه اضافه کرده و ادامه دهید:

```bash
git add <file>
git merge --continue
```

### موارد استفاده از `git merge`:

1. **ادغام تغییرات شاخه‌های ویژگی (Feature Branches)**:

   - زمانی که شما یک شاخه جدید برای توسعه یک ویژگی ایجاد کرده‌اید و می‌خواهید پس از اتمام کار آن را در شاخه اصلی ادغام کنید، `git merge` راهکار مناسبی است. این کار تغییرات شما را با شاخه اصلی هماهنگ می‌کند.

2. **ادغام شاخه‌های توسعه موازی**:

   - وقتی دو یا چند توسعه‌دهنده به طور همزمان روی شاخه‌های جداگانه کار می‌کنند، `git merge` به شما کمک می‌کند که تغییرات آن‌ها را با هم ترکیب کنید.

3. **ادغام پس از رفع باگ‌ها**:
   - اگر یک شاخه مجزا برای رفع باگ‌ها دارید، می‌توانید پس از رفع مشکل، تغییرات را با استفاده از `git merge` در شاخه اصلی ادغام کنید.

### مزایا و معایب `git merge`:

#### مزایا:

- **حفظ تاریخچه شاخه‌ها**: با استفاده از `git merge`، شما تاریخچه تغییرات هر دو شاخه را حفظ می‌کنید.
- **پشتیبانی از ادغام‌های پیچیده**: `git merge` از ادغام‌های پیچیده و چند مرحله‌ای با استفاده از سه نسخه مختلف (three-way merge) پشتیبانی می‌کند.
- **ادغام ساده در صورت عدم تعارض**: در صورتی که هیچ تعارضی وجود نداشته باشد، ادغام به سرعت و به راحتی انجام می‌شود.

#### معایب:

- **ایجاد کامیت ادغام**: در صورتی که تغییرات زیادی وجود داشته باشد، `git merge` ممکن است یک کامیت ادغام اضافی ایجاد کند که ممکن است تاریخچه گیت را پیچیده‌تر کند.
- **نیاز به حل تعارضات به صورت دستی**: در صورت بروز تعارضات، شما باید به صورت دستی آن‌ها را حل کنید که ممکن است زمان‌بر باشد.

### جمع‌بندی:

دستور **`git merge`** یکی از قدرتمندترین ابزارهای گیت است که به شما اجازه می‌دهد شاخه‌های مختلف پروژه را با هم ادغام کرده و تغییرات آن‌ها را ترکیب کنید. این دستور با ایجاد یک کامیت ادغام، تاریخچه پروژه را به گونه‌ای حفظ می‌کند که تمام تغییرات هر دو شاخه قابل پیگیری و بازیابی باشند.
