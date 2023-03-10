---
title: "서비스 기획 용어 정리"
date: "2023-01-14"
tags: ["러닝스푼즈", "서비스기획"]
summary : "서비스 기획과 관련된 다양한 용어를 정리해보고자.md"
---

`정렬 X`

> **PMF** (Product-Market Fit)  

_제품이 특정 시장의 요구를 충족시키는 정도_  
시장조사/고객피드백/제품개발을 통해 이루어지며 PMF를 달성하는 것은 성공적인 비즈니스 구축을 위한 필수 단계  
<br>

> **CLV** (Customer Lifetime Value)  

_고객이 비즈니스에 가져올 총 가치를 추정하는 데 사용되는 기준_  
기업이 고객 확보 및 유지에 얼마나 투자할 수 있는지 이해하게 해줌!  
일반적으로 평균 구매가치, 구매 빈도, 관계의 예상 기간과 같은 요소를 고려하며, 고객 경험 개선/반복 구매 장려와 같은 전략을 통해 CLV를 높이면 장기적으로 수익과 수익성을 높일 수 있음!  
<br>

> **CAC** (Customer Acquisition Cost)  

_고객 확보에 드는 총 비용을 측정하는 척도_  
마케팅 및 광고 비용/수수료 및 기타 직접 비용과 같은 신규 고객확보와 관련된 모든 비용을 합산한 후, 특정기간 동안한 확보한 신규 고객수로 나눔!  
CAC가 상승하고 있다면 기업이 마케팅 전략을 조정하거나 비용 절감의 신호로 받아들일 수 있고, CAC가 감소하는 경우 고객 확보에 호율적이라는 지표로 받아들일 수 있음!

<br>

> **KPI** (Key Performance Indicator)  

KPI, 즉 핵심 성과 지표는 기업이 특정 목표를 달성하기 위한 진행 상황 추적에 사용  
<br>

> **Customer Journey Map**  

고객여정지도, 사용자가 프로덕트를 사용하는 과정에서의 타임라인이며 그 안에서 고객들이 느끼는 경험이 함께 기술

<br>

> **Aha-moment**  

_제품의 핵심 가치를 경험하는 순간, 서비스를 계속 쓰게되는 특이점_  
정량적으로 정의되는 이 행동을 한 유저 대부분이 리텐션이 생기는 그 행동…  
복잡하고 정교한 분석 결과보다 단순하고 명확하게 팀원들이 추종 가능한 단순한 문장!  

<br>

> **AARRR**  (**A**cquisition  |  **A**ctivation  |  ***R***etention  |  **R**evenue  |  **R**eferral)  

<details>
<summary>특정 지표를 중심으로 서비스의 현주소를 파악할 수 있는 지표</summary>
<div markdown="1">  


> **Acquisition**  _고객확보과정_  

**DAU**(Daily Active User) : 일 활성 유저 수  
**WAU**(Weekly Active User) : 주 활성 유저 수  
**MAU**(Monthly Active User) : 월 활성 유저 수  
**New user** : 새로운 유저 수  

<br>


> **Activation** _고객이 처음 서비스를 접할 때에 긍정적인 경험을 제공하고 있는가?_  

**이탈율** = `수 / 페이지 세션`  
**체류시간** = `총 체류시간 / 총 세션 수`  
**회원가입 수** = `서비스 가입자 수`  
**클릭률** = `해당 컨텐츠의 Click 수 / 해당 컨텐츠의 View 수`  
**전환율** = `해당 컨텐츠를 Click`  

<br>

> **Retention** _고객이 이후 서비스를 다시 사용하는 정도_  

**클래식 리텐션(N-Day Retention)**  
SNS나 메신저와 같이 사용빈도가 높은 서비스에 적합
기준 날짜에서 날짜별로 해당 유저가 재접속 했는지 측정  

**범위 리텐션(Range Retention)**  
서비스 주기가 길거나 일정한 주기가 있는 서비스에 유리
해당 기간 안에 user_id 기준으로 고유값을 구해서 리텐션 비율을 구함  

**롤링 리텐션 (Rolling Retention)**  
사용자 이탈률에 초점. 이커머스나 여행 등 사용빈도가 낮은 서비스에 유리
매일 변할 수 있어서 트렌드 보기에 적합하며 기준 날짜와 접속 날짜에 공백이 있더라도 접속한 것으로 간주 함  
`1월 1일에 접속 후 20일에 접속 시 1~20일 사이를 모두 접속으로 처리`  

<br>

> **Revenue** _최종 목적으로 연결되고 있는가?_  

**LTV**(life time value) = `고객의 평균 구매 단가 x 평균 구매 횟수`  
하나의 수식으로 정의하기 힘듦. 서비스별로 LTV를 찾아야 함  
한명의 고객이 서비스에서 재화를 소비하다가 이탈할 때 까지의 가치  
`모든 고객이 평균적으로 2만원을 결제, 모든 고객이 서비스 이탈 전까지 평균 2회 결제 시 LTV 4만원`  
        
**GMV**(Gross Merchandise Volume) `= 거래된 서비스/상품의 총 금액`
주로 이커머스에서 많이 활용되며 해당 업체가 벌어들인 총 금액을 의미
**객단가** = 총 거래액 / 총 유저 수
**구매전환율** = 구매 유저 수 / 접속 유저 수

> **Referral** _고객의 자발적인 공유가 일어나고 있는가?_  

**바이럴 계수(viral k)** `= 초대하는 사람 수 * 초대에 응할 확률 `
기존 고객이 새 고객을 n명 초대, 그 중 일부가 응한 것이 한 Viral Loop  
`어떤 유저가 10명을 초대했는데 그중 2명이 초대를 수락하면 K = 10 * (2/10) = 2`  
그외 리뷰 개수, 공유 개수 ...
        
</div>
</details>
        
> **Stickness**  

월간 활성 사용자 대비 일간 활성 사용자의 비율로 계산하며,
앱의 활성화, 의존도를 알 수 있으며 값이 클수록 재방문율이 높음!
DAU/MAU가 10%라면 앱에 한달동안 사용자들이 10% 들어온 것  

<br>

> **ARPU, ARPPU**
- **ARPU**(Average Revenue User)
    - ARPU = 매출 / 순수 활동 유저 수
    - 모든 사용자에 대한 매출로, 평균적으로 결제 유도를 해내는지 판단하는 지표
    - ARPU를 통해 사용자 트래픽의 증감을 알면, 매출도 얼마나 늘어나는지 알 수 있음
- **ARPPU**(Average Revenue Per Paid User)
    - ARPPU = 매출 / 순수 유료 사용자 수
    - 결제한 사용자에 대한 매출을 구하는 것으로 해당 프로젝트에 사람들이 얼마나 돈을 쓸 것이냐에 대한 가격선을 측정할 때 활용  

<br>

> **CAC** (Customer Acquisition Cost)   유저 한 명 획득에 들어가는 비용 

`CAC = 유저 획득 비용 / 신규 유저 수`  
결국 CAC보다 LTV가 높아야 의미가 있는 마케팅이라 할 수 있음…  

<br>

> **ROAS** (Return On Ad Spending)  마케팅으로 벌어들인 매출에 대한 지표  

`ROAS = 광고기여매출 /  광고비`  
성과가 잘못 측정될 수도 있기 때문에 Return의 기준을 잡는게 매우 매우 중요!!    
일반적으로 마지막 클릭이 발생한 광고에서 구매가 이루어졌다면 Return!

<br>

> **CPC** (Cost Per Click) 광고 클릭 당 가격

광고 클릭당 가격 400 -> 100번 클릭 = 40,000 과금  

<br>

> **CPM**(Cost Per Mile) 광고 1000회 노출 당 비용  

1,000회 뷰당 가격 3,000원 -> 100,000뷰 -> 100 * 3000 = 300,000원 과금
- **CPP**(Cost Per Period) : 일정 시간당 고정된 금액을 걸고 광고를 노출
- **CPA**(Cost Per Actioin) : 광고주가 원하는 액션 당 가격(가입하기, 구매)
- **CPI**(Cost Per Install) : 광고를 통한 설치 당 가격  

<br>

> **Carrying Capacity**  

`Carrying Capacity = 신규유저(active) / 잃는 유저(chum)`  
특정 서비스가 얼마만큼 고객 수를 지속가능한 수준으로 보유 할 수 있는지 측정하는 방법으로
광고/마케팅이 아니라 본질적인 Organic MAU 증가를 위한 지표!!  

**Total Costomer**의 수는 오늘 들어오는 유저 수와 오늘 나가는 유저 수로 결정되며,
**Active** 유저와 **Chum** 유저의 기준을 잘 정해야함. CC가 본질적인 MAU 값이 될 수 있는 척도.  

결국 **매일 새로 들어오는 유저 수**, **매일 잃게 되는 유저의 비율** 을 개선하는 프로젝트

<br>
{{<alert>}}
<a href="https://elecbrandy.github.io/tags/러닝스푼즈/">📖 러닝스푼즈X새싹 유니콘 기업 현직자에게 배우는 IT 서비스 기획자 취업캠프</a>
{{</alert>}}