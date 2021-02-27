---
title: Django & Vue AWS EC2에 배포하기(2)
date: 2021-02-27 01:02:70
category: development
thumbnail: { thumbnailSrc }
draft: false
---

> 무사히 인스턴스에 Front와 Back 리포지토리를 clone받았다✨✨ 이제 Front(Vue)를 배포해보자



### 01. NodeJs 설치

> 자바스크립트 실행환경인 NodeJS를 설치한다.

```bash
// PPA로 14버전 가져오기
$ curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -

// NodeJS 설치
$ sudo apt-get install nodejs

// npm 설치 (NodeJS 설치하면 자동으로 npm까지 설치되지만, 혹시 모르니까 한 번 더 설치한다)
$ sudo apt-get install npm

// 버전 확인
$ node -v
$ npm -v

// build-essential 설치 (npm이 제대로 동작하려면 필요하다)
$ sudo apt-get install build-essential
```

<br/><br/>

### 02. Nginx 설치

>  nginx는 클라이언트와 서버 중간에서 대신 통신을 해주는 서버다. (리버스 프록시)

```bash
// nginx 설치
$ sudo apt-get install nginx

// 현재 사용가능한 서비스별 ufw 설정값을 확인한다.
$ sudo ufw app list
  Nginx Full # 포트 80(암호화되지 않은 웹 트래픽)과 포트 443(TLS/SSL 암호화 트래픽) 모두 연다.
  Nginx HTTP # 포트 80 (암호화되지 않은 웹 트래픽)을 연다
  Nginx HTTPS # 이 프로필은 포트 443 (TLS/SSL 암호화 트래픽)을 연다.
  OpenSSH 
  
// HTTP를 열어준다.
$ sudo ufw allow 'Nginx HTTP'

// sites-available 파일 수정
$ vi /etc/nginx/site-available/default
```

- Vue 프로젝트를 빌드하면 `dist`  폴더가 생긴다. dist 폴더의 위치를 `nginx` 의 `sites-available` 에서 명시해준다. (`i` 누르면 수정할 수 있다.)

```bash
server {
        listen 80 default_server;
        listen [::]:80 default_server;

		# dist 폴더 경로
        root /home/ubuntu/Movie_community_Front/dist;
     
        index index.html;

        server_name _;

        location / {
        	# 허용된 국가가 아닌경우 접근을 금지한다. 
        	if ($allowed_country = no) {
                return 403;
            }
            try_files $uri $uri/ /index.html;
        }
```

- `esc` 누르고  `:wq` 로 저장하고 나가준다. (만약에 안나가진다면 `:qa!`)

```bash
// nginx 재시작
$ sudo service nginx restart
또는
$ sudo systemctl restart nginx
```

- 이제 EC2 퍼블릭IP 로 접속하면 Fornt파일이 배포가 된 것을 확인할 수 있다!!

- (참고)  [웹서버 배포하기 1부 (Nginx 연동)](https://jay-ji.tistory.com/57) 블로그를 참고했다. 

- (참고) [나는 nginx 설정이 정말 싫다구요](https://juneyr.dev/nginx-basics) , [nginx 정리와 설치 및 기본 설정방법](https://wedul.site/579) 블로그에서 nginx 설정에 대한 설명을 확인할 수 있다. 

<br/><br/>