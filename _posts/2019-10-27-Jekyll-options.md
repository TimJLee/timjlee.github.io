---
layout: post
title: "Understanding Jekyll's options"
date: 2019-10-27
excerpt: "hi Jekyll"
tags: [feature, Jekyll]
feature: http://i.imgur.com/Ds6S7lJ.png
comments: true
---

## 유용한 기능들<br>
<br>
<a>
다음 기호 안에 post 에 보여지지 않기를 원하는 문장을 넣으면 주석처럼 동작한다.

~~~
<!--   -->
~~~
</a>
<!-- dsfadfs -->

다음과 같이  html 태그도 사용이 가능하다. \로는 코드들을 나타낼 수 없구나.. 더 연구를 해봐야겠다. -> 아래와 같이 code-highligt 를 이용하면 편리함을 깨달았다.

~~~ html
<br>hi</br>
~~~


\> 이걸 쓰면 다음과 같이 나온다.
> hi

\* 이걸 쓰면 다음과 같이 나온다.
* 1
* 2

여기서 주의할 점은 기호 뒤에 한칸을 띄어야 한다는 것이다.
다른 블로그들을 보니 html 태그를 이용해서 블로그를 작성한 곳이 꽤나 있다.(F12 개발자 도구로 본 결과 - 뒤늦은 깨달음 : 어떤 언어로 쓰든 웹상에 올라갈 때는 html 태그로 바뀌는구나!).

+또한 내가 만든 웹사이트를 ISP 에서 값을 지불하고 유료로 도메인을 얻는 대신, github.io 를 이용하면 무료로 웹사이트 시험이 가능함을 알았다.
