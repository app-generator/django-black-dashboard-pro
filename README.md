# [Django Black PRO](https://appseed.us/product/black-dashboard-pro/django/)

**[Django](https://appseed.us/admin-dashboards/django/)** Starter styled with **Black Dashboard PRO**, a premium `Bootstrap` Design from `Creative-Tim`.
The product is designed to deliver the best possible user experience with highly customizable feature-rich pages. 

> **NOTE**: This product `requires a License` in order to access the theme. During the purchase, a `GitHub Access TOKEN` is provided. 

- 🛒 [Django Black PRO](https://appseed.us/product/black-dashboard-pro/django/) - `Product page` (contains payment links)
- 👉 [Django Black PRO](https://django-black-dashboard-pro.appseed-srv1.com/) - `LIVE Demo`
- 🚀 [Support](https://appseed.us/support/) via `Email` & `Discord`

<br /> 

## Features: 

- ✅ `Up-to-date Dependencies`
- ✅ `Design`: [Django Theme Black](https://github.com/app-generator/django-admin-black-pro) - `PRO Version`
- ✅ `Sections` covered by the design:
  - ✅ **Admin section** (reserved for superusers)
  - ✅ **Authentication**: `Django.contrib.AUTH`, Registration
  - ✅ **All Pages** available in for ordinary users 
- ✅ `Docker`
- 🚀 `Deployment` 
  - `CI/CD` flow via `Render`

<br />

![Django Black PRO - Premium Seed project powered by Flask.](https://user-images.githubusercontent.com/51070104/187623954-c4ade6a0-8cb2-4d2e-8698-e962621a613c.png)

<br />

## Manual Build 

> 👉 Download the code  

```bash
$ git clone https://github.com/app-generator/django-black-dashboard-pro.git
$ cd django-black-dashboard-pro
```

<br />

> Export `GITHUB_TOKEN` in the environment. The value is provided by AppSeed during purchase. 

This is required because the project has a private REPO dependency: `github.com/app-generator/priv-django-admin-black-pro`

```bash
$ export GITHUB_TOKEN='TOKEN_HERE'  # for Linux, Mac
$ set GITHUB_TOKEN='TOKEN_HERE'     # Windows CMD
$ $env:GITHUB_TOKEN = 'TOKEN_HERE'  # Windows powerShell 
```

<br />

> 👉 Install modules via `VENV`.


```bash
$ virtualenv env
$ source env/bin/activate
$ pip install -r requirements.txt
```

<br />

> 👉 Edit the `.env` using the template `.env.sample`. 

```env

# True for development, False for production
DEBUG=True

```

<br />

> 👉 Set Up Database

```bash
$ python manage.py makemigrations
$ python manage.py migrate
```

<br />

> 👉 Create the Superuser

```bash
$ python manage.py createsuperuser
```

<br />

> 👉 Start the app

```bash
$ python manage.py runserver
```

At this point, the app runs at `http://127.0.0.1:8000/`. 

<br />

## Codebase structure

The project is coded using a simple and intuitive structure presented below:

```bash
< PROJECT ROOT >
   |
   |-- core/                            
   |    |-- settings.py                  # Project Configuration  
   |    |-- urls.py                      # Project Routing
   |
   |-- home/
   |    |-- views.py                     # APP Views 
   |    |-- urls.py                      # APP Routing
   |    |-- models.py                    # APP Models 
   |    |-- tests.py                     # Tests  
   |    |-- templates/                   # Theme Customisation 
   |         |-- includes                # 
   |              |-- custom-footer.py   # Custom Footer      
   |     
   |
   |-- requirements.txt                  # Project Dependencies
   |
   |-- env.sample                        # ENV Configuration (default values)
   |-- manage.py                         # Start the app - Django default start script
   |
   |-- ************************************************************************
```

<br />

## How to Customize 

When a template file is loaded in the controller, `Django` scans all template directories starting from the ones defined by the user, and returns the first match or an error in case the template is not found. 
The theme used to style this starter provides the following files: 

```bash
< LIBRARY_ROOT >                     # This exists in ENV: LIB/admin_black_pro
   |
   |-- templates/                    # Root Templates Folder 
   |    |          
   |    |-- accounts/       
   |    |    |-- login.html          # Sign IN Page
   |    |    |-- register.html       # Sign UP Page
   |    |
   |    |-- includes/       
   |    |    |-- footer.html         # Footer component
   |    |    |-- sidebar.html        # Sidebar component
   |    |    |-- navigation.html     # Navigation Bar
   |    |    |-- scripts.html        # Scripts Component
   |    |
   |    |-- layouts/       
   |    |    |-- base.html           # Masterpage
   |    |    |-- base-auth.html      # Masterpage for Auth Pages
   |    |
   |    |-- pages/       
   |         |-- index.html          # Index Page (presentation)
   |         |-- settings.html       # Settings  Page
   |         |-- dashboard.html      # Dashboard page
   |         |-- *.html              # All other pages
   |    
   |-- ************************************************************************
```

When the project requires customization, we need to copy the original file that needs an update (from the virtual environment) and place it in the template folder using the same path. 

> For instance, if we want to **customize the footer.html** these are the steps:

- ✅ `Step 1`: create the `templates` DIRECTORY inside the `home` app
- ✅ `Step 2`: configure the project to use this new template directory
  - `core/settings.py` TEMPLATES section
- ✅ `Step 3`: copy the `footer.html` from the original location (inside your ENV) and save it to the `home/templates` DIR
  - Source PATH: `<YOUR_ENV>/LIB/admin_black_pro/includes/footer.html`
  - Destination PATH: `<PROJECT_ROOT>home/templates/includes/footer.html`

> To speed up all these steps, the **codebase is already configured** (`Steps 1, and 2`) and a `custom footer` can be found at this location:

`home/templates/includes/custom_footer.html` 

By default, this file is unused because the `theme` expects `footer.html` (without the `custom_` prefix). 

In order to use it, simply rename it to `footer.html`. Like this, the default version shipped in the library is ignored by Django. 

In a similar way, all other files and components can be customized easily.

<br />

## Recompile SCSS  

The SCSS/CSS files used to style the UI are saved in the `<YOUR_ENV>/LIB/admin_black_pro/static/assets` directory by PIP. 
In order to update the Ui colors (primary, secondary) this procedure needs to be followed. 

- Copy the `static` Directory from `VENV` to `ROOT/static` 
  - like this, Django will use the local versions and ignore the `VENV` files 
- Install dependencies via `Yarn`
- Edit `_variables.scss`
- Regenerate CSS via `gulp` 

```bash
$ yarn # install modules
$ # # edit variables 
$ vi static/assets/scss/black-dashboard/custom/_variables.scss 
$ gulp # SCSS to CSS translation
```

The `_variables.scss` content defines the `primary` and `secondary` colors: 

```scss
$default:       #344675 !default; // EDIT for customization
$primary:       #e14eca !default; // EDIT for customization
$secondary:     #f4f5f7 !default; // EDIT for customization
$success:       #00f2c3 !default; // EDIT for customization
$info:          #1d8cf8 !default; // EDIT for customization
$warning:       #ff8d72 !default; // EDIT for customization
$danger:        #fd5d93 !default; // EDIT for customization
$black:         #222a42 !default; // EDIT for customization
```

<br />

## Deploy on [Render](https://render.com/)

- Create a Blueprint instance
  - Go to https://dashboard.render.com/blueprints this link.
- Click `New Blueprint Instance` button.
- Connect your `repo` which you want to deploy.
- Fill the `Service Group Name` and click on `Update Existing Resources` button.
- After that your deployment will start automatically.

At this point, the product should be LIVE.

<br />

---
[Django Black PRO](https://appseed.us/product/black-dashboard-pro/django/) - **Django** starter provided by **[AppSeed](https://appseed.us/)**
