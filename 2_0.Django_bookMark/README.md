# 두 번째 예제 설명

## 장고 기본 셋팅
  - $ pip install django
  - $ django-admin startproject config . (처음 시작할 때, 프로젝트에 대한 기본 설정을 담고 있기 때문에 이름을 confg라고 하는게 편하다.)
  - $ python manage.py migrate
  - $ python manage.py createsuperuser (http://l27.0.0.1:8000/admin)에서 사용할 유저
  - $ python manage.py runserver (프로젝트 실행)
  
## Bookmark 객체 생성
  - $ python manage.py startapp bookmark (명령어를 실행하면 venv 폴더 아래 기본 프로젝트 구조가 생성)
  
  - bookmark/model.py 아래 다음과 같이 작성
    ```python
    from django.db import models 
    
    # Create your models here. 
    class Bookmark(models.Model): 
      site_name = models.CharField(max_length=100) 
      url = models.URLField('Site URL')
    ```  

  - config/settings.py의 INSTALLED_APPS에 bookmark 추가
    ```python
        INSTALLED_APPS = [
          'django.contrib.admin',
          'django.contrib.auth',
          'django.contrib.contenttypes',
          'django.contrib.sessions',
          'django.contrib.messages',
          'django.contrib.staticfiles',
          'bookmark',
      ]
    ```
  - $ python manage.py makemigrations bookmark (모델을 생성하기 위한 명령어)
  
  - $ python manage.py migrate bookmark (생성한 모델을 DB에 적용하기 위한 명령어)
  
  - bookmark/admin.py에 다음과 같이 작성 (모델을 관리자 페이지에 등록해주는 역할, 관리자 페이지에서 보이는 내용의 변경, 기능 추가 등을 할 수 있는 코드를 입력하는 파일)
    ```python
      from django.contrib import admin

      # Register your models here.
      from .models import Bookmark

      admin.site.register(Bookmark)
    ```
    
  - python manage.py runserver (서버를 올리고 http://127.0.0.1:8000/admin 에 로그인한 뒤 페이지 아래 bookmark가 보이면 성공!)
    
   
