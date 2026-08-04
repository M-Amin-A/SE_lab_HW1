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

### تاریخچه Commitها (۲۱ commit)

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
| 21 | *(این commit)* | `docs: add implementation report to README` | dev | گزارش کامل |

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

### GitHub Actions — استقرار خودکار

Workflow در `.github/workflows/deploy.yml` با trigger روی push به `main`:

1. Checkout مخزن
2. Setup GitHub Pages
3. Upload artifact (فایل‌های استاتیک)
4. Deploy به GitHub Pages

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
