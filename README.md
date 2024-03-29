

# Django-start-project  <img src="https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=green" /> <img src="https://img.shields.io/badge/Python-FFD43B?style=for-the-badge&logo=python&logoColor=blue" />



### สร้าง Virtualenv และ Activate
```python
python -m venv name_venv
name_venv\Scripts\activate
```
### install Django
```python
pip install django
pip install -r requirements.txt #install .txt file
```
### สร้าง Project
```python
django-admin startproject project_name 
```
### สร้าง App 
```python
python manage.py startapp app_name
```
### settings.py 
```python #เพิ่ม App ที่สร้างเข้าไปใน Project ที่ไฟล์ Setting.py
INSTALLED_APPS = [
	'mywebsite', #เพิ่ม app เข้า project

]



TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [Path.joinpath(BASE_DIR, 'templates')],   #ใส่ Path ของ Templates
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

TIME_ZONE = 'Asia/Bangkok' # เพิ่ม Timezone

SESSION_ENGINE = 'django.contrib.sessions.backends.signed_cookies'

SESSION_EXPIRE_AT_BROWSER_CLOSE = True

#เพิ่ม Path ของ staticfile
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
from django.contrib.staticfiles.urls import staticfiles_urlpatterns

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('app_name.urls')), #เพิ่ม app เข้าใน project url
]
urlpatterns += static(settings.STATIC_URL, document_root=settings.STATIC_ROOT)
urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
urlpatterns += staticfiles_urlpatterns()
```
### urls.py ใน app
```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
```
### Folder ที่เพิ่มมา
`media`
`static`
`templates`
### views.py ของ app
```python
from django.shortcuts import render
def index(request):
    return render(request, 'index.html')
```
### คำสั่ง Migrate Database
```python
python manage.py makemigrations
python manage.py migrate
```
### คำสั่งสร้าง UserAdmin
```python
python manage.py createsuperuser
```
### คำสั่ง Runserver
```python
python manage.py runserver
```
### Database Clear Django 
```python
python manage.py flush
```
