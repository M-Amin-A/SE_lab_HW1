# SE Lab HW1 - Static Frontend

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

```
main ─────────────────────────────────────────────► (via PR from dev)
  │
  └── dev ──┬── feature/navigation ──► merge (conflict #1)
            ├── feature/projects ────► merge (conflict #2)
            └── hotfix/fix-contact-placeholder ──► fast-forward merge
```

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

```bash
# اتصال مخزن محلی به remote روی GitHub
git remote add origin https://github.com/M-Amin-A/SE_lab_HW1

# مشاهده وضعیت فایل‌ها (tracked / untracked / modified)
git status
```

#### ۲. Stage و Commit

```bash
# افزودن فایل مشخص به staging area
git add .gitignore
git add index.html css/styles.css

# ثبت تغییرات با پیام معنادار
git commit -m "chore: add .gitignore for Node, IDE and OS files"
git commit -m "feat: add basic HTML skeleton with RTL support"
```

**توضیح:** هر commit یک تغییر مشخص در فرآیند توسعه را ثبت می‌کند (مثلاً افزودن feature، رفع باگ، یا به‌روزرسانی مستندات).

#### ۳. کار با شاخه‌ها (Branch)

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

**توضیح:**
- `dev` — شاخه توسعه اصلی
- `feature/*` — هر feature در شاخه جداگانه
- `hotfix/*` — رفع سریع باگ بدون انتظار برای release بعدی

#### ۴. ادغام (Merge)

```bash
# ادغام feature/navigation در dev
git checkout dev
git merge feature/navigation -m "merge: integrate navigation feature into dev"

# ادغام feature/projects در dev
git merge feature/projects -m "merge: integrate projects and contact features into dev"

# ادغام hotfix در dev (fast-forward)
git merge hotfix/fix-contact-placeholder -m "merge: apply hotfix for contact form placeholder"
```

**توضیح:** merge تغییرات یک شاخه را در شاخه فعلی ادغام می‌کند. در صورت تداخل، Git conflict ایجاد می‌کند.

#### ۵. رفع Conflict

```bash
# هنگام merge، Git conflict را گزارش می‌دهد:
# CONFLICT (content): Merge conflict in index.html

# پس از ویرایش دستی فایل‌های conflict‌دار:
git add index.html css/styles.css
git commit -m "merge: resolve conflict between dev and feature/navigation in index.html"
```

**توضیح:** markerهای `<<<<<<<`، `=======`، `>>>>>>>` در فایل نشان‌دهنده conflict هستند. پس از انتخاب نسخه نهایی، فایل را add و commit کنید.

#### ۶. مشاهده تاریخچه

```bash
# لیخت commitها
git log --oneline

# تاریخچه همه شاخه‌ها
git log --oneline --all --graph

# مشاهده diff تغییرات
git diff
```

#### ۷. Push به GitHub

```bash
# ارسال شاخه dev به remote
git push -u origin dev

# ارسال همه شاخه‌ها
git push -u origin main dev feature/navigation feature/projects hotfix/fix-contact-placeholder
```

**توضیح:** `-u` (یا `--set-upstream`) ارتباط شاخه محلی با remote را برقرار می‌کند.

#### ۸. Pull Request (روی GitHub)

ادغام با `main` فقط از طریق Pull Request انجام می‌شود:

```bash
# پس از push شاخه dev:
# 1. به github.com/M-Amin-A/SE_lab_HW1 بروید
# 2. Pull requests → New pull request
# 3. base: main ← compare: dev
# 4. Create pull request → Merge pull request
```

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

```
Push to main  →  GitHub Actions Trigger  →  Build  →  Deploy  →  GitHub Pages
```

#### مراحل Workflow

| مرحله | Action | توضیح |
|-------|--------|-------|
| 1 | `actions/checkout@v4` | دریافت کد از مخزن |
| 2 | `actions/configure-pages@v5` | پیکربندی GitHub Pages |
| 3 | `actions/upload-pages-artifact@v3` | آپلود فایل‌های استاتیک (HTML, CSS, JS) |
| 4 | `actions/deploy-pages@v4` | استقرار روی GitHub Pages |

#### Trigger

```yaml
on:
  push:
    branches: [main]    # فقط push به main
  workflow_dispatch:    # اجرای دستی از تب Actions
```

#### پیش‌نیازهای فعال‌سازی Deploy

1. **Push شاخه `dev` به `main`** (از طریق Pull Request)
2. **Settings → Pages → Source:** انتخاب **GitHub Actions**
3. **Settings → Actions → General:** اجازه اجرای workflow

#### فایل `.nojekyll`

این فایل خالی در root پروژه قرار دارد تا GitHub Pages از Jekyll برای پردازش فایل‌ها استفاده نکند و فایل‌های استاتیک مستقیماً serve شوند.

#### آدرس سایت

پس از deploy موفق:

| محیط | URL |
|------|-----|
| GitHub Pages | [https://m-amin-a.github.io/SE_lab_HW1/](https://m-amin-a.github.io/SE_lab_HW1/) |

#### بررسی وضعیت Deploy

```bash
# در GitHub:
# Repository → Actions → Deploy to GitHub Pages → آخرین run

# یا:
# Repository → Settings → Pages → آدرس سایت و وضعیت deployment
```

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

---

### اجرای محلی

فایل `index.html` را در مرورگر باز کنید، یا:

```bash
# با Python
python -m http.server 8080

# با Node.js
npx serve .
```

---

### نویسنده

**M-Amin-A** — آزمایشگاه مهندسی نرم‌افزار، ترم ۸
