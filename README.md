# Django-basic-start-project


cheat sheet  >> https://dev.to/ericchapman/my-beloved-django-cheat-sheet-2056


Basic setting start project Django 
### สร้าง Virtualenv และ Activate
```python
virtualenv venv
```
```python
venv\Scripts\activate
```
### install Django
```python
pip install django
pip install Pillow
```
### สร้าง Project
```python
django-admin startproject myproject 
```
### สร้าง App 
```python
python manage.py startapp mywebsite
```
### settings.py 
```python
INSTALLED_APPS = [
	'mywebsite',

]



TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [Path.joinpath(BASE_DIR, 'templates')], 
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]

TIME_ZONE = 'Asia/Bangkok'

SESSION_ENGINE = 'django.contrib.sessions.backends.signed_cookies'

SESSION_EXPIRE_AT_BROWSER_CLOSE = True

STATIC_URL = '/static/'

STATICFILES_DIRS = [Path.joinpath(BASE_DIR, 'static')]
STATIC_ROOT = Path.joinpath(BASE_DIR, 'staticfiles')

MEDIA_URL = '/media/'
MEDIA_ROOT = Path.joinpath(BASE_DIR, 'media')
```
### urls.py 
```python
from django.contrib import admin
from django.urls import path, include
from django.conf import settings
from django.conf.urls.static import static

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('mywebsite.urls')),
]

urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
```
### urls.py ใน app
```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
```
### folder
`media`
`static`
`templates`
### views.py
```python
from django.shortcuts import render
def index(request):
    return render(request, 'index.html')
```
### คำสั่ง Migrate Database
`python manage.py makemigrations`

`python manage.py migrate`
### คำสั่งสร้าง UserAdmin
`python manage.py createsuperuser`
### คำสั่ง Runserver
`python manage.py runserver`

### Mysql install
```python
pip install mysqlclient
```
### Mysql setting.py
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'HOST': '',
        'USER': '',
        'PASSWORD': '',
        'PORT': '3306',
        'NAME': ''
    }
}
```



### Database Clear Django 

```Database Clear Django
python manage.py flush
```
