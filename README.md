# SE Lab HW1 - Static Frontend

<div dir="rtl">

پروژه آزمایشگاه مهندسی نرم‌افزار - تمرین اول

## درباره پروژه

یک وب‌سایت استاتیک (Static Frontend) با **HTML، CSS و JavaScript خالص** (بدون فریم‌ورک) پیاده‌سازی شده است. این پروژه شامل منوی ناوبری، بخش‌های Hero، About، Projects، Contact Form و Footer می‌باشد.


**آدرس GitHub Pages:** [https://m-amin-a.github.io/SE_lab_HW1/](https://m-amin-a.github.io/SE_lab_HW1/)

---

## گزارش پیاده‌سازی

### تکنولوژی‌های استفاده‌شده

| تکنولوژی | کاربرد |
|----------|--------|
| HTML5 | ساختار صفحات |
| CSS3 | استایل‌دهی، Flexbox، Grid، Animation |
| JavaScript (Vanilla) | Smooth Scroll، Active Nav، Contact Form |
| Git & GitHub | مدیریت نسخه و همکاری |
| GitHub Actions | استقرار خودکار (CI/CD) |
| GitHub Pages | میزبانی سایت استاتیک |

---

### شاخه‌ها (Branches)

در این پروژه از **۵ شاخه** با اهداف مشخص استفاده شده است:

| شاخه | هدف | وضعیت |
|------|-----|-------|
| `main` | شاخه اصلی (Production) — محافظت‌شده، فقط merge از طریق PR | فعال |
| `dev` | شاخه توسعه — ادغام featureها قبل از release | فعال |
| `feature/navigation` | پیاده‌سازی منوی ناوبری و JavaScript | merge شده در `dev` |
| `feature/projects` | پیاده‌سازی بخش پروژه‌ها، فرم تماس و footer | merge شده در `dev` |
| `hotfix/fix-contact-placeholder` | رفع باگ placeholder ایمیل در فرم تماس | merge شده در `dev` |

#### نمودار جریان شاخه‌ها

<div dir="ltr">

```
main ─────────────────────────────────────────────► (via PR from dev)
  │
  └── dev ──┬── feature/navigation ──► merge (conflict #1)
            ├── feature/projects ────► merge (conflict #2)
            └── hotfix/fix-contact-placeholder ──► fast-forward merge
```

</div>

---

### تاریخچه Commitها (۲۲ commit)

| # | Hash | پیام Commit | شاخه | توضیح |
|---|------|-------------|------|-------|
| 1 | `f73954a` | `chore: add .gitignore for Node, IDE and OS files` | main | افزودن `.gitignore` |
| 2 | `e8f4e9d` | `docs: add initial README with project description` | main | README اولیه |
| 3 | `72a9685` | `feat: add basic HTML skeleton with RTL support` | main | ساختار HTML پایه |
| 4 | `8991304` | `style: add CSS reset for consistent cross-browser styling` | main | CSS Reset |
| 5 | `492fbb4` | `style: add base styles with CSS custom properties` | main | متغیرهای CSS |
| 6 | `544ab58` | `feat: link stylesheets and add header structure` | main | اتصال CSS و Header |
| 7 | `d19f49c` | `style: add header and hero section styles` | dev | استایل Header و Hero |
| 8 | `da4c9f6` | `feat: add about section with description text` | feature/navigation | بخش About |
| 9 | `c829fc5` | `feat: add navigation menu with links to sections` | feature/navigation | منوی ناوبری |
| 10 | `2a210e9` | `feat: add smooth scroll and active nav link highlighting` | feature/navigation | JavaScript ناوبری |
| 11 | `af03531` | `feat(dev): customize hero title and about section content` | dev | تغییرات dev برای conflict |
| 12 | `a032875` | `merge: resolve conflict between dev and feature/navigation in index.html` | dev | **Conflict #1** — header و hero |
| 13 | `14d5210` | `feat: add projects section with card grid layout` | feature/projects | بخش Projects |
| 14 | `5002d01` | `feat: add contact form and footer section` | feature/projects | فرم تماس و Footer |
| 15 | `f6ba052` | `feat(dev): add preliminary footer section` | dev | Footer اولیه dev |
| 16 | `f4859a3` | `merge: resolve conflicts in footer styles and index.html` | dev | **Conflict #2** — footer |
| 17 | `84b0a52` | `ci: add GitHub Actions workflow for Pages deployment` | dev | Workflow استقرار |
| 18 | `b2289ac` | `chore: add .nojekyll for GitHub Pages static hosting` | dev | فایل `.nojekyll` |
| 19 | `27eadaa` | `fix: correct email placeholder format in contact form` | hotfix | رفع placeholder |
| 20 | `7aea900` | `style: add fade-in animation to hero section` | dev | انیمیشن Hero |
| 21 | `4ad6c4b` | `docs: add implementation report with branches, commits and conflicts` | dev | گزارش کامل |
| 22 | `8ee4c9b` | `docs: update commit hash in README report table` | dev | به‌روزرسانی hash |

---

### دستورات Git استفاده‌شده

در طول پیاده‌سازی، دستورات زیر به‌صورت دستی در ترمینال اجرا شدند:

#### ۱. راه‌اندازی اولیه مخزن

<div dir="ltr">

```bash
# اتصال مخزن محلی به remote روی GitHub
git remote add origin https://github.com/M-Amin-A/SE_lab_HW1

# مشاهده وضعیت فایل‌ها (tracked / untracked / modified)
git status
```

</div>

#### ۲. Stage و Commit

<div dir="ltr">

```bash
# افزودن فایل مشخص به staging area
git add .gitignore
git add index.html css/styles.css

# ثبت تغییرات با پیام معنادار
git commit -m "chore: add .gitignore for Node, IDE and OS files"
git commit -m "feat: add basic HTML skeleton with RTL support"
```

</div>


**توضیح:** هر commit یک تغییر مشخص در فرآیند توسعه را ثبت می‌کند (مثلاً افزودن feature، رفع باگ، یا به‌روزرسانی مستندات).

#### ۳. کار با شاخه‌ها (Branch)

<div dir="ltr">

```bash
# ایجاد و جابجایی به شاخه dev
git checkout -b dev

# ایجاد شاخه feature برای توسعه یک قابلیت
git checkout -b feature/navigation
git checkout -b feature/projects

# ایجاد شاخه hotfix برای رفع باگ
git checkout -b hotfix/fix-contact-placeholder

# بازگشت به شاخه dev
git checkout dev

# مشاهده لیست شاخه‌ها
git branch -v
```

</div>

**توضیح:**
- شاخه `dev` — شاخه توسعه اصلی
- شاخه `feature/*` — هر feature در شاخه جداگانه
- شاخه `hotfix/*` — رفع سریع باگ بدون انتظار برای release بعدی

#### ۴. ادغام (Merge)

<div dir="ltr">

```bash
# ادغام feature/navigation در dev
git checkout dev
git merge feature/navigation -m "merge: integrate navigation feature into dev"

# ادغام feature/projects در dev
git merge feature/projects -m "merge: integrate projects and contact features into dev"

# ادغام hotfix در dev (fast-forward)
git merge hotfix/fix-contact-placeholder -m "merge: apply hotfix for contact form placeholder"
```

</div>


**توضیح:** merge تغییرات یک شاخه را در شاخه فعلی ادغام می‌کند. در صورت تداخل، Git conflict ایجاد می‌کند.

#### ۵. رفع Conflict

<div dir="ltr">

```bash
# هنگام merge، Git conflict را گزارش می‌دهد:
# CONFLICT (content): Merge conflict in index.html

# پس از ویرایش دستی فایل‌های conflict‌دار:
git add index.html css/styles.css
git commit -m "merge: resolve conflict between dev and feature/navigation in index.html"
```

</div>

**توضیح:** markerهای `<<<<<<<`، `=======`، `>>>>>>>` در فایل نشان‌دهنده conflict هستند. پس از انتخاب نسخه نهایی، فایل را add و commit کنید.

#### ۶. مشاهده تاریخچه

<div dir="ltr">

```bash
# لیخت commitها
git log --oneline

# تاریخچه همه شاخه‌ها
git log --oneline --all --graph

# مشاهده diff تغییرات
git diff
```

</div>

#### ۷. Push به GitHub

<div dir="ltr">

```bash
# ارسال شاخه dev به remote
git push -u origin dev

# ارسال همه شاخه‌ها
git push -u origin main dev feature/navigation feature/projects hotfix/fix-contact-placeholder
```

</div>


**توضیح:** `-u` (یا `--set-upstream`) ارتباط شاخه محلی با remote را برقرار می‌کند.

#### ۸. Pull Request (روی GitHub)

ادغام با `main` فقط از طریق Pull Request انجام می‌شود:

<div dir="ltr">

```bash
# پس از push شاخه dev:
# 1. به github.com/M-Amin-A/SE_lab_HW1 بروید
# 2. Pull requests → New pull request
# 3. base: main ← compare: dev
# 4. Create pull request → Merge pull request
```

</div>

---

### Conflictها

#### Conflict #1 — ادغام `feature/navigation` در `dev`

- **فایل:** `index.html`
- **علت:** هر دو شاخه همزمان `header__brand` و محتوای `hero`/`about` را تغییر داده بودند.
- **راه‌حل:** نگه‌داشتن منوی ناوبری از feature branch، عنوان hero از dev، و ادغام متن about از هر دو شاخه.

#### Conflict #2 — ادغام `feature/projects` در `dev`

- **فایل‌ها:** `index.html`، `css/styles.css`
- **علت:** dev یک footer ساده اضافه کرده بود؛ feature/projects بخش contact، projects و footer کامل داشت.
- **راه‌حل:** نگه‌داشتن contact و projects از feature، و footer نهایی از feature/projects با استایل یکپارچه.

---

### GitHub Actions — استقرار خودکار (Deploy)

#### نحوه کار

فایل `.github/workflows/deploy.yml` workflow استقرار را تعریف می‌کند. با هر **push به شاخه `main`**، GitHub Actions به‌صورت خودکار اجرا می‌شود:

<div dir="ltr">

```
Push to main  →  GitHub Actions Trigger  →  Build  →  Deploy  →  GitHub Pages
```

</div>


#### مراحل Workflow

| مرحله | Action | توضیح |
|-------|--------|-------|
| 1 | `actions/checkout@v4` | دریافت کد از مخزن |
| 2 | `actions/configure-pages@v5` | پیکربندی GitHub Pages |
| 3 | `actions/upload-pages-artifact@v3` | آپلود فایل‌های استاتیک (HTML, CSS, JS) |
| 4 | `actions/deploy-pages@v4` | استقرار روی GitHub Pages |

#### Trigger

<div dir="ltr">

```yaml
on:
  push:
    branches: [main]    # فقط push به main
  workflow_dispatch:    # اجرای دستی از تب Actions
```

</div>


#### پیش‌نیازهای فعال‌سازی Deploy

1. انجام **Push شاخه `dev` به `main`** (از طریق Pull Request)
2. رفتن به **Settings → Pages → Source:** انتخاب **GitHub Actions**
3. رفتن به **Settings → Actions → General:** اجازه اجرای workflow

#### فایل `.nojekyll`

این فایل خالی در root پروژه قرار دارد تا GitHub Pages از Jekyll برای پردازش فایل‌ها استفاده نکند و فایل‌های استاتیک مستقیماً serve شوند.

#### آدرس سایت

پس از deploy موفق:

| محیط | URL |
|------|-----|
| GitHub Pages | [https://m-amin-a.github.io/SE_lab_HW1/](https://m-amin-a.github.io/SE_lab_HW1/) |

#### بررسی وضعیت Deploy

<div dir="ltr">

```bash
# در GitHub:
# Repository → Actions → Deploy to GitHub Pages → آخرین run

# یا:
# Repository → Settings → Pages → آدرس سایت و وضعیت deployment
```

</div>

#### اجرای دستی Deploy

1. به تب **Actions** در مخزن بروید
2. workflow **Deploy to GitHub Pages** را انتخاب کنید
3. **Run workflow** → branch: `main` → **Run workflow**

---

### محافظت از شاخه `main`

Branch Protection Rule روی GitHub:

- Require a pull request before merging
- Restrict direct pushes to `main`

**مسیر:** Repository → Settings → Branches → Add branch protection rule → Branch name: `main`

---

### Pull Requestها

| PR | From → To | توضیح |
|----|-----------|-------|
| PR #1 | `feature/navigation` → `dev` | ادغام منوی ناوبری (با conflict) |
| PR #2 | `feature/projects` → `dev` | ادغام projects و contact (با conflict) |
| PR #3 | `hotfix/fix-contact-placeholder` → `dev` | اعمال hotfix |
| PR #4 | `dev` → `main` | Release نهایی و فعال‌سازی GitHub Pages |

---

### ساختار پروژه

<div dir="ltr">

```
SE_lab_HW1/
├── .github/
│   └── workflows/
│       └── deploy.yml      # GitHub Actions CI/CD
├── css/
│   ├── reset.css           # CSS Reset
│   └── styles.css          # استایل‌های اصلی
├── js/
│   └── main.js             # JavaScript
├── index.html              # صفحه اصلی
├── .gitignore
├── .nojekyll               # غیرفعال کردن Jekyll در Pages
└── README.md
```

</div>

---

### اجرای محلی

فایل `index.html` را در مرورگر باز کنید، یا:

<div dir="ltr">

```bash
# با Python
python -m http.server 8080

# با Node.js
npx serve .
```

</div>

---


## پاسخ سوالات

### ۱. پوشه‌ی `.git` چیست، چه اطلاعاتی در آن ذخیره می‌شود و با چه دستوری ساخته می‌شود؟

* **پوشه‌ی `.git` چیست؟** این پوشه قلب تپنده‌ی گیت است؛ یک دایرکتوری مخفی که در ریشه‌ی پروژه‌ی شما قرار دارد و تمام تاریخچه، تنظیمات، شاخه‌ها (Branches)، تگ‌ها و اطلاعات مربوط به نسخه‌های پروژه را در خود نگه می‌دارد. گیت تمام اطلاعات لازم برای مدیریت سورس‌کد را در این پوشه متمرکز کرده است.
* **چه اطلاعاتی در آن ذخیره می‌شود؟**
* **پوشه‌ی `objects`:** پایگاه داده‌ی محتوای فایل‌ها و کامیت‌ها (به‌صورت اشیاء فشرده و هش‌شده).
* **پوشه‌ی `refs`:** اشاره‌گرها به شاخه‌ها (Branches)، تگ‌ها و ریموت‌ها (مانند `refs/heads/main`).
* **فایل `HEAD`:** نشان می‌دهد که در حال حاضر روی چه شاخه‌ای (Branch) قرار دارید.
* **فایل `config`:** تنظیمات اختصاصی مخزن (مانند اطلاعات ریموت‌ها و کانفیگ‌های محلی).
* **فایل `index` (یا staging area):** اطلاعات مربوط به فایل‌هایی که آماده‌ی کامیت شدن هستند.


* **با چه دستوری ساخته می‌شود؟** با دستور زیر در ریشه‌ی پروژه ساخته می‌شود:
```bash
git init

```



---

### ۲. منظور از Atomic بودن در Atomic Commit و Atomic Pull-Request چیست؟

مفهوم **Atomic (اتمیک یا تجزیه‌ناپذیر)** به این معناست که یک تغییر یا مجموعه‌ای از تغییرات، **باید یک واحد کامل و مستقل از کار را انجام دهند**؛ یعنی یا به‌طور کامل اعمال شوند، یا اصلاً اعمال نشوند. هیچ‌وقت نباید یک تغییر ناقص یا بی‌ارتباط با بقیه را شامل شود.

* مفهوم **Atomic Commit:** یعنی هر کامیت فقط شامل تغییراتی باشد که به یک هدف واحد مربوط می‌شوند (مثلاً رفع یک باگ خاص یا افزودن یک ویژگی کوچک). نباید اصلاح چند باگِ مجزا یا ویژگی‌های نامربوط را در یک کامیت قرار داد تا در صورت نیاز بتوان به‌راحتی آن را عیب‌یابی (Debug) یا ریسِت کرد.
* مفهوم **Atomic Pull-Request (PR):** یعنی یک پول‌ریکوئست باید روی یک موضوع یا وظیفه‌ی مشخص تمرکز داشته باشد و اندازه‌اش معقول باشد (نه خیلی بزرگ). بررسی و تایید PRهای اتمیک برای تیم بسیار ساده‌تر و کم‌خطاتر است.

---

### ۳. تفاوت دستورهای fetch، pull، merge، rebase و cherry-pick

* دستور **`git fetch`:** آخرین تغییرات را از مخزن ریموت (Remote) دریافت می‌کند، اما آن‌ها را با شاخه‌ی محلی شما ترکیب (Merge) نمی‌کند. این دستور امن‌ترین راه برای دیدن کارهای دیگران است.
* دستور **`git pull`:** ترکیبی از دو دستور `git fetch` و سپس `git merge` (یا `git rebase` اگر تنظیم شده باشد) است. تغییرات را از ریموت دانلود کرده و بلافاصله روی شاخه‌ی فعلی شما اعمال می‌کند.
* دستور **`git merge`:** تاریخچه‌ی دو شاخه را با هم ترکیب می‌کند. این کار با ساختن یک **کامیتِ تجمیعی (Merge Commit)** جدید انجام می‌شود که تاریخچه‌ی انشعاب‌ها را حفظ می‌کند.
* دستور **`git rebase`:** تغییرات شاخه‌ی فعلی شما را برداشته و آن‌ها را روی سرِ شاخه‌ی دیگری بازپخش (Replay) می‌کند. این کار تاریخچه‌ی پروژه را به شکلی **خطی و تمیز** درمی‌آورد و از کامیت‌های اضافیِ merge جلوگیری می‌کند.
* دستور **`git cherry-pick`:** به شما اجازه می‌دهد یک کامیت مشخص (با هشِ آن) را از یک شاخه انتخاب کرده و دقیقاً همان تغییرات را روی شاخه‌ی فعلی خود اعمال کنید.

---

### ۴. تفاوت دستورهای reset، revert، restore، switch و checkout

* دستور **`git reset`:** شاخه‌ی فعلی را به عقب برمی‌گرداند. این دستور می‌تواند فضای استیج، ایندکس و کامیت‌ها را تغییر دهد (مثلاً با پارامترهای `--soft` یا `--hard`). این کار تاریخچه را بازنویسی می‌کند و برای تغییرات محلی استفاده می‌شود.
* دستور **`git revert`:** یک کامیتِ **جدید** می‌سازد که دقیقا اثرات منفیِ یک کامیتِ قبلی را خنثی (معکوس) می‌کند. برخلاف reset، تاریخچه را دست‌نخورده نگه می‌دارد و برای کارهایی که روی ریموت پوش شده‌اند امن است.
* دستور **`git restore`:** برای بازگرداندن فایل‌های کاری (Working Directory) یا پاک کردن تغییراتِ اِستینج‌نشده به حالت قبل استفاده می‌شود (جایگزین مدرن‌تر برای برخی کاربردهای قدیمی checkout).
* دستور **`git switch`:** دستور مدرن و اختصاصی برای جابه‌جایی بین شاخه‌ها (Branches) یا ساخت شاخه‌ی جدید (`-c`) است.
* دستور **`git checkout`:** دستوری قدیمی و همه‌کاره است که کارهای مختلفی انجام می‌دهد: جابه‌جایی بین شاخه‌ها، سوئیچ به کامیت‌های قدیمی، یا بازیابی فایل‌ها. امروزه توصیه می‌شود به جای آن از `git switch` و `git restore` استفاده شود.

---

### ۵. منظور از Stage یا همان Index چیست؟ دستور stash چه کاری را انجام می‌دهد؟

* مفهوم **Stage (یا Index):** فضایی میانی در گیت است که فایل‌های تغییریافته قبل از اینکه در قالب یک کامیتِ دائمی ثبت شوند، در آن قرار می‌گیرند. این فضا به شما اجازه می‌دهد دقیقا انتخاب کنید چه بخش‌هایی از کدهایتان آماده‌ی ثبت هستند (`git add`).
* **دستور `git stash`:** تغییراتی را که هنوز کامیت نکرده‌اید (چه در Working Directory و چه در Stage) موقتاً در یک انبار ذخیره می‌کند و فضای کاری شما را پاک‌سازی و تمیز تحویل می‌دهد. این کار زمانی مفید است که باید فوراً به شاخه‌ی دیگری بروید تا باگی را اصلاح کنید، بدون اینکه بخواهید کارهای نصفه‌نیمه‌ی فعلی را کامیت کنید. بعداً با `git stash pop` می‌توانید تغییرات را برگردانید.

---

### ۶. مفهوم Snapshot به چه معناست؟ ارتباط آن با commit چیست؟

* تصویر لحظه‌ای **Snapshot:** برخلاف سیستم‌های کنترل نسخه‌ی قدیمی که تغییراتِ خط به خط فایل‌ها (Deltas) را ذخیره می‌کردند، گیت وضعیت کل پروژه‌ی شما را در هر لحظه مانند یک عکسِ اسکن‌شده (Snapshot) ثبت می‌کند. اگر فایلی تغییر نکرده باشد، گیت فایل جدیدی نمی‌سازد بلکه تنها یک لینک (Reference) به فایل قبلی نگه می‌دارد.
* **ارتباط با Commit:** هر **Commit** در واقع یک Snapshot از کل پروژه به همراه متادیتایی مثل نویسنده، تاریخ و پیام کامیت است. وقتی کامیت می‌کنید، گیت یک تصویر لحظه‌ای جدید از وضعیتِ فایل‌های استیج‌شده ایجاد می‌کند و آن را به تاریخچه پیوند می‌زند.

---

### ۷. تفاوت‌های Local Repository و Remote Repository

| ویژگی | Local Repository (مخزن محلی) | Remote Repository (مخزن ریموت) |
| --- | --- | --- |
| **محل ذخیره‌سازی** | روی هارد دیسک و سیستم کامپیوتر شخصی شما. | روی یک سرور ابری یا شبکه‌ای (مثل GitHub، GitLab یا Bitbucket). |
| **دسترسی آفلاین** | کاملاً مستقل است و برای کار با آن نیازی به اینترنت ندارید. | برای دسترسی به آن نیازمند اتصال به اینترنت هستید. |
| **اشتراک‌گذاری** | تغییرات فقط برای خودِ شما قابل مشاهده است تا زمانی که Push کنید. | نقطه‌ی مرکزی برای اشتراک‌گذاری کدها بین اعضای تیم است. |
| **دستورات اصلی** | `add`, `commit`, `status`, `log` | `push`, `pull`, `fetch`, `clone` |


## استفاده از هوش مصنوعی

در این تمرین برای پیاده‌سازی و انجام commit ها از ابزار cursor و مدل Composer 2.5 Fast استفاده شده است.
دسترسی به این مدل از طریق ظرفیت رایگان اکانت cursor امکان پذیر بود.
پرامپت ورودی داده شده توضیح متنی پروژه در کوئرا بوده و خروجی آن عموما تغییرات مستقیم روی فایل ها بود. متن کامل پرامپت ها و پاسخ هوش مصنوعی در فایل 
cursor_static_frontend_deployment_proje.md
ضممیه شده است.

برای پاسخ به سوالات پروژه، از هوش مصنوعی 
Gemini 3.6 Flash
با دسترسی رایگان استفاده شد. پرامپت داده شده کپی مستقیم سوالات بود و خروجی در بخش پاسخ سوالات آورده شده است.

## نویسنده

محمدامین عباس فر

</div>
