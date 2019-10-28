---
layout: post
title: "Database studying"
date: 2019-10-27
excerpt: "with homework"
tags: [DB,HW]
feature: http://i.imgur.com/Ds6S7lJ.png
comments: true
---

## DB과제
<figure>
    <img src="/images/Er.png">
    <figcaption>ER Diagram of open market database</figcaption>
</figure>

 > table 을 추가하기 전에는 다음과 같이 반드시 drop 명령어를 써서 기존의 중복되는 이름을 가지는 테이블을 삭제해 주어야 한다.

 ~~~ sql
 DROP TABLE account cascade constraint;
 DROP TABLE item cascade constraint;
 DROP TABLE service cascade constraint;
 DROP TABLE customer cascade constraint;
 DROP TABLE branch cascade constraint;
 ~~~
 <Br>

 > servece table 생성<br>
    <b>참조되는 테이블</b>을 반드시 먼저 생성해 주어야한다.

  ~~~ sql
  create table service(
  s_date date not null,
  s_join varchar2(3) not null,
  constraint service_pk primary key(s_date,s_join));
  ~~~

<i>마지막줄을 만약, s_date primary key, s_join varchar2(3) primary key 로 하면 다음과 같은 오류가 뜬다.
ORA-02260: 테이블에는 하나의 기본 키만 가질 수 있습니다. => 실제로 우리가 원하는 것은 primary key 가 두개 인 것//이 아니라, 두개의 컬럼을 하나의 primary key 로 사용하는 것이며.(이것만 가능) 이 명령어가 바로
constraint service_pk primary key(s_date,s_join)); 인 것이다!*****
그래서 이 primary key 를 fk 로 참조 할 때도 아래 customer table 에서 주석처리 된것처럼 하면 안되고,
constraint ac_dajo_fk foreign key(c_s_date,c_s_join) references service(s_date,s_join)); 이렇게
해야한다. </i>
<br><Br>

> customer table 생성

~~~ sql
create table customer(
c_no decimal(7) not null,
c_name varchar2(5) not null,
c_addr varchar2(20) not null,
c_phone varchar2(16) not null,
c_email varchar2(15),
c_s_date date not null,
c_s_join varchar2(3) not null,
constraint ac_no_pk primary key(c_no),
constraint ac_dajo_fk foreign key(c_s_date,c_s_join) references service(s_date,s_join));
//constraint ac_da_fk foreign key(c_s_date) references service(s_date),
//constraint ac_jo_fk foreign key(c_s_join) references service(s_join));
~~~

<br><br>

> product table 생성

~~~ sql
create table product(
p_no decimal(7) not null,
p_date date not null,
p_left varchar2(5) not null,
p_comp varchar2(10) not null,
p_s_date date not null,
p_s_join varchar2(3) not null,
constraint ac_no_pk1 primary key(p_no,p_date),
constraint ac_dajo_fk1 foreign key(p_s_date,p_s_join) references service(s_date,s_join));
//constraint ac_da_fk1 foreign key(p_s_date) references service(s_date),
//constraint ac_jo_fk1 foreign key(p_s_join) references service(s_join));
~~~

<br><br>

> delivery table 생성

~~~ sql
create table delivery(
d_no decimal(7) not null,
d_name varchar2(10) not null,
constraint ac_noname_pk2 primary key(d_no,d_name));
//constraint ac_no_pk2 primary key(d_no),
//constraint ac_name_pk2 primary key(d_name));
~~~

<br><Br>

> buying table 생성

~~~ sql
create table buying(
b_c_no decimal(7) not null,
b_p_no decimal(7) not null,
b_p_date date not null,
constraint ac_buy_pk primary key(b_c_no,b_p_no,b_p_date),
constraint ac_cno_fk3 foreign key(b_c_no) references customer(c_no),
constraint ac_pnodate_fk3 foreign key(b_p_no,b_p_date) references product(p_no,p_date));
//constraint ac_pno_fk3 foreign key(b_p_no) references product(p_no),
//constraint ac_pdate_fk3 foreign key(b_p_date) references product(p_date));
~~~

<Br><Br>

> whodeliver table 생성

~~~ sql
create table whodeliver(
w_d_no decimal(7) not null,
w_d_name varchar2(10) not null,
w_p_no decimal(7) not null,
w_p_date date not null,
constraint ac_whodeliv_pk4 primary key(w_d_no,w_d_name,w_p_no,w_p_date),
constraint ac_don_fk4 foreign key(w_d_no,w_d_name) references delivery(d_no,d_name),
constraint ac_pno_fk4 foreign key(w_p_no,w_p_date) references product(p_no,p_date));
~~~
