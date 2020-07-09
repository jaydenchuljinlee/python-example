# 1. Django 프로젝트 설정 및 실행

  ### $ pip install django
  - pip를 이용하여 django를 설치한다.

  ### $ django-admin startproject config .
  - 위 명령어를 통해 config라는 설정 파일들과 venv(가상 환경 설정), manage.py라는 파일이 생긴다.

  ### $ python manage.py migrate
  - DB를 초기화하면서 파일을 생성
  - db.sqlite3라는 파일이 생김

  ### $ python manage.py createsuperuser
  - 위 명령어로 터미널에서 유저를 생성

  ### $ python manage.py runserver
  - 생성한 서버를 실행

# 2. Django 프로젝트 구조

  ## config 폴더
   - 프로젝트 관련 설정 파일과 웹 서비스 실행을 위한 파일들
   - django-admin start project 명령어를 통해 생성된 폴더

   ### __init__.py
    - 파이썬 2.x 버전과의 호환을 위해 만들어진 비어있는 파일
    - 3.x 버전에서는 불필요하지만, 계속 생성 되어지는 파일
    
   ### settings.py
    - 프로젝트 설정에 관한 다양한 내용
    - 뒤에서 자세히 설명
    
   ### urls.py
    - url 설정 관련
    - settings.py에서 변경 가능
    
   ### wsgi.py
    - 웹 서비스를 실행하기 위한 wsgi 관련 내용
    
  ## venv 폴터
   - 프로젝트 구동에 필요한 가상환경이 들어있는 폴더
   
  ## db.sqlite3
   - SQLite3 DB 파일
   - 임의로 삭제하거나 위치를 이동하면 안된다.
   - 다른 DB를 사용할 경우 필요 없다.
   
  ## manage.py
   - 장고의 다양한 명령어를 실행 하기 위한 파일
   
  ## settings.py
  
   - BASE_DIR : 프로젝트 루트 폴더. 설정 파일이나 py 파일 등에서 프로젝트 루트 폴더를 찾아 그 하위를 탐색하는 일을 수행
   
   - SECRET_KEY : 보안을 위해 사용. 세션값의 보호나 비밀번호 변경시 사용되는 URL을 만드는 일 등에 사용
   
   - DEBUG : 디버그 모드를 설정. TRUE일 경우 다양한 오류 메시지를 즉시 확인 가능. 실제 어플리케이션 배포시에는 False
   
   - ALLOWED_HOSTS : 현재 서비스의 호스트 설정. 디버그 모드가 False일 때, 이곳이 비어있다면 서비스 시작 불가
   
   - INSTALLED_APPS : 현재 프로젝트에서 사용하는 앱의 목록을 기록하고 관리. 작성하고 추가 할 앱 또한 이곳에 한다.
   
   - MIDDLEWARE : 장고의 모든 요청/응답 사이에 실행되는 특수한 프레임워크. 주로 보안 관련 내용들
   
   - ROOT_URLCONF : 기준이 되는 urls.py의 경로 설정
   
   - TEMPLATES : 장고에서 사용하는 템플릿 관련 설정. 템플릿 엔진과 폴더의 경로 등을 변경하는데 사용
   
   - WSGI_APPLICATION : wsgi 어플리케이션을 설정
   
   - DATABASES : DB 관련 설정
   
   - AUTH_PASSWORD_VALIDATORS : 비밀번호 검증을 위한 설정. 기본적인 검증 로직이 들어있다.
   
   - LANGUAGE_CODE : 다국어 관련 

