---
title: "Gatsby 블로그 개설!!\U0001F387"
date: 2021-01-07 23:01:31
category: Diary
thumbnail: { thumbnailSrc }
draft: false
---

### 왜 블로그를 시작하게 되었나 🤷‍♂️

> 장기기억의 매커니즘을 적극 활용하기 위함이랄까..

삼성 청년 소프트웨어 아카데미 (SSAFY) 비전공자반에서 6개월간의 웹 개발과정을 마쳤다.

이제 남은 6개월간 프로젝트를 진행하고 개발자로 취업을 준비하게 될 것이다. 본격적으로 취업 전선에 뛰어들기 전, 배웠던 내용을 다시 한 번 정리하는 시간이 필요하다고 느꼈다.  (미래의 동료 & 선배님들께 당당히 한 몫 해내는 모습을 보여드리고 싶다!)

이전까진 낯선 Web세계에서 눈코 뜰 새 없이 지식을 욱여넣었다면, 지금부터는 Blog정리로 나만의 지식으로 체화할 것이다 🦾

<br>

### Gatsby 블로그 생성하기

> Tistory, velog, jekyll, Medium, github.io 등 다양한 개발블로그 플랫폼이 있지만 **Gatsby**로 선택!

##### Gatsby란?

- **Gatsby**는 **JAMstack** 구조를 따르는 **정적 사이트 생성기**이다. 
- **React** + **GrapQL**

<br>

`JAMstack` 

JavaScript+ APIs + Markup 의 앞글자를 땄다. 

Client 요청은 자바스크립트, DB나 Server 관련 기능은 API, 정적 사이트 생성기 등으로 마크업을 미리 만든다는 개념이다.  (ex. 정적사이트, SPA 등등...)

[![image-20210123004927097](gatsby-%EB%B8%94%EB%A1%9C%EA%B7%B8-%EA%B0%9C%EC%84%A4!!%F0%9F%8E%87.assets/image-20210123004927097.png)](https://jamstack.org/)

☝ 자세한 설명 click

<br>

모든 정적 사이트는 잼스택 구조를 따르고 다양한 정적 사이트 생성기가 있다.

![image-20210123005306844](gatsby-%EB%B8%94%EB%A1%9C%EA%B7%B8-%EA%B0%9C%EC%84%A4!!%F0%9F%8E%87.assets/image-20210123005306844.png)

<br>

`Static Website (정적 웹사이트)` 

클라이언트가 요청을 보낸 후 서버는 따로 추가 처리 과정을 겪지 않는다. 

따라서 모든 사용자 같은 웹사이트 화면을 보게된다. 서버에 저장된 html파일이 그대로 브라우저에 보인다. 

(ex. 기술블로그, 기업소개 페이지)

<br>

`Dynamic Website (동적 웹사이트)` 

클라이언트가 요청을 보내면 서버는 클라이언트 요청한 데이터를 뿌려주거나 특정 기능을 수행한다. 

따라서 같은 웹사이트 주소라도 사용자마다 보이는 콘텐츠 내용이 다르다. 서버에 저장된 html파일이 동적으로 만들어진다. 

(ex. SNS 댓글 창, 쇼핑 검색 결과)

<br>

**왜 Gatsby 인가?**

- **Markdown**을 사용한다. 콘텐츠 관리가 쉽다.
- **SEO** , **성능** GOOD

`Gatsby Performance`

[![image-20210123012545911](gatsby-%EB%B8%94%EB%A1%9C%EA%B7%B8-%EA%B0%9C%EC%84%A4!!%F0%9F%8E%87.assets/image-20210123012545911.png)](https://www.gatsbyjs.com/features/jamstack/)☝ Gatsby vs 잼스택 프레임워크와 성능을 비교한 표 click! 

<br>

**Gatsby 블로그 만들기**

to be continue



**[참고]** 

[오픈소스 블로그 기술의 새 바람 ! 정적 페이지란?](https://blog.lgcns.com/2336)

[정적 사이트 생성기  Gatsby](https://blog.outsider.ne.kr/1426)

[React밖에 모르는 당신에게. GatsbyJS한 잔, '채용~'](https://blog.banksalad.com/tech/build-a-website-with-gatsby/)

