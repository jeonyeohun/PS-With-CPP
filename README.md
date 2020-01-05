# Maeil Maeil Coding!
## Daily Problem Solving in C++
### Rules
* 매일매일 한문제씩 푼다.
* 1시간동안 고민해보고 안풀리면 솔루션을 찾아본다.
* 솔루션 코드에 주석을 달면서 분석한다.
* 내 코드로 다시 작성한다.
* 내꺼에도 주석달고 솔루션 보고 작성한건 커밋하면서 태그 붙여놓는다.
* 리드미에 접근 방법 기록한다. 틀린 접근방법도 기록한다.
* _(중요)_ 오늘도 부지런히 한 문제를 푼 나를 칭찬한다.

* * *

### 2019.12.18 수요일
#### [2775번: 부녀회장이 될테야](https://www.acmicpc.net/problem/2775)
~~~
평소 반상회에 참석하는 것을 좋아하는 주희는 이번 기회에 부녀회장이 되고 싶어 각 층의 사람들을 불러 모아 반상회를 주최하려고 한다. 이 아파트에 거주를 하려면 조건이 있는데, “a층의 b호에 살려면 자신의 아래(a-1)층의 1호부터 b호까지 사람들의 수의 합만큼 사람들을 데려와 살아야 한다” 는 계약 조항을 꼭 지키고 들어와야 한다. 
아파트에 비어있는 집은 없고 모든 거주민들이 이 계약 조건을 지키고 왔다고 가정했을 때, 주어지는 양의 정수 k와 n에 대해 k층에 n호에는 몇 명이 살고 있는지 출력하라. 단, 아파트에는 0층부터 있고 각층에는 1호부터 있으며, 0층의 i호에는 i명이 산다. 첫 번째 줄에 Test case의 수 T가 주어진다. 
그리고 각각의 케이스마다 입력으로 첫 번째 줄에 정수 k, 두 번째 줄에 정수 n이 주어진다. (1 <= k <= 14, 1 <= n <= 14) 각각의 Test case에 대해서 해당 집에 거주민 수를 출력하라.
~~~
* 접근 방법 1: 규칙을 보아하니 팩토리얼로 푸는 것 같아서 각 층을 팩토리얼로 매핑을 해두고 나중에 다 더하려고 했는데 문제를 완전 잘못 이해하고 있었다.. 나는 B호의 이전까지의 모든 거주민의 합을 구하는 것인줄 알았는데, A-1층에서 B번째 방까지 있는 사람의 수를 합치는 것이었다..팩토리얼로 어떻게 해보려다가 시간만 많이 낭비했다.

* 접근 방법 2: 새로 생각한 방법은 전체 14X14 배열에 거주민을 미리 맵핑해두고 어떤 n과 k가 들어오든 바로바로 값을 알려주면 되는 방법이었다. 일단 0층은 i와 같은 사람의 수가 있으니까 0층은 i대로 맵핑하고 다른 층은 k-1층에 있는 값들을 n열까지 더해서 넣어주었다.

* 두번째 방법으로 푸니까 잘 풀렸다. 그런데 제출할때 계속 틀렸다고 나와서 찾아보니 배열크기를 14X14가 아니라 15X14로 해야된다고 한다. 이걸 쓰면서 이유를 알았는데 층수는 0층부터 시작하고 호수는 1호 부터 시작하니까..!

#### [10250번: ACM 호텔](https://www.acmicpc.net/problem/10250)
~~~
ACM 호텔 매니저 지우는 손님이 도착하는 대로 빈 방을 배정하고 있다. 고객 설문조사에 따르면 손님들은 호텔 정문으로부터 걸어서 가장 짧은 거리에 있는 방을 선호한다고 한다. 여러분은 지우를 도와 줄 프로그램을 작성하고자 한다. 
즉 설문조사 결과 대로 호텔 정문으로부터 걷는 거리가 가장 짧도록 방을 배정하는 프로그램을 작성하고자 한다. 문제를 단순화하기 위해서 호텔은 직사각형 모양이라고 가정하자.
각 층에 W 개의 방이 있는 H 층 건물이라고 가정하자 (1 ≤ H, W ≤ 99). 그리고 엘리베이터는 가장 왼쪽에 있다고 가정하자(그림 1 참고). 
이런 형태의 호텔을 H × W 형태 호텔이라고 부른다. 호텔 정문은 일층 엘리베이터 바로 앞에 있는데, 정문에서 엘리베이터까지의 거리는 무시한다. 또 모든 인접한 두 방 사이의 거리는 같은 거리(거리 1)라고 가정하고 호텔의 정면 쪽에만 방이 있다고 가정한다. 
방 번호는 YXX 나 YYXX 형태인데 여기서 Y 나 YY 는 층 수를 나타내고 XX 는 엘리베이터에서부터 세었을 때의 번호를 나타낸다. 
즉, 그림 1 에서 빗금으로 표시한 방은 305 호가 된다. 손님은 엘리베이터를 타고 이동하는 거리는 신경 쓰지 않는다. 
다만 걷는 거리가 같을 때에는 아래층의 방을 더 선호한다. 예를 들면 102 호 방보다는 301 호 방을 더 선호하는데, 102 호는 거리 2 만큼 걸어야 하지만 301 호는 거리 1 만큼만 걸으면 되기 때문이다. 같은 이유로 102 호보다 2101 호를 더 선호한다. 
여러분이 작성할 프로그램은 초기에 모든 방이 비어있다고 가정하에 이 정책에 따라 N 번째로 도착한 손님에게 배정될 방 번호를 계산하는 프로그램이다. 첫 번째 손님은 101 호, 두 번째 손님은 201 호 등과 같이 배정한다. 그림 1 의 경우를 예로 들면, H = 6이므로 10 번째 손님은 402 호에 배정해야 한다.
~~~

* 접근 방법 : 일단 호텔 특성 상 아무리 층수가 높아져도 낮은 숫자의 호수가 먼저 채워진다. 그래서 일단 전체 방문객 수를 층수에서 나눠서 나온 몫을 호수로 하면 될 것 같다는 생각이 든다. 근데 이건 딱 나누어 떨어질 때 이야기고, 딱 안나누어 떨어지면서 층수보다 큰 숫자이면 몫+1을 해주어야지 제대로 된 호수가 나올 것이다. 그리고 전체 방문객수를 층수에서 나눈 나머지를 층수로 정하면 될 것 같다. 

* 예를 들어 이 호텔의 층수가 7이고 10번째 방문객의 방을 찾는다면 10/7 의 몫인 1에 방문객이 층수보다 크니까 1을 더해서 2호, 그리고 층수는 10%7인 3층으로 해서 결과가 302호가 나오게 된다.
* 반례를 생각해보자. 만약 방문객수가 층수로 딱 떨어진다면? 만약 7층짜리 호텔에 방문객이 14명이라고 치면 2로 나누어 떨어지는데 이때는 1을 더하지 않고 2로 호수를 정하고, 층수는 나머지가 0이 나올 때, 전체 층수로 바꿔주면 될 것 같은데..? 일단 코드 짜보고 반례나오면 더 생각해보자.

### 2019.12.19 목요일
#### [1993번: 분수찾기](https://www.acmicpc.net/problem/1193)
~~~
나열된 분수들을 1/1 -> 1/2 -> 2/1 -> 3/1 -> 2/2 -> … 과 같은 지그재그 순서로 차례대로 1번, 2번, 3번, 4번, 5번, … 분수라고 하자. 
X가 주어졌을 때, X번째 분수를 구하는 프로그램을 작성하시오.
~~~

* 접근 방법: 규칙을 찾아보려고 했는데 보니까 지그재그니까 홀수 행에서는 위로, 짝수행에서는 아래로 이동한다. 그리고 홀수 행에서는 분모가 1씩 늘어나고 분자가 1씩 줄어든다. 짝수 행에서는 분모가 1씩 줄어들고 분자가 1씩 늘어난다. 이 규칙을 수식화 하면 풀 수 있을 것 같다. 그리고 한번 이동할 때마다 열만큼 이동하면 된다. 주어진 숫자에 다다를때까지 이 규칙대로 계속 진행하면 결과를 바로 알 수 있을 것 같다. 

* 해결 후 : 해결하고 다른 사람이 짠 숏코딩을 봤는데 진짜 대단하다.. 접근 방법이 비슷해도 그걸 구현해내는 능력이 참 다른 것 같다. 15줄만에 끝내는 어떤 코드를 보면서 존경스러운 생각이 들었다..

### 2019.12.20 금요일
#### [4153번: 직각삼각형](https://www.acmicpc.net/problem/4153)
~~~
과거 이집트인들은 각 변들의 길이가 3, 4, 5인 삼각형이 직각 삼각형인것을 알아냈다. 주어진 세변의 길이로 삼각형이 직각인지 아닌지 구분하시오. 
입력은 여러개의 테스트케이스로 주어지며 마지막줄에는 0 0 0이 입력된다. 각 테스트케이스는 모두 30,000보다 작은 양의 정수로 주어지며, 
각 입력은 변의 길이를 의미한다. 각 입력에 대해 직각 삼각형이 맞다면 "right", 아니라면 "wrong"을 출력한다.
~~~

* 접근 방법: 직각삼각형은 a^2+b^2=c^2 의 식이 성립하는 삼각형이므로 입력 중 가장 긴 변을 c로 잡고 나머지 두 입력을 a와 b로 잡아 식에 대입해보고 직각삼각형 여부를 판별한다.

#### [3053번: 택시기하학](https://www.acmicpc.net/problem/3053)
~~~
19세기 독일 수학자 헤르만 민코프스키는 비유클리드 기하학 중 택시 기하학을 고안했다. 
택시 기하학에서 두 점 T1(x1,y1), T2(x2,y2) 사이의 거리는 다음과 같이 구할 수 있다. 
D(T1,T2) = |x1-x2| + |y1-y2|, 두 점 사이의 거리를 제외한 나머지 정의는 유클리드 기하학에서의 정의와 같다. 
따라서 택시 기하학에서 원의 정의는 유클리드 기하학에서 원의 정의와 같다. 

원: 평면 상의 어떤 점에서 거리가 일정한 점들의 집합. 
반지름 R이 주어졌을 때, 유클리드 기하학에서 원의 넓이와, 택시 기하학에서 원의 넓이를 구하는 프로그램을 작성하시오.
~~~

* 접근 방법: 이 문제는 기하학 자체가 나한테 생소해서 택시 기하학에 대한 자료를 찾아보고 해결했다.. 사실 찾아보니까 너무 생각을 안하고 찾아보기만 했다는 생각이 들긴 하다.. 일단 유클리드 기하학의 원의 형태가 택시 기하학에서는 정사각형이다. 결국 원의 지름이 정사각형의 대각선 길이와 같다. 정사각형의 대각선 공식은 (한변의 길이) X sqrt(2) 이기 때문에 입력으로 받은 반지름X2를 대각선 길이로 잡고 한변의 길이에 대한 식으로 전개하면 (한변의 길이)^2 = 2r^2 이 된다. 첫줄에는 원의 넓이인 PI X r^2 을, 두번쨰 줄에는 정사각형의 넓이인 2r^2을 출력한다.


### 2019.12.21 토요일
#### [1011번: Fly me to the Alpha Centauri](https://www.acmicpc.net/problem/1011)
~~~
우현이는 어린 시절, 지구 외의 다른 행성에서도 인류들이 살아갈 수 있는 미래가 오리라 믿었다. 그리고 그가 지구라는 세상에 발을 내려 놓은 지 23년이 지난 지금, 세계 최연소 ASNA 우주 비행사가 되어 새로운 세계에 발을 내려 놓는 영광의 순간을 기다리고 있다. 
그가 탑승하게 될 우주선은 Alpha Centauri라는 새로운 인류의 보금자리를 개척하기 위한 대규모 생활 유지 시스템을 탑재하고 있기 때문에, 그 크기와 질량이 엄청난 이유로 최신기술력을 총 동원하여 개발한 공간이동 장치를 탑재하였다. 
하지만 이 공간이동 장치는 이동 거리를 급격하게 늘릴 경우 기계에 심각한 결함이 발생하는 단점이 있어서, 이전 작동시기에 k광년을 이동하였을 때는 k-1 , k 혹은 k+1 광년만을 다시 이동할 수 있다. 

예를 들어, 이 장치를 처음 작동시킬 경우 -1 , 0 , 1 광년을 이론상 이동할 수 있으나 사실상 음수 혹은 0 거리만큼의 이동은 의미가 없으므로 1 광년을 이동할 수 있으며, 그 다음에는 0 , 1 , 2 광년을 이동할 수 있는 것이다. ( 여기서 다시 2광년을 이동한다면 다음 시기엔 1, 2, 3 광년을 이동할 수 있다. ) 김우현은 공간이동 장치 작동시의 에너지 소모가 크다는 점을 잘 알고 있기 때문에 x지점에서 y지점을 향해 최소한의 작동 횟수로 이동하려 한다. 

하지만 y지점에 도착해서도 공간 이동장치의 안전성을 위하여 y지점에 도착하기 바로 직전의 이동거리는 반드시 1광년으로 하려 한다. 
김우현을 위해 x지점부터 정확히 y지점으로 이동하는데 필요한 공간 이동 장치 작동 횟수의 최솟값을 구하는 프로그램을 작성하라.
~~~

* 접근 방법: 아무리 생각해도 규칙이 찾아지지가 않아서 솔루션을 찾아봤다. 워프하는 거리로 봤을 때, 갈 수 있는 최대거리가 N^2만큼, 그리고 워프 횟수는 2XN-1 이 나온다. 따라서, y-x를 해서 얻은 거리를 최대 이동거리로 나누고 난 나머지가 추가로 가야하는 거리가 되는데, 이 거리는 남은 거리/워프횟수를 올림하면 구할 수 있다. 이 것을 일반화해서 풀면 쉽게 풀리는 문제였다.

* 해결 후: 솔루션을 보고 얻은 것은 for 반복문을 for(;;jum++) 로 쓰면서 while을 무한반복문으로 만들면서 i를 컨트롤해줘야하는 번거로움을 쉽게 해결한 부분이었다. 그리고 테스트 케이스도 번거롭게 for 반복문으로 돌리는게 아니라 while(t--)로 0이되면 바로 끝내는 방식으로 구성하니 훨씬 깔끔하게 코드를 만들 수 있었다. 규칙을 찾는 문제는 항상 어렵게 늦게지는데 소루션을 제시한 사람처럼 표를 만들어서 천천히 규칙을 찾아내는 방식이 좋은 것 같다.
 
 ### 2019.12.22 일요일
 #### [1002번: 터렛](https://www.acmicpc.net/problem/1002)
~~~
조규현과 백승환은 터렛에 근무하는 직원이다. 하지만 워낙 존재감이 없어서 인구수는 차지하지 않는다. 다음은 조규현과 백승환의 사진이다. 
이석원은 조규현과 백승환에게 상대편 마린(류재명)의 위치를 계산하라는 명령을 내렸다. 조규현과 백승환은 각각 자신의 터렛 위치에서 현재 적까지의 거리를 계산했다. 

조규현의 좌표 (x1, y1)와 백승환의 좌표 (x2, y2)가 주어지고, 조규현이 계산한 류재명과의 거리 r1과 백승환이 계산한 류재명과의 거리 r2가 주어졌을 때, 류재명이 있을 수 있는 좌표의 수를 출력하는 프로그램을 작성하시오.
~~~

* 접근 방법: 두 터렛의 공격범위가 겹치는 점을 구하면 되는 문제인 것 같다. 원의 교점에 대한 내용을 다 잊어버려서 구글링을 통해서 규칙을 찾아보았다.

* 규칙: r1, r2 가 두 원의 반지름이고 d가 두원의 중심 사이의 거리를 의미할 때, 
   + 두 원이 만나지 않는 경우
     1. r1 + r2 < d
     2. r1 - r2 > d
     3. d = 0
   + 두 원이 한 점에서 만나는 경우
     1. r1 + r2 = d
     2. r1 - r2 = d
   + 두 원이 두 점에서 만나는 경우
     1. r1 - r2 < d < r1 + r2
   + 그리고 두 원이 일치하는 경우는 중심점 좌표가 같으면서 반지름이 같은 경우이다.

이 규칙을 코드로 잘 풀어내면 해결 할 수 있을 것 같다.

### 2019.12.23 월요일
#### [2920번: 음계](https://www.acmicpc.net/problem/2920)
~~~
다장조는 c d e f g a b C, 총 8개 음으로 이루어져있다. 이 문제에서 8개 음은 다음과 같이 숫자로 바꾸어 표현한다. c는 1로, d는 2로, ..., C를 8로 바꾼다. 1부터 8까지 차례대로 연주한다면 ascending, 8부터 1까지 차례대로 연주한다면 descending, 둘 다 아니라면 mixed 이다. 연주한 순서가 주어졌을 때, 이것이 ascending인지, descending인지, 아니면 mixed인지 판별하는 프로그램을 작성하시오.
~~~

* 접근 방법: 단순한 문제였다. 그냥 소팅을 확인하면 되는 문제라 쉽게 해결했다. 배열의 요소들이 1씩 늘어나거나 1씩 줄어들 때마다 오름차순, 내림차순 카운트를 하나씩 올리고 최종적으로 7개가 되는 플래그를 정답으로 선택하면 된다. 

#### [2953번: 나는 요리사다](https://www.acmicpc.net/problem/2953)
~~~
"나는 요리사다"는 다섯 참가자들이 서로의 요리 실력을 뽐내는 티비 프로이다. 각 참가자는 자신있는 음식을 하나씩 만들어오고, 서로 다른 사람의 음식을 점수로 평가해준다. 점수는 1점부터 5점까지 있다. 각 참가자가 얻은 점수는 다른 사람이 평가해 준 점수의 합이다. 이 쇼의 우승자는 가장 많은 점수를 얻은 사람이 된다. 각 참가자가 얻은 평가 점수가 주어졌을 때, 우승자와 그의 점수를 구하는 프로그램을 작성하시오.
~~~

*  접근 방법: 이것도 단순한 문제. 그냥 총점을 배열에 집어넣고 최댓값의 인덱스를 찾으면 된다. 

#### [1159번: 농구 경기](https://www.acmicpc.net/problem/1159)
~~~
상근이는 농구의 세계에서 점차 영향력을 넓혀가고 있다. 처음에 그는 농구 경기를 좋아하는 사람이었다. 농구에 대한 열정은 그를 막을 수 없었고, 결국 상근이는 농구장을 청소하는 일을 시작했다. 상근이도 농구장을 청소하면서 감독이 되기 위해 가져야할 능력을 공부해나갔다. 서당개 3년이면 풍월을 읊듯이 상근이는 점점 감독으로 한 걸음 다가가고 있었다. 어느 날 그에게 지방의 한 프로농구팀을 감독할 기회가 생기게 되었다. 그는 엄청난 지도력을 보여주며 프로 리그에서 우승을 했고, 이제 국가대표팀의 감독이 되었다. 내일은 일본과 국가대표 친선 경기가 있는 날이다. 상근이는 내일 경기에 나설 선발 명단을 작성해야 한다. 국가대표팀의 감독이 된 이후에 상근이는 매우 게을러졌다. 그는 선수의 이름을 기억하지 못하고, 각 선수의 능력도 알지 못한다. 따라서, 누가 선발인지 기억하기 쉽게 하기 위해 성의 첫 글자가 같은 선수 5명을 선발하려고 한다. 만약, 성의 첫 글자가 같은 선수가 5명보다 적다면, 상근이는 내일 있을 친선 경기를 기권하려고 한다. 상근이는 내일 경기를 위해 뽑을 수 있는 성의 첫 글자를 모두 구해보려고 한다.
~~~

* 접근 방법: 어차피 각 이름의 첫 글자만 필요하니까 벡터에 첫 글자를 넣고 중복되는 글자가 나올때마다 횟수 카운터만 올려준다. 최종적으로는 횟수가 5개 이상인 글자들만 출력한다.

#### [2799번: 블라인드](https://www.acmicpc.net/problem/2799)
~~~
봄이 오고 있다. 해는 높이 떠서 환하게 빛나고 있다. 사람들은 햇볕을 가리기 위해 블라인드를 내린다. 상근이는 이웃들이 무엇을 하는지를 염탐하고, 이것에 대해서 뒷담화를 하는 주부이다. 올해는 건너편 아파트에 사는 사람들이 블라인드를 얼마나 내리는지를 조사하려고 한다. 모든 창문은 4X4 그리드로 나타낼 수 있고, 별문자를 이용해서 블라인드를 나타낸다. 상근이가 볼 수 있는 창문은 다음 5가지 상태 중 하나이다. 건너편 아파트의 한 층에는 N개의 창문이 있고, 총 M층 건물이다. 현재 건너편 아파트의 창문 상태가 주어졌을 때, 위의 5가지 상태가 각각 몇 번 나오는지 구하는 프로그램을 작성하시오.
~~~

* 접근 방법: 배열에 문자를 쭉 넣어두고 별의 갯수를 세면서 어떤 타입인지 판정한다.

#### [5397번: 키로거](https://www.acmicpc.net/problem/5397)
~~~
창영이는 강산이의 비밀번호를 훔치기 위해서 강산이가 사용하는 컴퓨터에 키로거를 설치했다. 며칠을 기다린 끝에 창영이는 강산이가 비밀번호 창에 입력하는 글자를 얻어냈다. 키로거는 사용자가 키보드를 누른 명령을 모두 기록한다. 따라서, 강산이가 비밀번호를 입력할 때, 화살표나 백스페이스를 입력해도 정확한 비밀번호를 알아낼 수 있다. 강산이가 비밀번호 창에서 입력한 키가 주어졌을 때, 강산이의 비밀번호를 알아내는 프로그램을 작성하시오. 첫째 줄에 테스트 케이스의 개수가 주어진다. 각 테스트 케이스는 한줄로 이루어져 있고, 강산이가 입력한 순서대로 길이가 L인 문자열이 주어진다. (1 ≤ L의 길이 ≤ 1,000,000) 강산이가 백스페이스를 입력했다면, '-'가 주어진다. 이때 커서의 바로 앞에 글자가 존재한다면, 그 글자를 지운다. 화살표의 입력은 '<'와 '>'로 주어진다. 이때는 커서의 위치를 움직일 수 있다면, 왼쪽 또는 오른쪽으로 1만큼 움직인다. 나머지 문자는 비밀번호의 일부이다. 물론, 나중에 백스페이스를 통해서 지울 수는 있다. 만약 커서의 위치가 줄의 마지막이 아니라면, 그 문자를 입력하고, 커서는 오른쪽으로 한 칸 이동한다.
~~~

* 접근 방법: 링크드 리스트로 커서를 구현해서 주어진 조건에 따라 문자를 삽입한다. list 라이브러리를 사용해서 해결했는데, erase 할 때 커서 위치를 수정하는것, 그리고 '>' 기능과 '<', '-' 기능이 리스트의 양끝에서 적용되는 것에 대한 예외처리 때문에 조금 애를 먹긴했다.

#### [10870번: 피보나치 수 5](https://www.acmicpc.net/problem/10870)
* 재귀함수 연습문제이다. 너무 간단한 문제라서 풀었다는 기록만 남기고 생략한다.

### 2019.12.26 목요일
#### [11478번: 서로 다른 부분 문자열](https://www.acmicpc.net/problem/11478)
~~~
문자열 S가 주어졌을 때, S의 서로 다른 부분 문자열의 개수를 구하는 프로그램을 작성하시오. 부분 문자열은 S에서 연속된 일부분을 말하며, 길이가 1보다 크거나 같아야 한다. 예를 들어, ababc의 부분 문자열은 a, b, a, b, c, ab, ba, ab, bc, aba, bab, abc, abab, babc, ababc가 있고, 서로 다른것의 개수는 12개이다.
~~~

* 접근 방법: 일단 중복된 문자열을 허용하지 않기 때문에 set자료구조를 사용하기로 했다. 그리고 string 라이브러리에 포함된 substr을 사용하여 첫 글자부터 그 다음 글자들을 부분 문자열로 가져올 문자열 길이를 1씩 늘려가며 모두 가져와 set에 넣어주었다. 이렇게 하면 가능한 모든 부분 문자열이 중복없이 set에 들어가고 최종적으로는 set의 사이즈를 출력하면 될 것이다. 

#### [6321번: IBM 뺴기 1](https://www.acmicpc.net/problem/6321)
~~~
'2001: 스페이스 오디세이'는 아서 C. 클라크의 소설이자 스탠리 큐브릭 감독의 영화이다. 이 작품에서 우주선은 토성으로 가고 있다. 긴 여행동안 선원들은 모두 정체 상태에 빠져있고, 두 선원은 깨어나 있다. 우주선은 인공지능 컴퓨터 HAL이 조정하고 있다. HAL은 점점 이상하게 행동하더니 선원들을 죽이기 시작했다. 자세한 이야기는 소설을 읽거나 영화를 보면 알 수 있다. 영화가 유명해지고 난 이후에 사람들은 '2001: 스페이스 오디세이'에 나오는 인공지능 컴퓨터인 HAL의 뜻에 관심을 가졌다. HAL은 휴리스틱 알고리즘 (Heuristic ALgorithm)의 약자이다. 하지만, HAL의 각 글자를 알파벳 다음 순서로 쓰면 IBM이 되기 때문에, IBM과 연관이 있다고 믿는 사람이 매우 많다. 컴퓨터의 이름이 주어졌을 때, 각 글자를 알파벳 다음 순서로 써서 출력하는 프로그램을 작성하시오.
~~~

* 접근 방법: 아스키 코드 연산으로 쉽게 해결할 수 있을 것 같다. 조건에 이름의 최대길이가 50이라고 주어져서 문자열 길이에 대해 신경쓸 필요도 없고 Z문자가 있으면 아스키코드 대문자 A의 바로 이전이 64로 문자를 바꿔주면 된다.

#### [4659번: 비밀번호 발음하기](https://www.acmicpc.net/problem/4659)
~~~
좋은 패스워드를 만드는것은 어려운 일이다. 대부분의 사용자들은 buddy처럼 발음하기 좋고 기억하기 쉬운 패스워드를 원하나, 이런 패스워드들은 보안의 문제가 발생한다. 어떤 사이트들은 xvtpzyo 같은 비밀번호를 무작위로 부여해 주기도 하지만, 사용자들은 이를 외우는데 어려움을 느끼고 심지어는 포스트잇에 적어 컴퓨터에 붙여놓는다. 가장 이상적인 해결법은 '발음이 가능한' 패스워드를 만드는 것으로 적당히 외우기 쉬우면서도 안전하게 계정을 지킬 수 있다. 회사 FnordCom은 그런 패스워드 생성기를 만들려고 계획중이다. 당신은 그 회사 품질 관리 부서의 직원으로 생성기를 테스트해보고 생성되는 패스워드의 품질을 평가하여야 한다. 높은 품질을 가진 비밀번호의 조건은 다음과 같다. 1. 모음(a,e,i,o,u) 하나를 반드시 포함하여야 한다. 2. 모음이 3개 혹은 자음이 3개 연속으로 오면 안 된다. 3. 같은 글자가 연속적으로 두번 오면 안되나, ee 와 oo는 허용한다. 이 규칙은 완벽하지 않다;우리에게 친숙하거나 발음이 쉬운 단어 중에서도 품질이 낮게 평가되는 경우가 많이 있다.
~~~

* 접근 방법: 문자열을 읽어와서 하나씩 문자형 변수로 읽으면서 조건을 모두 검사한다. 각 조건마다 플래그 변수를 두어서 최종적으로 플래그가 모두 통과조건에 해당할 경우에만 acceptable로 판정한다. 자음모음 여부는 해당 문자가 a, e, i, o, u 중 하나면 모음으로, 아니면 자음으로 판정하고 모음이 하나라도 나오면 1번 조건에 대한 플래그를 킨다. 그리고 자음모음이 연달아 나올때마다 그 갯수를 세서 3이 넘으면 2번 조건에 대한 플래그를 키고 두 글자가 연달아 나오면 e나 o인지 확인하고 아닐경우에 플래그를 키는 방식으로 순회를 진행한다. 

#### [10757번: 큰 수 A+B](https://www.acmicpc.net/problem/10757)
~~~
A+B를 계산하시오. 첫째 줄에 A와 B가 주어진다. (0 < A,B < 1010000)
~~~

* 접근 방법: A 와 B의 범위가 매우 크기 때문에 long long int로 연산해도 오버플로우가 난다. 따라서 전공교과에서 배웠던 이진수 adder 컨셉을 그대로 구현하기로 했다. 코딩하면서 이걸 하게될 줄은 몰랐다 정말..문자열을 스택처럼 하나씩 꺼내면서 한자리씩 더하고 10을 넘어가면 carry out으로 다음자리에 넘겨주는 방식으로 연산을 진행했다.

#### [1476번: 날짜 계산](https://www.acmicpc.net/problem/1476)
~~~
준규가 사는 나라는 우리가 사용하는 연도와 다른 방식을 이용한다. 준규가 사는 나라에서는 수 3개를 이용해서 연도를 나타낸다. 각각의 수는 지구, 태양, 그리고 달을 나타낸다. 지구를 나타내는 수를 E, 태양을 나타내는 수를 S, 달을 나타내는 수를 M이라고 했을 때, 이 세 수는 서로 다른 범위를 가진다. (1 ≤ E ≤ 15, 1 ≤ S ≤ 28, 1 ≤ M ≤ 19) 우리가 알고있는 1년은 준규가 살고있는 나라에서는 1 1 1로 나타낼 수 있다. 1년이 지날 때마다, 세 수는 모두 1씩 증가한다. 만약, 어떤 수가 범위를 넘어가는 경우에는 1이 된다. 예를 들어, 15년은 15 15 15로 나타낼 수 있다. 하지만, 1년이 지나서 16년이 되면 16 16 16이 아니라 1 16 16이 된다. 이유는 1 ≤ E ≤ 15 라서 범위를 넘어가기 때문이다. E, S, M이 주어졌고, 1년이 준규가 사는 나라에서 1 1 1일때, 준규가 사는 나라에서 E S M이 우리가 알고 있는 연도로 몇 년인지 구하는 프로그램을 작성하시오.
~~~

* 접근 방법: 주어진 입력과 출력에 따라 규칙을 찾아보았을 때, 어떤 년도 i 에서 E를 빼고 E의 최댓값인 15로 나누어 떨어지고, 나머지 S와 M에 대해서도 똑같이 나누어 떨어지는 최솟값이 구하고자 하는 값이라는 것을 알았다. 코드로 옮길 때도 있는 그대로 i를 하나씩 올려가면서 i-E, i-S, i-M이 각각 15, 28, 19로 나누어 떨어지는 값을 구하여 출력한다.

#### [4150번: 피보나치 수](https://www.acmicpc.net/problem/4150)
~~~
피보나치 수열은 다음과 같이 그 전 두 항의 합으로 계산되는 수열이다. 첫 두 항은 1로 정의된다. f(1) = 1, f(2) = 1, f(n > 2) = f(n − 1) + f(n − 2) 정수를 입력받아, 그에 해당하는 피보나치 수를 출력하는 프로그램을 작성하여라.
~~~

* 접근 방법: long long 으로도 표현할 수 없는 큰 정수를 나타내야 한다. 앞서 큰 수 A+B에서 구현했던 알고리즘을 조금 수정해서 벡터 대신 string 자료형을 사용하는 것으로 수정하고 피보나치 수열을 계산할 때 사용하는 f(n-1) + f(n-2) 를 문자열을 이용한 더하기로 만들었다.

#### [6571번: 피보나치 수의 개수](https://www.acmicpc.net/problem/6571)
~~~
두 수 a와 b가 주어졌을 때, 구간 [a, b]에 포함되는 피보나치 수의 개수를 구하는 프로그램을 작성하시오.
~~~

* 접근 방법: 위와 똑같은데 범위 내에 있는 수의 개수를 찾는 문제이다. 이 문제는 테스트케이스가 여러번 들어오기 때문에 차라리 배열에 피보나치 수열을 맵핑해두고 테스트 케이스로 들어오는 범위 내에 있는 수의 갯수를 계산해서 출력하는 방식으로 구현했다. 피보나치 수열을 배열에 맵핑하는 함수, 범위 안에 있는지 확인해야하기 때문에 주어진 두 숫자 문자열 중 더 큰 숫자를 판단하는 함수가 필요하다.

#### [2751번: 수 정렬하기 2](https://www.acmicpc.net/problem/2751)
~~~
N개의 수가 주어졌을 때, 이를 오름차순으로 정렬하는 프로그램을 작성하시오.
~~~

* 접근 방법: 이 문제는 옛날에 자바로 풀다가 너무 안풀려서 포기한 문제였다. 사실 안풀린다기 보다는 퀵소트를 사용해야된다는 것을 알지만 직접 구현이 어려워 미뤄두었던 문제다. C++ 에서는 algorithm 라이브러리에 sort라는 함수가 지원되는데, 이 함수는 nlogn 의 시간복잡도를 가지는 퀵소트가 내부적으로 구성되어 있다. 따라서 그냥 벡터에 값을 쭉 넣어놓고 sort함수를 돌린 뒤에 순서대로 출력해주기만 하면 되었다. 문제를 제출하고 시간초과가 또 났었는데, cin 과 cout을 사용하다보니 데이터 양이 너무 많아 생기는 문제인 것 같아 iostream 대신 cstdio로 풀었더니 역시 해결되었다.

### 2019.12.27 금요일

#### [3052번: 나머지](https://www.acmicpc.net/problem/3052)
~~~
두 자연수 A와 B가 있을 때, A%B는 A를 B로 나눈 나머지 이다. 예를 들어, 7, 14, 27, 38을 3으로 나눈 나머지는 1, 2, 0, 2이다. 수 10개를 입력받은 뒤, 이를 42로 나눈 나머지를 구한다. 그 다음 서로 다른 값이 몇 개 있는지 출력하는 프로그램을 작성하시오.
~~~

* 접근 방법: set 자료구조을 사용하면 따로 알고리즘을 생각할 필요없이 중복된 값을 제외하고 unique한 값들로만 set을 채우기 때문에 10의 숫자를 각각 42로 나눈 나머지 값을 set에 insert시키고 최종적으로 set의 크기를 출력하면 된다.

#### [2846번: 오르막길](https://www.acmicpc.net/problem/2846)
~~~
상근이는 자전거를 타고 등교한다. 자전거 길은 오르막길, 내리막길, 평지로 이루어져 있다. 상근이는 개강 첫 날 자전거를 타고 가면서 일정 거리마다 높이를 측정했다. 상근이는 가장 큰 오르막길의 크기를 구하려고 한다. 측정한 높이는 길이가 N인 수열로 나타낼 수 있다. 여기서 오르막길은 적어도 2개의 수로 이루어진 높이가 증가하는 부분 수열이다. 오르막길의 크기는 부분 수열의 첫 번째 숫자와 마지막 숫자의 차이이다. 예를 들어, 높이가 다음과 같은 길이 있다고 하자. 12 3 5 7 10 6 1 11. 이 길에는 2 개의 오르막길이 있다. 밑 줄로 표시된 부분 수열이 오르막길이다. 첫 번째 오르막길의 크기는 7이고, 두 번째 오르막길의 크기는 10이다. 높이가 12와 6인 곳은 오르막길에 속하지 않는다. 가장 큰 오르막길을 구하는 프로그램을 작성하시오.
~~~

* 접근 방법: 탐색 알고리즘 아이디어를 생각했다. 탐색을 시작하는 출발 인덱스를 설정하고 내리막길을 만날때까지 인덱스를 증가시킨다. 내리막길을 만나면 오르막길의 끝 인덱스의 값과 출발 지점의 값의 차를 구해서 높이를 구하고 그 높이가 현재까지 구한 값들 중 최대 높이인지 확인한다. 탐색은 주어진 수열의 끝의 도달할때까지 진행하고 중복 탐색을 방지하기 위해서 한번 탐색이 끝나면 탐색 시작인덱스를 마지막으로 찾은 인덱스+1로 지정한다.

#### [3040번: 백설 공주와 일곱 난쟁이](https://www.acmicpc.net/problem/3040)
~~~
매일 매일 일곱 난쟁이는 광산으로 일을 하러 간다. 난쟁이가 일을 하는 동안 백설공주는 그들을 위해 저녁 식사를 준비한다. 백설공주는 의자 일곱개, 접시 일곱개, 나이프 일곱개를 준비한다. 어느 날 광산에서 아홉 난쟁이가 돌아왔다. (왜 그리고 어떻게 아홉 난쟁이가 돌아왔는지는 아무도 모른다) 아홉 난쟁이는 각각 자신이 백설공주의 일곱 난쟁이라고 우기고 있다. 백설공주는 이런 일이 생길 것을 대비해서, 난쟁이가 쓰고 다니는 모자에 100보다 작은 양의 정수를 적어 놓았다. 사실 백설 공주는 공주가 되기 전에 매우 유명한 수학자였다. 따라서, 일곱 난쟁이의 모자에 쓰여 있는 숫자의 합이 100이 되도록 적어 놓았다. 아홉 난쟁이의 모자에 쓰여 있는 수가 주어졌을 때, 일곱 난쟁이를 찾는 프로그램을 작성하시오. (아홉 개의 수 중 합이 100이 되는 일곱 개의 수를 찾으시오)
~~~

* 접근 방법: 처음에는 이것저것 이상하게 시도를 많이 해봤는데 잘 안돼서 단순하지만 확실한 방법으로 해결했다. 벡터에 입력을 모두 저장하고 모든 요소들을 이중 for 문으로 순회하면서 두 개의 요소의 값을 0으로 만든다. 어차피 입력은 1이상 99이하이므로 0이 들어올 일이 없어 괜찮다. 그리고 벡터의 요소들의 합을 구해 100인지 확인한다. 100이라면 0을 제외한 벡터 요소를 출력하고 프로그램을 종료한다. 0으로 만들었던 값은 다음 검사를 위해서 복구해줘야 하는데 임시로 기억시키기 보다는 그냥 새로운 벡터를 하나 만들어서 한 검사가 새로 시작될 때마다 기존 입력으로 받았던 벡터를 assign을 통해 복사해두고 검사를 진행했다.

#### [2783번: 삼각김밥](https://www.acmicpc.net/problem/2783)
~~~
유명 편의점 체인점 세븐25는 삼각 김밥을 전국에서 가장 싸게 판매하고 있다. 이 회사의 직원들은 삼각 김밥의 가격을 전국 최저가를 유지하기 위해 매일 근처의 편의점을 방문한다. 그리고 나서 세븐25의 삼각 김밥보다 싼 가격을 발견하면, 삼각 김밥의 가격을 그 가격으로 바꿔 최저가를 유지한다. 매일 아침, 점심, 저녁으로 삼각 김밥을 먹는 상근이와 정인이는 정말 세븐25가 제일 싼지 궁금해졌다. 이들은 학교 근처에 있는 세븐 25와 세븐 25를 제외한 서로 다른 N개의 편의점 체인을 방문 할 것이다. 이 편의점을 방문하면서 세븐25보다 싼 삼각김밥을 찾을 것이다. 또, 전체 편의점에서 가장 싼 삼각 김밥은 어디인지 찾을 것이다. 어느 편의점의 삼각 김밥이 제일 싼지 고객들이 쉽게 알지 못하기 하기 위해서, 모든 편의점은 삼각 김밥의 가격을 다음과 같이 표시한다. "삼각 김밥 Y그램 당 X원" 상근이와 정인이는 삼각 김밥을 1,000그램 살 것이다. 세븐 25의 삼각 김밥 가격과, 다른 N개 편의점의 삼각 김밥 가격이 주어졌을 때, 1,000그램의 삼각 김밥을 가장 싸게 사려면 얼마면 되는지 구하는 프로그램을 작성하시오. 삼각 김밥은 여러 군데에서 돌아가면서 사도 되고, 세븐 25와 N개 편의점 이외의 다른 곳에서는 살 수 없다.
~~~

* 접근 방법: 사실 거스름돈 문제와 비슷한 전개로 가야한다고 생각해서 벡터도 두개만들고 이리저리 삽질을 하다가 문제를 다시 보니 이런게 아닌것 같아서 1그램당 가격을 구하고 가장 싼 가격으로 1000그램을 만드는 방식으로 풀었더니 풀렸다. 엄청 간단한 문제였는데 너무 복잡하게 생각한 것 같고 잠깐 쉬다가 다시 하니까 머리가 잘 돌아가는 것 같다.

### 2019.12.29 일요일
#### [3000번: 직각 삼각형](https://www.acmicpc.net/problem/3000)
~~~
좌표 평면에 점 N개가 있다. 이때, 빗변을 제외한 나머지 두 변이 좌표축에 평행한 직각삼각형을 이루는 점 3개를 고르는 방법을 수를 구하는 프로그램을 작성하시오. 직각삼각형은 한각이 직각인 삼각형이며, 직각의 대변을 빗변이라고 한다.
~~~

* 접근 방법 1: 처음 시도했던 방법은 빗변의 갯수를 구하는 방법이었다. 좌표축과 평행하려면 각 3개의 x, y좌표 중 적어도 각각 두 개의 좌표가 같은 위치에 있어야 한다. 따라서 겹치는 점이 아예 없는 좌표들을 빗변으로 생각하고 만들어진 빗변의 양끝점의 x나 y좌표와 일치하는 점을 찾는 방법을 시도했다. 결과는 시간초과였다.

* 접근 방법 2: 좌표축과 평행한 직각삼각형은 두 x좌표가 같은 위치에 있고 동시에 동시에 두 y좌표가 같은 점에 있는 삼각형이다. 그리고 동시에 두 점이 겹치면 안된다. 그래서 각 좌표를 순회하면서 해당 좌표의 x, y에 대해 동일한 x좌표의 갯수, 동일한 y좌표의 갯수를 구한 뒤 두 값을 곱하면 두 x좌표와 y좌표가 겹치는 세개의 좌표의 경우의 수를 구할 수 있다. 결과는 실패..

* 접근 방법 3: 입력이 최대 100000까지 들어오기 때문에 int 형을 long long int 로 바꾸고, 기준이 되는 좌표의 점까지 고려하면 같은 좌표를 가지는 3개의 점까지 경우의 수에 포함되기 때문에 삼각형이 아닌 직선의 좌표들이 들어가게 된다. 기준점 되는 좌표는 제외하고 갯수를 세었다. 결과는 정답!

### 2019.12.30 월요일
#### [15552번: 빠른 A+B](https://www.acmicpc.net/problem/15552)
* 빠른 입출력 연습용 문제. 별 다른 접근 방법이 필요없다.

#### [8958번: OX퀴즈](https://www.acmicpc.net/problem/8958)
~~~
"OOXXOXXOOO"와 같은 OX퀴즈의 결과가 있다. O는 문제를 맞은 것이고, X는 문제를 틀린 것이다. 문제를 맞은 경우 그 문제의 점수는 그 문제까지 연속된 O의 개수가 된다. 예를 들어, 10번 문제의 점수는 3이 된다. "OOXXOXXOOO"의 점수는 1+2+0+0+1+0+0+1+2+3 = 10점이다. OX퀴즈의 결과가 주어졌을 때, 점수를 구하는 프로그램을 작성하시오.
~~~
* 접근 방법: 연속된 갯수를 세는 변수하나를 만들어서 그 변수의 값과 O가 나올 때마다 1을 곱해서 점수를 계속 누적시키면서 더한다.

#### [1712번: 손익분기점](https://www.acmicpc.net/problem/1712)
~~~
월드전자는 노트북을 제조하고 판매하는 회사이다. 노트북 판매 대수에 상관없이 매년 임대료, 재산세, 보험료, 급여 등 A만원의 고정 비용이 들며, 한 대의 노트북을 생산하는 데에는 재료비와 인건비 등 총 B만원의 가변 비용이 든다고 한다. 예를 들어 A=1,000, B=70이라고 하자. 이 경우 노트북을 한 대 생산하는 데는 총 1,070만원이 들며, 열 대 생산하는 데는 총 1,700만원이 든다. 노트북 가격이 C만원으로 책정되었다고 한다. 일반적으로 생산 대수를 늘려 가다 보면 어느 순간 총 수입(판매비용)이 총 비용(=고정비용+가변비용)보다 많아지게 된다. 최초로 총 수입이 총 비용보다 많아져 이익이 발생하는 지점을 손익분기점(BREAK-EVEN POINT)이라고 한다. A, B, C가 주어졌을 때, 손익분기점을 구하는 프로그램을 작성하시오.
~~~

* 접근 방법 1: x를 증가시키면서 손익분기점을 넘는 갯수를 찾으려고 했는데 시간 초과가 됐다.

* 접근 방법 2: 손익 분기점을 찾는 공식이 있어 찾아보니 고정비용/가변비용-가격 을 계산하면 손익분기점에 대한 상품 갯수를 알 수 있는데, 여기서 손익 분기점에 정확히 도달하게되는 상품 갯수가 나오기 때문에 손익분기점을 넘지 못한다. 따라서 위 식에서 구한 갯수에 +1을 해준다. 손익분기점이 존재하지 않는 경우도 고려해야하는데, 분모가 되는 가변비용-가격이 0인경우, 그리고 손익분기점 갯수가 0으로 계산되는 경우는 손익분기점이 존재하지 않는 것이므로 -1를 출력하도록 한다.

#### [2798번: 블랙잭](https://www.acmicpc.net/problem/2798)
~~~
카지노에서 제일 인기 있는 게임 블랙잭의 규칙은 상당히 쉽다. 카드의 합이 21을 넘지 않는 한도 내에서, 카드의 합을 최대한 크게 만드는 게임이다. 블랙잭은 카지노마다 다양한 규정이 있다. 한국 최고의 블랙잭 고수 김정인은 새로운 블랙잭 규칙을 만들어 상근, 창영이와 게임하려고 한다. 김정인 버젼의 블랙잭에서 각 카드에는 양의 정수가 쓰여 있다. 그 다음, 딜러는 N장의 카드를 모두 숫자가 보이도록 바닥에 놓는다. 그런 후에 딜러는 숫자 M을 크게 외친다. 이제 플레이어는 제한된 시간 안에 N장의 카드 중에서 3장의 카드를 골라야 한다. 블랙잭 변형 게임이기 때문에, 플레이어가 고른 카드의 합은 M을 넘지 않으면서 M과 최대한 가깝게 만들어야 한다. N장의 카드에 써져 있는 숫자가 주어졌을 때, M을 넘지 않으면서 M에 최대한 가까운 카드 3장의 합을 구해 출력하시오.
~~~

* 접근 방법 : 브루트 포스 문제인것 같다. 어차피 N이 최대 100개까지 밖에 못들어오기 때문에 모든 경우의 수를 다 계산해도 시간초과는 나지 않을 것 같다. 반복문을 세 개 중첩해서 쓰면서 3개를 더해서 나올 수 있는 M이하의 최댓값을 구한다.

#### [1181번: 단어 정렬](https://www.acmicpc.net/problem/1181)
~~~
알파벳 소문자로 이루어진 N개의 단어가 들어오면 아래와 같은 조건에 따라 정렬하는 프로그램을 작성하시오. 1. 길이가 짧은 것부터 2. 길이가 같으면 사전 순으로
~~~

* 접근 방법 : C++에서 지원하는 sort함수는 nlogn 복잡도라서 따로 내가 구현할 필요없이 이 함수를 사용하면 될 것 같다. 전체 단어들을 벡터에 넣어두고 글자길이 순서대로 꺼내서 새로운 벡터에 넣고 같은 글자길이들 끼리 정렬을 해주어야하는데, 각 글자길이당 시작되는 벡터 인덱스를 소트 함수에 넣어주어서 글자 길이가 같은 단어들끼리만 소팅이 되게 하였다.

#### [350. Intersection of Two Arrays II](https://leetcode.com/problems/intersection-of-two-arrays-ii/)
~~~
Given two arrays, write a function to compute their intersection.
~~~

* 접근 방법: 조금이라도 효율적으로 해보려고 처음엔 벡터 두개를 합쳐서 중복되는 값의 갯수를 구해서 해결하려고 했는데, 생각해보니까 말도 안되는 방법이었다..두 벡터를 합쳐버리면 어떤 값이 어디에 속하는지 알 수가 없으니까..그래서 그냥 벡터를 복사해서 페어가 만들어지는 값을 날려버렸다. 이렇게 하면 기준이 되는 벡터의 인덱스에 문제가 생겨서 한번 erase 할 때마다 인덱스를 한자리씩 앞으로 당겨주면 된다.

#### [324. Wiggle Sort II](https://leetcode.com/problems/wiggle-sort-ii/)
~~~
Given an unsorted array nums, reorder it such that nums[0] < nums[1] > nums[2] < nums[3]....
~~~

* 접근 방법: 이 정렬 방법은 결국 배열이 정렬된 상태에서 짝수번째에 있는 위치에 삽입되면 해결된다. 따라서 우선 주어진 벡터를 sort함수로 정렬하고 맨 뒤에서부터 정해진 위치에 아이템을 insert하고 insert가 끝난 아이템은 pop_back하면 해결할 수 있다.

### 2019.12.31 화요일

#### [448. Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)
~~~
Given an array of integers where 1 ≤ a[i] ≤ n (n = size of array), some elements appear twice and others appear once. Find all the elements of [1, n] inclusive that do not appear in this array. Could you do it without extra space and in O(n) runtime? You may assume the returned list does not count as extra space.
~~~

* 접근 방법: 최대한 O(n)에 맞춘 방법을 생각하는게 어려웠다. 계속 고민하다가 discussion에서 힌트를 얻어 벡터에 이미 한번이라도 나온 숫자에 해당하는 인덱스를 마킹하는 방법으로 접근했다. 어차피 숫자는 1부터 최대 nums.size()까지만 들어오니까 똑같은 길이의 bool형 벡터를 만들고 nums의 요소를 하나씩 읽어서 nums[i]-1 인덱스를 true 로 마킹하면 최종적으로는 nums 배열에 포함되어 있지 않는 숫자에 해당하는 bool 벡터 인덱스 값이 모두 false로 마킹되어 있을 것이다. 이 인덱스 값에 +1을 하여 반환을 할 벡터에 추가한다.

#### [41. First Missing Positive](https://leetcode.com/problems/first-missing-positive/)
~~~
 Given an unsorted integer array, find the smallest missing positive integer.
~~~

* 접근 방법: 주어진 배열에 없는 정수의 최솟값을 구하기 위해서 먼저 배열을 정렬한다. 그리고 음수, 0은 무시해야하기 때문에 정수가 시작되는 지점을 구한다. 그리고 반복문을 돌릴 때, 제외된 음수와 0의 갯수만큼을 현재 배열에 최댓값에 더해서 나올 수 있는 최댓값을 설정한다. 이후에 i를 1부터 방금 구한 최댓값까지 올리면서 현재 배열안에 해당 값이 있는 지 확인하고 존재하지 않는 값을 i가 가지게 되면 i를 바로 리턴한다. 만약 배열의 끝에 도달할때까지 리턴되는 값이 없다면, 일단 배열에 정수가 존재하는지 확인한다. 이 경우는 배열이 정수없이 음수나 0으로만 이루어져 있을 경우 무조건 1을 리턴하게 하기 위한 검사이다. 그리고 만약 배열에 정수가 존재한다면 1부터 마지막 숫자까지 비어있는 정수가 없다는 의미이기 때문에 배열에서 가장 큰 정수인 nums[nums.size()-1]에 1을 더한 값을 리턴한다.

#### [12. Integer to Roman](https://leetcode.com/problems/integer-to-roman/)
~~~
Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000

For example, two is written as II in Roman numeral, just two one's added together. Twelve is written as, XII, which is simply X + II. The number twenty seven is written as XXVII, which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. 
Instead, the number four is written as IV. Because the one is before the five we subtract it making four. 
The same principle applies to the number nine, which is written as IX. 
There are six instances where subtraction is used:

I can be placed before V (5) and X (10) to make 4 and 9. 
X can be placed before L (50) and C (100) to make 40 and 90. 
C can be placed before D (500) and M (1000) to make 400 and 900.
Given an integer, convert it to a roman numeral. Input is guaranteed to be within the range from 1 to 3999.
~~~

* 접근 방법: 배열에 각 숫자와 로마자들을 미리 넣어두고 가장 큰 수인 1000부터 꺼내면서 num과 나누어 몫만큼의 로마자를 리턴할 문자열에 추가한다. 추가한 이후에는 num을 나머지로 줄여주어야지 반복을 끝낼 수 있다.

#### [1764번: 듣보잡](https://www.acmicpc.net/problem/1764)
~~~
문제
김진영이 듣도 못한 사람의 명단과, 보도 못한 사람의 명단이 주어질 때, 듣도 보도 못한 사람의 명단을 구하는 프로그램을 작성하시오.

입력
첫째 줄에 듣도 못한 사람의 수 N, 보도 못한 사람의 수 M이 주어진다. 이어서 둘째 줄부터 N개의 줄에 걸쳐 듣도 못한 사람의 이름과, N+2째 줄부터 보도 못한 사람의 이름이 순서대로 주어진다. 이름은 띄어쓰기 없이 영어 소문자로만 이루어지며, 그 길이는 20 이하이다. N, M은 500,000 이하의 자연수이다.

출력
듣보잡의 수와 그 명단을 사전순으로 출력한다.
~~~
* 접근 방법: 처음에는 벡터를 두개 사용해서 find함수를 통해 해결하려고 했는데, std::find 함수는 모든 배열 요소를 검사하는 O(N^2) 의 복잡도를 가진다. 그래서 시간초과를 해결하기 위해 set을 사용하기로 했다. set 자료구조는 아이템이 들어갈 때마다 자동으로 정렬이 되고 이미 정렬된 배열이기 때문에 find함수도 이진탐색을 기반으로 한 O(log n) 의 복잡도를 가진다. 

### 2020.01.01 수요일
#### [1018번: 체스판 다시 칠하기](https://www.acmicpc.net/problem/1018)
~~~
문제
지민이는 자신의 저택에서 MN개의 단위 정사각형으로 나누어져 있는 M*N 크기의 보드를 찾았다. 어떤 정사각형은 검은색으로 칠해져 있고, 나머지는 흰색으로 칠해져 있다. 지민이는 이 보드를 잘라서 8*8 크기의 체스판으로 만들려고 한다.

체스판은 검은색과 흰색이 번갈아서 칠해져 있어야 한다. 구체적으로, 각 칸이 검은색과 흰색 중 하나로 색칠되어 있고, 변을 공유하는 두 개의 사각형은 다른 색으로 칠해져 있어야 한다. 따라서 이 정의를 따르면 체스판을 색칠하는 경우는 두 가지뿐이다. 하나는 맨 왼쪽 위 칸이 흰색인 경우, 하나는 검은색인 경우이다.

보드가 체스판처럼 칠해져 있다는 보장이 없어서, 지민이는 8*8 크기의 체스판으로 잘라낸 후에 몇 개의 정사각형을 다시 칠해야겠다고 생각했다. 당연히 8*8 크기는 아무데서나 골라도 된다. 지민이가 다시 칠해야 하는 정사각형의 최소 개수를 구하는 프로그램을 작성하시오.

입력
첫째 줄에 N과 M이 주어진다. N과 M은 8보다 크거나 같고, 50보다 작거나 같은 자연수이다. 둘째 줄부터 N개의 줄에는 보드의 각 행의 상태가 주어진다. B는 검은색이며, W는 흰색이다.

출력
첫째 줄에 지민이가 다시 칠해야 하는 정사각형 개수의 최솟값을 출력한다.
~~~
* 접근 방법 1: 처음에는 각 행의 첫 자리를 홀수번째 열, 짝수번째 열과 비교하며 바꿔야하는 자리를 찾는 방법으로 해결하려고 했는데, 틀렸습니다가 계속 나왔다. 그래서 반례를 찾아보니 만약 (0, 0) 자리의 말만 바꾸면 해결되는 경우가 있을 수 있기 때문에 이 방법은 잘못된 방법이라는 것을 알았다.

* 접근 방법 2: 단순하지만 효과적인 방법으로 W로 시작하는 8X8 정답 판과 B로 시작하는 8X8정답판을 미리 만들어두고 두 판 중 주어진 8X8 윈도우 안에 고쳐야할 말이 더 적은 경우를 선택하도록 했다. 처음에는 이렇게 하는게 비효율적이라는 생각이 들었는데 생각해보니까 브루트 포스가 원래 단순해도 확실한 방법이 아니겠는가!

#### [1436번: 영화감독 숌](https://www.acmicpc.net/problem/1436)
~~~
문제
666은 종말을 나타내는 숫자라고 한다. 따라서, 많은 블록버스터 영화에서는 666이 들어간 제목을 많이 사용한다. 영화감독 숌은 세상의 종말 이라는 시리즈 영화의 감독이다. 조지 루카스는 스타워즈를 만들 때, 스타워즈 1, 스타워즈 2, 스타워즈 3, 스타워즈 4, 스타워즈 5, 스타워즈 6과 같이 이름을 지었고, 피터 잭슨은 반지의 제왕을 만들 때, 반지의 제왕 1, 반지의 제왕 2, 반지의 제왕 3과 같이 영화 제목을 지었다.

하지만 숌은 자신이 조지 루카스와 피터 잭슨을 뛰어넘는다는 것을 보여주기 위해서 영화 제목을 좀 다르게 만들기로 했다.

종말의 숫자란 어떤 수에 6이 적어도 3개이상 연속으로 들어가는 수를 말한다. 제일 작은 종말의 숫자는 666이고, 그 다음으로 큰 수는 1666, 2666, 3666, .... 과 같다.

따라서, 숌은 첫 번째 영화의 제목은 세상의 종말 666, 두 번째 영화의 제목은 세상의 종말 1666 이렇게 이름을 지을 것이다. 일반화해서 생각하면, N번째 영화의 제목은 세상의 종말 (N번째로 작은 종말의 숫자) 와 같다.

숌이 만든 N번째 영화의 제목에 들어간 숫자를 출력하는 프로그램을 작성하시오. 숌은 이 시리즈를 항상 차례대로 만들고, 다른 영화는 만들지 않는다.

입력
첫째 줄에 숫자 N이 주어진다. N은 10,000보다 작거나 같은 자연수이다.

출력
첫째 줄에 N번째 영화의 제목에 들어간 수를 출력한다.
~~~
* 접근 방법: 사실 나머지 연산으로 해도 될 것 같긴 한데, 문자열로 처리하는게 제일 간단해보여서 나는 i를 0부터 계속 증가시키면서 i를 문자열로 변환하고 해당 문자열에 666이 포함되어 있는지 확인하는 방법을 시도했다. string 라이브러리의 substr() 함수는 substring을 찾으면 그 string을 반환하고, 찾지 못하면 string::npos를 반환하기 때문에, npos를 제외하고 어떤 값이라도 반환이 되면 카운트를 하나씩 올리고 이 카운트 변수가 입력으로 받은 N과 일치하면 반복을 종료하고 마지막으로 받았던 문자열을 출력하도록 한다.

### 2020.01.02 목요일
#### [13. Roman to Integer](https://leetcode.com/problems/roman-to-integer/)
~~~
Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
For example, two is written as II in Roman numeral, just two one's added together. Twelve is written as, XII, which is simply X + II. The number twenty seven is written as XXVII, which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:

I can be placed before V (5) and X (10) to make 4 and 9. 
X can be placed before L (50) and C (100) to make 40 and 90. 
C can be placed before D (500) and M (1000) to make 400 and 900.
Given a roman numeral, convert it to an integer. Input is guaranteed to be within the range from 1 to 3999.
~~~
* 접근 방법: 10진수 -> 로마자를 만들었을 때처럼 배열에 모든 정보를 미리 맵핑해두고 prefix가 될 수 있는 로마자인 I, X, C가 나오면 바로 다음에 위치한 문자와 합쳐서 사용가능한 문자인지 확인하고 점수를 계산한다. 만약에 사용이 가능하다면 다음 검사는 바로 다음 문자가 아니라 2칸 뒤에 떨어져있는 문자가 되어야하기 때문에 반복문 컨트롤을 잘 해주어야 한다.

#### [14. Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/)
~~~
Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".
~~~
* 접근 방법: 먼저, 주어진 단어들 중 길이가 가장 짧은 단어를 찾아서 그 단어를 기준으로 common prefix를 검사한다. 왜냐하면 어차피 단어길이가 가장 짧은 단어의 길이를 넘어가면 common prefix를 찾는것이 의미가 없기 때문이다. 길이를 찾고 각 단어의 n 번째 문자를 차례대로 검사하면서 공통되는 문자가 나오면 리턴할 문자열에 집어넣는다. 그리고 만약 공통되지 않는 글자가 나오면 바로 지금까지 넣어둔 결과 문자열을 리턴한다.

#### [686. Repeated String Match](https://leetcode.com/problems/repeated-string-match/)
~~~
Given two strings A and B, find the minimum number of times A has to be repeated such that B is a substring of it. If no such solution, return -1.

For example, with A = "abcd" and B = "cdabcdab".

Return 3, because by repeating A three times (“abcdabcdabcd”), B is a substring of it; and B is not a substring of A repeated two times ("abcdabcd").

Note:
The length of A and B will be between 1 and 10000.
~~~

* 접근 방법: 단순히 A를 계속 누적해서 더해가면서 find 함수를 통해 부분 문자열의 존재 여부를 확인하는 방법을 선택했다. 문제를 풀면서 까다로웠던 부분은 no solution 판정을 어느 시점에서 할 것인가 인데, 누적된 A의 문자열 길이가 A의 초기 문자열 길이+ B의 길이가 되면 앞으로 이어질 문자열은 이미 모든 부분 문자열의 경우의 수가 다 나온 상태이기 때문에 이떄까지 결과가 안나오면 no solution으로 판정하고 -1을 반환하도록 했다.

#### [67. Add Binary](https://leetcode.com/problems/add-binary/)
~~~
Given two binary strings, return their sum (also a binary string).

The input strings are both non-empty and contains only characters 1 or 0.
~~~
* 접근 방법: one bit adder를 구현하면 된다. carry out이랑 자릿수가 다른 이진수 끼리의 덧셈할 때 인덱스 예외만 잘 처리해주면 된다.

#### [6. ZigZag Conversion](https://leetcode.com/problems/zigzag-conversion/)
~~~
The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

P   A   H   N
A P L S I I G
Y   I   R
And then read line by line: "PAHNAPLSIIGYIR"

Write the code that will take a string and make this conversion given a number of rows:

string convert(string s, int numRows);
~~~
* 접근 방법: 2차원 배열을 만들어두고 문제에서 주어진 조건대로 배열에 문자를 하나씩 집어 넣으 이후에 배열을 순서대로 출력하는 방법으로 해결했다. 행과 열의 인덱스를 규칙에 따라 바꾸어주어야하는데, row가 1씩 증가하는 것을 default 조건으로 만들고 row가 numRows-1에 도달하면 대각선으로 이동하도록 인덱스를 증감시키고 row가 다시 0에 도달하면 원래대로 행만 변경하면서 직선으로 내려오도록 인덱스를 증감시켰다. numRows가 1로 들어올 때 zero division에 대한 예외처리 때문에 애를 먹었는데, 결국 단순하게 생각해보면 numrows가 1이라는 것은 입력으로 들어온 문자열이 그대로 출력되는 것을 의미하기 때문에 파라미터로 들어온 문자열을 그대로 반환하는 것으로 해결했다.

### 2020.01.03 금요일
#### [155. Min Stack](https://leetcode.com/problems/min-stack/)
~~~
Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

push(x) -- Push element x onto stack.
pop() -- Removes the element on top of the stack.
top() -- Get the top element.
getMin() -- Retrieve the minimum element in the stack.
~~~

* 접근 방법: 스택을 구현하는데 백터를 사용하는게 뭔가 아이러니하긴 하지만 아이템을 push하고 pop하는 과정은 벡터로 쉽게 구현이 가능했다. 그냥 push_back()과 pop_back()을 사용하면 되니까..결국 최솟값을 구하는 것을 최소한의 시간을 가지고 해야하는데 문제는 pop 기능이 있기 때문에 최솟값이 업데이트 되기 이전의 값으로 되돌릴 경우도 있다는 것이다. 이것을 해결하기 위해서 벡터 하나를 더 만들어서 또 다른 스택처럼 최솟값을 계속 모아두었다가 pop하는 값이 모아둔 최솟값의 가장 top에 위치한 아이템과 같다면, 최솟값 스택도 같이 pop해주는 방법으로 해결했다.

#### [686. Baseball Game](https://leetcode.com/problems/baseball-game/)
~~~
You're now a baseball game point recorder.

Given a list of strings, each string can be one of the 4 following types:

Integer (one round's score): Directly represents the number of points you get in this round.
"+" (one round's score): Represents that the points you get in this round are the sum of the last two valid round's points.
"D" (one round's score): Represents that the points you get in this round are the doubled data of the last valid round's points.
"C" (an operation, which isn't a round's score): Represents the last valid round's points you get were invalid and should be removed.
Each round's operation is permanent and could have an impact on the round before and the round after.

You need to return the sum of the points you could get in all the rounds.
~~~
* 접근 방법: 벡터에 점수들을 모아두고 마지막에 벡터에 있는 수들의 합을 구해 리턴하는 방법으로 해결했다. 처음에는 isdigt()함수를 이용해서 숫자가 나왔을 때 벡터에 push하는 방법을 사용하려고 했는데, 테스트케이스 중에 음수가 나오는 케이스가 있었다. isdigit()은 음수, 실수를 모두 false 로 반환한다. 그래서 다른 조건들을 먼저 앞에 걸어두고 else 까지 오면 무조건 push 하는 것으로 로직을 수정했다. C가 나오면 pop_back을 통해서 마지막 수를 없애고, D가 나오면 벡터 마지막에 들어있는 수에 2를 곱한 값을 벡터에 push 한다. 그리고 +가 나오면 벡터 마지막에 위치한 두 수를 합친 값을 push 한다. 최종적으로 이렇게 모인 수들을 합쳐서 리턴한다.

#### [10989번: 수 정렬하기 3](https://www.acmicpc.net/problem/10989)
~~~
문제
N개의 수가 주어졌을 때, 이를 오름차순으로 정렬하는 프로그램을 작성하시오.

입력
첫째 줄에 수의 개수 N(1 ≤ N ≤ 10,000,000)이 주어진다. 둘째 줄부터 N개의 줄에는 숫자가 주어진다. 이 수는 10,000보다 작거나 같은 자연수이다.

출력
첫째 줄부터 N개의 줄에 오름차순으로 정렬한 결과를 한 줄에 하나씩 출력한다.
~~~
* 접근 방법 1: 문제에서 카운팅 정렬을 사용하라는 힌트를 주어서 구글링을 통해 카운팅 정렬의 개념을 보고 구현에 성공 했다. 근데 메모리 초과 오류가 났다. 이 문제에서 메모리가 8MB로 제한되어 있기 때문에 배열을 3개까지 사용해야하는 카운팅 정렬은 불가능 했다. 

* 접근 방법 2: 자연수가 10000까지 들어오므로 배열을 하나만 써서 해결해야한다. 카운팅 정렬의 컨셉만 그대로 사용해서 입력을 받을 때마다 입력을 따로 저장하지 않고 몇번 나왔는지 출현 횟수만 저장하는 카운팅 배열 하나만 사용한다. 그리고 입력이 모두 끝난 이후에는 배열의 처음부터 끝까지 순회하면서 숫자 N을 출현했던 횟수 coutn[N] 만큼 출력해준다. 이렇게 하면 배열을 하나만 쓰고 해결 할 수 있다.

#### [2108번: 통계학](https://www.acmicpc.net/problem/2108)
~~~
문제
수를 처리하는 것은 통계학에서 상당히 중요한 일이다. 통계학에서 N개의 수를 대표하는 기본 통계값에는 다음과 같은 것들이 있다. 단, N은 홀수라고 가정하자.

산술평균 : N개의 수들의 합을 N으로 나눈 값
중앙값 : N개의 수들을 증가하는 순서로 나열했을 경우 그 중앙에 위치하는 값
최빈값 : N개의 수들 중 가장 많이 나타나는 값
범위 : N개의 수들 중 최댓값과 최솟값의 차이
N개의 수가 주어졌을 때, 네 가지 기본 통계값을 구하는 프로그램을 작성하시오.

입력
첫째 줄에 수의 개수 N(1 ≤ N ≤ 500,000)이 주어진다. 그 다음 N개의 줄에는 정수들이 주어진다. 입력되는 정수의 절댓값은 4,000을 넘지 않는다.

출력
첫째 줄에는 산술평균을 출력한다. 소수점 이하 첫째 자리에서 반올림한 값을 출력한다.

둘째 줄에는 중앙값을 출력한다.

셋째 줄에는 최빈값을 출력한다. 여러 개 있을 때에는 최빈값 중 두 번째로 작은 값을 출력한다.

넷째 줄에는 범위를 출력한다.
~~~
* 접근 방법: 
  + 산술평균: numeric 라이브러리에 들어있는 accumulate 함수를 통해서 입력받은 값들이 들어있는 벡터 요소들의 총합을 구하고 N으로 나눈다. cmath 의 round를 이용해서 반올림을 구현한다.
  + 중앙값: 입력이 언제나 홀수개로 들어오기 때문에 그냥 벡터의 사이즈/2 를 해주면 중앙값의 인덱스를 구할 수 있다. 중앙 값을 구하기 전에 벡터가 sort 함수를 통해 정렬되어 있어야 한다.
  + 최빈값: 그냥 최빈값을 찾는건 쉬운데 최빈값이 여러개 있을 때를 처리하기 위해서 일단 최빈값을 찾는다. 이를 이해서 길이 8001개 짜리 벡터 하나를 만들어서 입력을 받을 때마다 해당 값의 인덱스 값을 1씩 올려준다. 최빈값을 찾은 후에 카운팅 벡터를 돌면서 최빈값에 해당하는 수를 모두 별도의 벡터에 넣고 이 벡터의 사이즈가 1 이상이되면 sort 후에 1번째 인덱스에 있는 값을 출력한다.
  + 범위 : 범위는 최댓값 - 최솟값 이므로 정렬된 벡터의 가장 마지막 값과 제일 첫번째 값의 차를 구해서 출력한다.

#### [1427번: 소트인사이드](https://www.acmicpc.net/problem/1427)
~~~
문제
배열을 정렬하는 것은 쉽다. 수가 주어지면, 그 수의 각 자리수를 내림차순으로 정렬해보자.

입력
첫째 줄에 정렬하고자하는 수 N이 주어진다. N은 1,000,000,000보다 작거나 같은 자연수이다.

출력
첫째 줄에 자리수를 내림차순으로 정렬한 수를 출력한다.
~~~
* 접근 방법: 사실 C로 풀었으면 좀 헤맸을 것 같은데 CPP로 풀어서 쉽게 풀 수 있었다. 내림차순 정렬을 위해서 sort함수의 마지막 인자로 넣어줄 functional 라이브러리의 greater<type>()을 가져오고 입력으로 받은 string을 정렬해주기만 하면 끝이다.

### 2020.01.04 토요일
#### [11650번: 좌표 정렬하기](https://www.acmicpc.net/problem/11650)
~~~
문제
2차원 평면 위의 점 N개가 주어진다. 좌표를 x좌표가 증가하는 순으로, x좌표가 같으면 y좌표가 증가하는 순서로 정렬한 다음 출력하는 프로그램을 작성하시오.

입력
첫째 줄에 점의 개수 N (1 ≤ N ≤ 100,000)이 주어진다. 둘째 줄부터 N개의 줄에는 i번점의 위치 xi와 yi가 주어진다. (-100,000 ≤ xi, yi ≤ 100,000) 좌표는 항상 정수이고, 위치가 같은 두 점은 없다.

출력
첫째 줄부터 N개의 줄에 점을 정렬한 결과를 출력한다.
~~~
* 접근 방법: 벡터를 두개 써보기도 하고 map을 써보기도 하고 엄청 헤맸다..그러다가 pair 를 벡터의 아이템으로 넣을 수 있다는 것을 알게되어 이 방법으로 시도해 보았다. pair를 벡터 안에 입력 받을 때마다 넣고 sort함수를 통해 벡터를 정렬하면 first 기준으로 오름차순 정렬되고 first끼리 같다면 second 끼리 비교하여 오름차순으로 정렬된다.

#### [10814번: 나이순 정렬](https://www.acmicpc.net/problem/10814)
~~~
문제
온라인 저지에 가입한 사람들의 나이와 이름이 가입한 순서대로 주어진다. 이때, 회원들을 나이가 증가하는 순으로, 나이가 같으면 먼저 가입한 사람이 앞에 오는 순서로 정렬하는 프로그램을 작성하시오.

입력
첫째 줄에 온라인 저지 회원의 수 N이 주어진다. (1 ≤ N ≤ 100,000)

둘째 줄부터 N개의 줄에는 각 회원의 나이와 이름이 공백으로 구분되어 주어진다. 나이는 1보다 크거나 같으며, 200보다 작거나 같은 정수이고, 이름은 알파벳 대소문자로 이루어져 있고, 길이가 100보다 작거나 같은 문자열이다. 입력은 가입한 순서로 주어진다.

출력
첫째 줄부터 총 N개의 줄에 걸쳐 온라인 저지 회원을 나이 순, 나이가 같으면 가입한 순으로 한 줄에 한 명씩 나이와 이름을 공백으로 구분해 출력한다.
~~~
* 접근 방법: map 자료구조를 사용하면 쉽게 해결할 수 있다. map 은 pair를 insert 하면 바로 first를 기준으로 정렬한다. 그리고 first가 같은 같은 pair는 원래 허용이 안되지만 multimap이라는 특수한 자료구조를 사용하면 여러개의 first 값을 유지하면서 first가 같은 값은 나중에 들어온 순서대로 정렬된다. 따라서 이 문제에서 원하는 바를 정확하게 수행할 수 있다.

### 2020.01.05 일요일
#### [11651번: 좌표 정렬하기 2](https://www.acmicpc.net/problem/11651)
~~~
문제
2차원 평면 위의 점 N개가 주어진다. 좌표를 y좌표가 증가하는 순으로, y좌표가 같으면 x좌표가 증가하는 순서로 정렬한 다음 출력하는 프로그램을 작성하시오.

입력
첫째 줄에 점의 개수 N (1 ≤ N ≤ 100,000)이 주어진다. 둘째 줄부터 N개의 줄에는 i번점의 위치 xi와 yi가 주어진다. (-100,000 ≤ xi, yi ≤ 100,000) 좌표는 항상 정수이고, 위치가 같은 두 점은 없다.

출력
첫째 줄부터 N개의 줄에 점을 정렬한 결과를 출력한다.
~~~

* 접근 방법: 기존 정렬하기 코드에서 sort 함수의 인자로 새로 정의한 비교함수를 넣어주었다. 이 함수에서는 pair 의 second 끼리 비교하고 second가 서로 같으면 first끼리 다시 비교해서 first가 더 작은 수를 앞으로 정렬시키도록 구성했다.

#### [15649번: N과 M (1)](https://www.acmicpc.net/problem/15649)
~~~
문제
자연수 N과 M이 주어졌을 때, 아래 조건을 만족하는 길이가 M인 수열을 모두 구하는 프로그램을 작성하시오.

1부터 N까지 자연수 중에서 중복 없이 M개를 고른 수열
입력
첫째 줄에 자연수 N과 M이 주어진다. (1 ≤ M ≤ N ≤ 8)

출력
한 줄에 하나씩 문제의 조건을 만족하는 수열을 출력한다. 중복되는 수열을 여러 번 출력하면 안되며, 각 수열은 공백으로 구분해서 출력해야 한다.

수열은 사전 순으로 증가하는 순서로 출력해야 한다.
~~~
* 접근 방법: DFS를 통해 해결하는 문제. 백트래킹을 연습하는 단계에 들어왔는데 자료구조때 배웠던 DFS를 다 까먹어서 구글링하면서 다시 공부했다. 전체적인 알고리즘은 깊이를 계속 내려가면서 방문했던 노드를 마킹하고 깊이가 내려갈 때마다 아이템을 넣을 배열 위치를 하나씩 늘려간다. 그리고 배열이 M 길이만큼 채워지면 채워진 값들을 모두 출력하고 리턴한다. 리턴된 이후에는 다시 모든 마킹을 false로 처리해주어야 다음번 경우의 수에서 값들을 정상적으로 체크할 수 있다.

#### [15650번: N과 M (2)](https://www.acmicpc.net/problem/15650)
~~~
문제
자연수 N과 M이 주어졌을 때, 아래 조건을 만족하는 길이가 M인 수열을 모두 구하는 프로그램을 작성하시오.

1부터 N까지 자연수 중에서 중복 없이 M개를 고른 수열
고른 수열은 오름차순이어야 한다.
입력
첫째 줄에 자연수 N과 M이 주어진다. (1 ≤ M ≤ N ≤ 8)

출력
한 줄에 하나씩 문제의 조건을 만족하는 수열을 출력한다. 중복되는 수열을 여러 번 출력하면 안되며, 각 수열은 공백으로 구분해서 출력해야 한다.

수열은 사전 순으로 증가하는 순서로 출력해야 한다.
~~~
* 접근 방법: N과 M(1)과 마찬가지로 진행하면서 오름차순인 수열들만 결과 벡터에 넣어두고 맨 마지막의 결과 벡터에 들어있는 값들을 출력해주었다.

#### [15651번: N과 M (3)](https://www.acmicpc.net/problem/15651)
~~~
문제
자연수 N과 M이 주어졌을 때, 아래 조건을 만족하는 길이가 M인 수열을 모두 구하는 프로그램을 작성하시오.
 - 1부터 N까지 자연수 중에서 M개를 고른 수열
 - 같은 수를 여러 번 골라도 된다.

입력
첫째 줄에 자연수 N과 M이 주어진다. (1 ≤ M ≤ N ≤ 7)

출력
한 줄에 하나씩 문제의 조건을 만족하는 수열을 출력한다. 중복되는 수열을 여러 번 출력하면 안되며, 각 수열은 공백으로 구분해서 출력해야 한다.

수열은 사전 순으로 증가하는 순서로 출력해야 한다.
~~~
* 접근 방법: 기존 N과 M을 구현할 때는 bool형 visited 벡터를 두어서 이미 들렀던 노드의 여부를 체크해줘서 first와 second가 같은 값을 가지지 않도록 했었는데, 이번 문제는 중복을 허용하기 때문에 visited 벡터를 없애고 모든 노드를 매번 순회하면 된다.

