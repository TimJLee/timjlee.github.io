---
layout: post
title: "Consideration for Homomorphic Encryption"
date: 2019-10-30
excerpt: "Consideration for Homomorphic Encryption in comparison with public-key cryptography"
tags: [Security,Cryptography]
feature: http://i.imgur.com/Ds6S7lJ.png
comments: true
---

## <b>동형암호</b>에 대한 고찰 ~ <i style="font-size:20px; color:red;">논문 수정</i><br>

  <p>&nbsp;&nbsp;&nbsp;선배님으로부터 피드백을 받으면서, 내 논문에 부족한 점이 있다면 동형암호에 대한 '고찰'이다. 단순히 동형암호란 무엇인지 개념을 나눠서 설명하고, 이를 연구중인 여러 단체와 이제까지 개발된 라이브러리 등을 제시하는 것을 넘어선, <b>'나 스스로 생각하기에'</b> 이러이러한 점이 개선되어야 한다고 생각하는 부분이 있어야 한다는 것을 깨달았다.</p>
  &nbsp;&nbsp;&nbsp;직관적으로 봤을 때 고찰에 대한 내용을 결론에 바로 덧붙이는 것 보다는 본론 내부에 소제목을 다음과 같이 <b>2.5 고찰</b> 로 짓고 이에 대한 내용을 <b>2.6 전망</b> 전에 삽입하는 것이 괜찮을 것 같다고 결론을 내렸다. 다음 표에서 보듯이 현재까지 제시된 동형암호는 현재 사용중인 공개키 암호방식인 RSA,ECC 와 동급의 Security level 로 설계가 되었다. 그런데 키사이즈가 기존의 암호들에 비해서 비약적으로 크다는 것을 알 수 있다. 그러므로 키사이즈 축소방안과 최적화 구현에 대한 연구가 더 필요할 것으로 보인다~~ 이런식으로 수정을 해야겠다.<br><br>
  <figure>
      <a href="https://github.com/TimJLee/timjlee.github.io/blob/master/images/crypto.png?raw=true"><img src="https://github.com/TimJLee/timjlee.github.io/blob/master/images/crypto.png?raw=true"></a>
      <figcaption>공개키 암호와 동형암호의 성능 비교</figcaption>
  </figure>
