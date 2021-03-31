---
title: Django & Vue AWS EC2에 배포하기(3)
date: 2021-02-27 14:02:54
category: development
thumbnail: { thumbnailSrc }
draft: false
---

> Front파일을 배포했으니, Back 파일도 배포해보자!!



### 01. virtualenv 설치

> 먼저, clone 받은 Back 파일로 들어가서 가상환경을 만든다.

```bash
// 가상환경 설치
$ sudo apt-get install virtualenv

// venv라는 이름의 가상환경을 만든다
$ virtualenv -p python3 venv

// venv 활성화
$ source venv/bin/activate

// requiremets.txt에 있는 패키지 설치
$ pip install -r requirements.txt

// django 데이터베이스 migrate
$ python manage.py makemigrations
$ python manage.py migrate
$ python manage.py loaddata movies.json

// 실행 확인
$ python manage.py runserver 0.0.0.0:8000
[EC2 인스턴스 public IP:8000 으로 접속하면 확인할 수 있다.]
```

<br/><br/>

### 02. WSGI (Gunicorn) 설치

>웹 서버와 웹 어플리케이션의 인터페이스를 위한 파이썬 프레임워크이다. 

```bash
// 가상환경에 gunicorn 설치
$ pip install gunicorn

// gunicorn service 등록 스크립트를 작성한다. 
$ vi /etc/systemd/system/gunicorn.service

[Unit]
Description=gunicorn daemon
After=network.target

[Service]
User=ubuntu
Group=www-data
WorkingDirectory=[Back 폴더 경로] # /home/ubuntu/Movie_community_Back
ExecStart=[gunicorn 경로] \ #/home/ubuntu/Movie_community_Back/venv/bin/gunicorn \
        --workers 5 \
        --bind [포트 연결] \ #0.0.0.0:8000
        [프로젝트 이름].wsgi:application

[Install]
WantedBy=multi-user.target


// gunicorn service 적용 및 시작
$ sudo systemctl daemon-reload
$ sudo systemctl start gunicorn
$ sudo systemctl enable gunicorn 

// gunicorn 확인
$ systemctl status gunicorn

// gunicorn을 다시 시작해야 할 때
$ sudo systemctl daemon-reload
$ sudo systemctl restart gunicorn
```

<br/><br/>

### 03. nginx 설정

```bash
// sites-enablec/default 수정
$ sudo vi /etc/nginx/sites-enabled/default

location / {
	#혹시 모를 CORS 이슈 해결을 위해 header를 넣어준다
	add_header 'Access-Control-Allow-Origin' '*';
	try_files $uri $uri/ /index.html;
}
```

<br/><br/>