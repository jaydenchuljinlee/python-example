# 파이썬 장고 예제 기록

  ## 장고 기본 명령어
 
  -  django-admin startproject : 장고 프로젝트를 만드는 명령어
  
  - startapp : 프로젝트에 기능 단위인 앱을 새로 만들 때 사용
  
  - makemigrations : 어플리케이션 변경 사항을 추적해 DB에 적용할 내용 정리. 앱 안의 모델에 변경 사항이 존재할 때 사용
  
  - sqlmigrate : 실행할 SQL 명령문을 출력
  
  - migrate : 실제 변경 사항을 DB에 반영
  
  - showmigrations : 프로젝트의 DB 변경 사항 목록과 상태 출력
  
  - runserver : 테스트 서버를 실행. 웹 서비스를 실제로 동작시켜 확인
  
  - dumpdata : 현재 DB의 내용을 백업할 때 사용
  
  - loaddata : 백업 파일에서 DB로 내용을 복구할 때 사용
  
  - flush : DB 테이블은 그대로 두고 테이블의 내용만 전부 삭제
  
  - shell : 장고 쉘을 실행. 작성한 모델 등을 불러와 실제로 테스트 가능
  
  - dbshell : DB에 직접 접근할 수 있는 쉘을 실행. 장고 관리자에 문제가 있을 때 주로 dbshell을 통해 DB을 수정
  
  - createsuperuser : 관리자 계정을 생성
  
  - changepassword : 계정의 비밀번호를 변경
