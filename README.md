# 🧾 InnoVentory

A smart, web-based inventory and business management system built for small and medium enterprises (SMEs).

**Python**
**Django**
**MySQL**

---

## 📘 Overview

InnoVentory simplifies inventory tracking, sales monitoring, and business record-keeping for SMEs.

Key features:

* ✅ Streamline daily operations
* 🧠 Reduce human error
* 📊 Real-time data insights
* 👥 Efficient user and role management

---

## 🛠 Local Setup (No .env)

Follow these steps to run InnoVentory locally using full settings in `settings.py`.

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/<your-username>/innoventory.git
cd innoventory
```

### 2️⃣ Create and Activate Virtual Environment

```bash
# macOS/Linux
python -m venv venv
source venv/bin/activate

# Windows
python -m venv venv
venv\Scripts\activate
```

### 3️⃣ Install Dependencies

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### 4️⃣ Setup MySQL Database

Start MySQL server.

Create the database:

```sql
CREATE DATABASE innoventory;
```

Example local credentials:

| Field    | Value       |
| -------- | ----------- |
| NAME     | innoventory |
| USER     | root        |
| PASSWORD | 123456      |
| HOST     | localhost   |
| PORT     | 3306        |

### 5️⃣ Generate Django Secret Key

Run:

```bash
python -c "from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())"
```

Copy the output and use it in your settings.

### 6️⃣ Full `settings.py` Example (MySQL, no .env)

```python
from pathlib import Path

BASE_DIR = Path(__file__).resolve().parent.parent

# SECURITY
SECRET_KEY = "paste-your-generated-secret-key-here"
DEBUG = True
ALLOWED_HOSTS = ["127.0.0.1", "localhost"]
CSRF_TRUSTED_ORIGINS = ["http://127.0.0.1:8000"]

# Application definition
INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
    "accounts",
    "products",
    "sales",
    "suppliers",
    "reports",
    "django.contrib.humanize",
]

MIDDLEWARE = [
    "django.middleware.security.SecurityMiddleware",
    "whitenoise.middleware.WhiteNoiseMiddleware",
    "django.contrib.sessions.middleware.SessionMiddleware",
    "django.middleware.common.CommonMiddleware",
    "django.middleware.csrf.CsrfViewMiddleware",
    "django.contrib.auth.middleware.AuthenticationMiddleware",
    "django.contrib.messages.middleware.MessageMiddleware",
    "django.middleware.clickjacking.XFrameOptionsMiddleware",
]

ROOT_URLCONF = "innoventory.urls"

TEMPLATES = [
    {
        "BACKEND": "django.template.backends.django.DjangoTemplates",
        "DIRS": [BASE_DIR / "templates"],
        "APP_DIRS": True,
        "OPTIONS": {
            "context_processors": [
                "django.template.context_processors.request",
                "django.template.context_processors.debug",
                "django.contrib.auth.context_processors.auth",
                "django.contrib.messages.context_processors.messages",
            ],
        },
    },
]

WSGI_APPLICATION = "innoventory.wsgi.application"

# Database
DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.mysql",
        "NAME": "innoventory",
        "USER": "root",
        "PASSWORD": "123456",
        "HOST": "localhost",
        "PORT": "3306",
    }
}

AUTH_USER_MODEL = "accounts.CustomUser"

# Password validation
AUTH_PASSWORD_VALIDATORS = [
    {"NAME": "django.contrib.auth.password_validation.UserAttributeSimilarityValidator"},
    {"NAME": "django.contrib.auth.password_validation.MinimumLengthValidator"},
    {"NAME": "django.contrib.auth.password_validation.CommonPasswordValidator"},
    {"NAME": "django.contrib.auth.password_validation.NumericPasswordValidator"},
]

PASSWORD_HASHERS = [
    "django.contrib.auth.hashers.BCryptSHA256PasswordHasher",
]

# Static files
STATIC_URL = "/static/"
STATICFILES_DIRS = [BASE_DIR / "static"]
STATIC_ROOT = BASE_DIR / "staticfiles"
STATICFILES_STORAGE = "whitenoise.storage.CompressedManifestStaticFilesStorage"

# Authentication redirects
LOGIN_REDIRECT_URL = "/accounts/dashboard/"
LOGIN_URL = "/accounts/login/"
LOGOUT_REDIRECT_URL = "/accounts/login/"

# Internationalization
LANGUAGE_CODE = "en-us"
TIME_ZONE = "UTC"
USE_I18N = True
USE_TZ = True

DEFAULT_AUTO_FIELD = "django.db.models.BigAutoField"
```

### 7️⃣ Apply Migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

### 8️⃣ Create Superuser

```bash
python manage.py createsuperuser
```

### 9️⃣ Run Development Server

```bash
python manage.py runserver
```

Visit: [http://127.0.0.1:8000](http://127.0.0.1:8000)

---

## 👥 Team Members

**Michelle Marie P. Habon** — Business Analyst — [michellemarie.habon@cit.edu](mailto:michellemarie.habon@cit.edu)
**Tovi Joshua J. Hermosisima** — Scrum Master — [tovijoshua.hermosisima@cit.edu](mailto:tovijoshua.hermosisima@cit.edu)
**Ashley N. Igonia** — Product Owner — [ashley.igonia@cit.edu](mailto:ashley.igonia@cit.edu)
**Kenn Xavier C. Dabon** — Developer — [kenn.dabon@cit.edu](mailto:kenn.dabon@cit.edu)
**Shinely Marie R. Embalsado** — Developer — [shinelymarie.embalsado@cit.edu](mailto:shinelymarie.embalsado@cit.edu)
**Michaela Ma. Alexa D. Estrera** — Lead Developer — [michaelamaalexa.estrera@cit.edu](mailto:michaelamaalexa.estrera@cit.edu)

---
