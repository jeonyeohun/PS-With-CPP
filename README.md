# Maeil Maeil Coding!
### Daily Problem Solving in C++

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
[2775번: 부녀회장이 될테야](https://www.acmicpc.net/problem/2775)
> 평소 반상회에 참석하는 것을 좋아하는 주희는 이번 기회에 부녀회장이 되고 싶어 각 층의 사람들을 불러 모아 반상회를 주최하려고 한다. 이 아파트에 거주를 하려면 조건이 있는데, “a층의 b호에 살려면 자신의 아래(a-1)층의 1호부터 b호까지 사람들의 수의 합만큼 사람들을 데려와 살아야 한다” 는 계약 조항을 꼭 지키고 들어와야 한다. 아파트에 비어있는 집은 없고 모든 거주민들이 이 계약 조건을 지키고 왔다고 가정했을 때, 주어지는 양의 정수 k와 n에 대해 k층에 n호에는 몇 명이 살고 있는지 출력하라. 단, 아파트에는 0층부터 있고 각층에는 1호부터 있으며, 0층의 i호에는 i명이 산다. 첫 번째 줄에 Test case의 수 T가 주어진다. 그리고 각각의 케이스마다 입력으로 첫 번째 줄에 정수 k, 두 번째 줄에 정수 n이 주어진다. (1 <= k <= 14, 1 <= n <= 14) 각각의 Test case에 대해서 해당 집에 거주민 수를 출력하라.

* 접근 방법 1: 규칙을 보아하니 팩토리얼로 푸는 것 같아서 각 층을 팩토리얼로 매핑을 해두고 나중에 다 더하려고 했는데 문제를 완전 잘못 이해하고 있었다.. 나는 B호의 이전까지의 모든 거주민의 합을 구하는 것인줄 알았는데, A-1층에서 B번째 방까지 있는 사람의 수를 합치는 것이었다..팩토리얼로 어떻게 해보려다가 시간만 많이 낭비했다.

* 접근 방법 2: 새로 생각한 방법은 전체 14X14 배열에 거주민을 미리 맵핑해두고 어떤 n과 k가 들어오든 바로바로 값을 알려주면 되는 방법이었다. 일단 0층은 i와 같은 사람의 수가 있으니까 0층은 i대로 맵핑하고 다른 층은 k-1층에 있는 값들을 n열까지 더해서 넣어주었다.

* 두번째 방법으로 푸니까 잘 풀렸다. 그런데 제출할때 계속 틀렸다고 나와서 찾아보니 배열크기를 14X14가 아니라 15X14로 해야된다고 한다. 이걸 쓰면서 이유를 알았는데 층수는 0층부터 시작하고 호수는 1호 부터 시작하니까..!

[10250번: ACM 호텔](https://www.acmicpc.net/problem/10250)
> ACM 호텔 매니저 지우는 손님이 도착하는 대로 빈 방을 배정하고 있다. 고객 설문조사에 따르면 손님들은 호텔 정문으로부터 걸어서 가장 짧은 거리에 있는 방을 선호한다고 한다. 여러분은 지우를 도와 줄 프로그램을 작성하고자 한다. 즉 설문조사 결과 대로 호텔 정문으로부터 걷는 거리가 가장 짧도록 방을 배정하는 프로그램을 작성하고자 한다. 문제를 단순화하기 위해서 호텔은 직사각형 모양이라고 가정하자. 각 층에 W 개의 방이 있는 H 층 건물이라고 가정하자 (1 ≤ H, W ≤ 99). 그리고 엘리베이터는 가장 왼쪽에 있다고 가정하자(그림 1 참고). 이런 형태의 호텔을 H × W 형태 호텔이라고 부른다. 호텔 정문은 일층 엘리베이터 바로 앞에 있는데, 정문에서 엘리베이터까지의 거리는 무시한다. 또 모든 인접한 두 방 사이의 거리는 같은 거리(거리 1)라고 가정하고 호텔의 정면 쪽에만 방이 있다고 가정한다. 방 번호는 YXX 나 YYXX 형태인데 여기서 Y 나 YY 는 층 수를 나타내고 XX 는 엘리베이터에서부터 세었을 때의 번호를 나타낸다. 즉, 그림 1 에서 빗금으로 표시한 방은 305 호가 된다. 손님은 엘리베이터를 타고 이동하는 거리는 신경 쓰지 않는다. 다만 걷는 거리가 같을 때에는 아래층의 방을 더 선호한다. 예를 들면 102 호 방보다는 301 호 방을 더 선호하는데, 102 호는 거리 2 만큼 걸어야 하지만 301 호는 거리 1 만큼만 걸으면 되기 때문이다. 같은 이유로 102 호보다 2101 호를 더 선호한다. 여러분이 작성할 프로그램은 초기에 모든 방이 비어있다고 가정하에 이 정책에 따라 N 번째로 도착한 손님에게 배정될 방 번호를 계산하는 프로그램이다. 첫 번째 손님은 101 호, 두 번째 손님은 201 호 등과 같이 배정한다. 그림 1 의 경우를 예로 들면, H = 6이므로 10 번째 손님은 402 호에 배정해야 한다.

* 접근 방법 : 일단 호텔 특성 상 아무리 층수가 높아져도 낮은 숫자의 호수가 먼저 채워진다. 그래서 일단 전체 방문객 수를 층수에서 나눠서 나온 몫을 호수로 하면 될 것 같다는 생각이 든다. 근데 이건 딱 나누어 떨어질 때 이야기고, 딱 안나누어 떨어지면서 층수보다 큰 숫자이면 몫+1을 해주어야지 제대로 된 호수가 나올 것이다. 그리고 전체 방문객수를 층수에서 나눈 나머지를 층수로 정하면 될 것 같다. 

* 예를 들어 이 호텔의 층수가 7이고 10번째 방문객의 방을 찾는다면 10/7 의 몫인 1에 방문객이 층수보다 크니까 1을 더해서 2호, 그리고 층수는 10%7인 3층으로 해서 결과가 302호가 나오게 된다.
* 반례를 생각해보자. 만약 방문객수가 층수로 딱 떨어진다면? 만약 7층짜리 호텔에 방문객이 14명이라고 치면 2로 나누어 떨어지는데 이때는 1을 더하지 않고 2로 호수를 정하고, 층수는 나머지가 0이 나올 때, 전체 층수로 바꿔주면 될 것 같은데..? 일단 코드 짜보고 반례나오면 더 생각해보자.

### 2019.12.19 목요일
[1993번: 분수찾기](https://www.acmicpc.net/problem/1193)
> 나열된 분수들을 1/1 -> 1/2 -> 2/1 -> 3/1 -> 2/2 -> … 과 같은 지그재그 순서로 차례대로 1번, 2번, 3번, 4번, 5번, … 분수라고 하자. X가 주어졌을 때, X번째 분수를 구하는 프로그램을 작성하시오.

* 접근 방법: 규칙을 찾아보려고 했는데 보니까 지그재그니까 홀수 행에서는 위로, 짝수행에서는 아래로 이동한다. 그리고 홀수 행에서는 분모가 1씩 늘어나고 분자가 1씩 줄어든다. 짝수 행에서는 분모가 1씩 줄어들고 분자가 1씩 늘어난다. 이 규칙을 수식화 하면 풀 수 있을 것 같다. 그리고 한번 이동할 때마다 열만큼 이동하면 된다. 주어진 숫자에 다다를때까지 이 규칙대로 계속 진행하면 결과를 바로 알 수 있을 것 같다. 

* 해결 후 : 해결하고 다른 사람이 짠 숏코딩을 봤는데 진짜 대단하다.. 접근 방법이 비슷해도 그걸 구현해내는 능력이 참 다른 것 같다. 15줄만에 끝내는 어떤 코드를 보면서 존경스러운 생각이 들었다..

### 2019.12.20 금요일
[4153번: 직각삼각형](https://www.acmicpc.net/problem/4153)
> 과거 이집트인들은 각 변들의 길이가 3, 4, 5인 삼각형이 직각 삼각형인것을 알아냈다. 주어진 세변의 길이로 삼각형이 직각인지 아닌지 구분하시오. 입력은 여러개의 테스트케이스로 주어지며 마지막줄에는 0 0 0이 입력된다. 각 테스트케이스는 모두 30,000보다 작은 양의 정수로 주어지며, 각 입력은 변의 길이를 의미한다. 각 입력에 대해 직각 삼각형이 맞다면 "right", 아니라면 "wrong"을 출력한다.

* 접근 방법: 직각삼각형은 a^2+b^2=c^2 의 식이 성립하는 삼각형이므로 입력 중 가장 긴 변을 c로 잡고 나머지 두 입력을 a와 b로 잡아 식에 대입해보고 직각삼각형 여부를 판별한다.

[3053번: 택시기하학](https://www.acmicpc.net/problem/3053)
> 19세기 독일 수학자 헤르만 민코프스키는 비유클리드 기하학 중 택시 기하학을 고안했다. 택시 기하학에서 두 점 T1(x1,y1), T2(x2,y2) 사이의 거리는 다음과 같이 구할 수 있다. D(T1,T2) = |x1-x2| + |y1-y2|, 두 점 사이의 거리를 제외한 나머지 정의는 유클리드 기하학에서의 정의와 같다. 따라서 택시 기하학에서 원의 정의는 유클리드 기하학에서 원의 정의와 같다. 원: 평면 상의 어떤 점에서 거리가 일정한 점들의 집합. 반지름 R이 주어졌을 때, 유클리드 기하학에서 원의 넓이와, 택시 기하학에서 원의 넓이를 구하는 프로그램을 작성하시오.

* 접근 방법: 이 문제는 기하학 자체가 나한테 생소해서 택시 기하학에 대한 자료를 찾아보고 해결했다.. 사실 찾아보니까 너무 생각을 안하고 찾아보기만 했다는 생각이 들긴 하다.. 일단 유클리드 기하학의 원의 형태가 택시 기하학에서는 정사각형이다. 결국 원의 지름이 정사각형의 대각선 길이와 같다. 정사각형의 대각선 공식은 (한변의 길이) X sqrt(2) 이기 때문에 입력으로 받은 반지름X2를 대각선 길이로 잡고 한변의 길이에 대한 식으로 전개하면 (한변의 길이)^2 = 2r^2 이 된다. 첫줄에는 원의 넓이인 PI X r^2 을, 두번쨰 줄에는 정사각형의 넓이인 2r^2을 출력한다.


### 2019.12.21 토요일
[1011번: Fly me to the Alpha Centauri](https://www.acmicpc.net/problem/1011)
> 우현이는 어린 시절, 지구 외의 다른 행성에서도 인류들이 살아갈 수 있는 미래가 오리라 믿었다. 그리고 그가 지구라는 세상에 발을 내려 놓은 지 23년이 지난 지금, 세계 최연소 ASNA 우주 비행사가 되어 새로운 세계에 발을 내려 놓는 영광의 순간을 기다리고 있다. 그가 탑승하게 될 우주선은 Alpha Centauri라는 새로운 인류의 보금자리를 개척하기 위한 대규모 생활 유지 시스템을 탑재하고 있기 때문에, 그 크기와 질량이 엄청난 이유로 최신기술력을 총 동원하여 개발한 공간이동 장치를 탑재하였다. 하지만 이 공간이동 장치는 이동 거리를 급격하게 늘릴 경우 기계에 심각한 결함이 발생하는 단점이 있어서, 이전 작동시기에 k광년을 이동하였을 때는 k-1 , k 혹은 k+1 광년만을 다시 이동할 수 있다. 예를 들어, 이 장치를 처음 작동시킬 경우 -1 , 0 , 1 광년을 이론상 이동할 수 있으나 사실상 음수 혹은 0 거리만큼의 이동은 의미가 없으므로 1 광년을 이동할 수 있으며, 그 다음에는 0 , 1 , 2 광년을 이동할 수 있는 것이다. ( 여기서 다시 2광년을 이동한다면 다음 시기엔 1, 2, 3 광년을 이동할 수 있다. ) 김우현은 공간이동 장치 작동시의 에너지 소모가 크다는 점을 잘 알고 있기 때문에 x지점에서 y지점을 향해 최소한의 작동 횟수로 이동하려 한다. 하지만 y지점에 도착해서도 공간 이동장치의 안전성을 위하여 y지점에 도착하기 바로 직전의 이동거리는 반드시 1광년으로 하려 한다. 김우현을 위해 x지점부터 정확히 y지점으로 이동하는데 필요한 공간 이동 장치 작동 횟수의 최솟값을 구하는 프로그램을 작성하라.

* 접근 방법: 아무리 생각해도 규칙이 찾아지지가 않아서 솔루션을 찾아봤다. 워프하는 거리로 봤을 때, 갈 수 있는 최대거리가 N^2만큼, 그리고 워프 횟수는 2XN-1 이 나온다. 따라서, y-x를 해서 얻은 거리를 최대 이동거리로 나누고 난 나머지가 추가로 가야하는 거리가 되는데, 이 거리는 남은 거리/워프횟수를 올림하면 구할 수 있다. 이 것을 일반화해서 풀면 쉽게 풀리는 문제였다.

* 해결 후: 솔루션을 보고 얻은 것은 for 반복문을 for(;;jum++) 로 쓰면서 while을 무한반복문으로 만들면서 i를 컨트롤해줘야하는 번거로움을 쉽게 해결한 부분이었다. 그리고 테스트 케이스도 번거롭게 for 반복문으로 돌리는게 아니라 while(t--)로 0이되면 바로 끝내는 방식으로 구성하니 훨씬 깔끔하게 코드를 만들 수 있었다. 규칙을 찾는 문제는 항상 어렵게 늦게지는데 소루션을 제시한 사람처럼 표를 만들어서 천천히 규칙을 찾아내는 방식이 좋은 것 같다.
 
 ### 2019.12.22 일요일
 [1002번: 터렛](https://www.acmicpc.net/problem/1002)
 > 조규현과 백승환은 터렛에 근무하는 직원이다. 하지만 워낙 존재감이 없어서 인구수는 차지하지 않는다. 다음은 조규현과 백승환의 사진이다. 이석원은 조규현과 백승환에게 상대편 마린(류재명)의 위치를 계산하라는 명령을 내렸다. 조규현과 백승환은 각각 자신의 터렛 위치에서 현재 적까지의 거리를 계산했다. 조규현의 좌표 (x1, y1)와 백승환의 좌표 (x2, y2)가 주어지고, 조규현이 계산한 류재명과의 거리 r1과 백승환이 계산한 류재명과의 거리 r2가 주어졌을 때, 류재명이 있을 수 있는 좌표의 수를 출력하는 프로그램을 작성하시오.
 
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
[2920번: 음계](https://www.acmicpc.net/problem/2920)
> 다장조는 c d e f g a b C, 총 8개 음으로 이루어져있다. 이 문제에서 8개 음은 다음과 같이 숫자로 바꾸어 표현한다. c는 1로, d는 2로, ..., C를 8로 바꾼다. 1부터 8까지 차례대로 연주한다면 ascending, 8부터 1까지 차례대로 연주한다면 descending, 둘 다 아니라면 mixed 이다. 연주한 순서가 주어졌을 때, 이것이 ascending인지, descending인지, 아니면 mixed인지 판별하는 프로그램을 작성하시오.

* 접근 방법: 단순한 문제였다. 그냥 소팅을 확인하면 되는 문제라 쉽게 해결했다. 배열의 요소들이 1씩 늘어나거나 1씩 줄어들 때마다 오름차순, 내림차순 카운트를 하나씩 올리고 최종적으로 7개가 되는 플래그를 정답으로 선택하면 된다. 

[2953번: 나는 요리사다](https://www.acmicpc.net/problem/2953)
> "나는 요리사다"는 다섯 참가자들이 서로의 요리 실력을 뽐내는 티비 프로이다. 각 참가자는 자신있는 음식을 하나씩 만들어오고, 서로 다른 사람의 음식을 점수로 평가해준다. 점수는 1점부터 5점까지 있다. 각 참가자가 얻은 점수는 다른 사람이 평가해 준 점수의 합이다. 이 쇼의 우승자는 가장 많은 점수를 얻은 사람이 된다. 각 참가자가 얻은 평가 점수가 주어졌을 때, 우승자와 그의 점수를 구하는 프로그램을 작성하시오.

*  접근 방법: 이것도 단순한 문제. 그냥 총점을 배열에 집어넣고 최댓값의 인덱스를 찾으면 된다. 

[1159번: 농구 경기](https://www.acmicpc.net/problem/1159)
> 상근이는 농구의 세계에서 점차 영향력을 넓혀가고 있다. 처음에 그는 농구 경기를 좋아하는 사람이었다. 농구에 대한 열정은 그를 막을 수 없었고, 결국 상근이는 농구장을 청소하는 일을 시작했다. 상근이도 농구장을 청소하면서 감독이 되기 위해 가져야할 능력을 공부해나갔다. 서당개 3년이면 풍월을 읊듯이 상근이는 점점 감독으로 한 걸음 다가가고 있었다. 어느 날 그에게 지방의 한 프로농구팀을 감독할 기회가 생기게 되었다. 그는 엄청난 지도력을 보여주며 프로 리그에서 우승을 했고, 이제 국가대표팀의 감독이 되었다. 내일은 일본과 국가대표 친선 경기가 있는 날이다. 상근이는 내일 경기에 나설 선발 명단을 작성해야 한다. 국가대표팀의 감독이 된 이후에 상근이는 매우 게을러졌다. 그는 선수의 이름을 기억하지 못하고, 각 선수의 능력도 알지 못한다. 따라서, 누가 선발인지 기억하기 쉽게 하기 위해 성의 첫 글자가 같은 선수 5명을 선발하려고 한다. 만약, 성의 첫 글자가 같은 선수가 5명보다 적다면, 상근이는 내일 있을 친선 경기를 기권하려고 한다. 상근이는 내일 경기를 위해 뽑을 수 있는 성의 첫 글자를 모두 구해보려고 한다.

* 접근 방법: 어차피 각 이름의 첫 글자만 필요하니까 벡터에 첫 글자를 넣고 중복되는 글자가 나올때마다 횟수 카운터만 올려준다. 최종적으로는 횟수가 5개 이상인 글자들만 출력한다.

[2799번: 블라인드](https://www.acmicpc.net/problem/2799)
> 봄이 오고 있다. 해는 높이 떠서 환하게 빛나고 있다. 사람들은 햇볕을 가리기 위해 블라인드를 내린다. 상근이는 이웃들이 무엇을 하는지를 염탐하고, 이것에 대해서 뒷담화를 하는 주부이다. 올해는 건너편 아파트에 사는 사람들이 블라인드를 얼마나 내리는지를 조사하려고 한다. 모든 창문은 4X4 그리드로 나타낼 수 있고, 별문자를 이용해서 블라인드를 나타낸다. 상근이가 볼 수 있는 창문은 다음 5가지 상태 중 하나이다. 건너편 아파트의 한 층에는 N개의 창문이 있고, 총 M층 건물이다. 현재 건너편 아파트의 창문 상태가 주어졌을 때, 위의 5가지 상태가 각각 몇 번 나오는지 구하는 프로그램을 작성하시오.

* 접근 방법: 배열에 문자를 쭉 넣어두고 별의 갯수를 세면서 어떤 타입인지 판정한다.

[5397번: 키로거](https://www.acmicpc.net/problem/5397)
> 창영이는 강산이의 비밀번호를 훔치기 위해서 강산이가 사용하는 컴퓨터에 키로거를 설치했다. 며칠을 기다린 끝에 창영이는 강산이가 비밀번호 창에 입력하는 글자를 얻어냈다. 키로거는 사용자가 키보드를 누른 명령을 모두 기록한다. 따라서, 강산이가 비밀번호를 입력할 때, 화살표나 백스페이스를 입력해도 정확한 비밀번호를 알아낼 수 있다. 강산이가 비밀번호 창에서 입력한 키가 주어졌을 때, 강산이의 비밀번호를 알아내는 프로그램을 작성하시오. 첫째 줄에 테스트 케이스의 개수가 주어진다. 각 테스트 케이스는 한줄로 이루어져 있고, 강산이가 입력한 순서대로 길이가 L인 문자열이 주어진다. (1 ≤ L의 길이 ≤ 1,000,000) 강산이가 백스페이스를 입력했다면, '-'가 주어진다. 이때 커서의 바로 앞에 글자가 존재한다면, 그 글자를 지운다. 화살표의 입력은 '<'와 '>'로 주어진다. 이때는 커서의 위치를 움직일 수 있다면, 왼쪽 또는 오른쪽으로 1만큼 움직인다. 나머지 문자는 비밀번호의 일부이다. 물론, 나중에 백스페이스를 통해서 지울 수는 있다. 만약 커서의 위치가 줄의 마지막이 아니라면, 그 문자를 입력하고, 커서는 오른쪽으로 한 칸 이동한다.

* 접근 방법: 링크드 리스트로 커서를 구현해서 주어진 조건에 따라 문자를 삽입한다. list 라이브러리를 사용해서 해결했는데, erase 할 때 커서 위치를 수정하는것, 그리고 '>' 기능과 '<', '-' 기능이 리스트의 양끝에서 적용되는 것에 대한 예외처리 때문에 조금 애를 먹긴했다.

[10870번: 피보나치 수 5](https://www.acmicpc.net/problem/10870)
* 재귀함수 연습문제이다. 너무 간단한 문제라서 풀었다는 기록만 남기고 생략한다.

### 2019.12.26 목요일
[11478번: 서로 다른 부분 문자열](https://www.acmicpc.net/problem/11478)
> 문자열 S가 주어졌을 때, S의 서로 다른 부분 문자열의 개수를 구하는 프로그램을 작성하시오. 부분 문자열은 S에서 연속된 일부분을 말하며, 길이가 1보다 크거나 같아야 한다. 예를 들어, ababc의 부분 문자열은 a, b, a, b, c, ab, ba, ab, bc, aba, bab, abc, abab, babc, ababc가 있고, 서로 다른것의 개수는 12개이다.

* 접근 방법: 일단 중복된 문자열을 허용하지 않기 때문에 set자료구조를 사용하기로 했다. 그리고 string 라이브러리에 포함된 substr을 사용하여 첫 글자부터 그 다음 글자들을 부분 문자열로 가져올 문자열 길이를 1씩 늘려가며 모두 가져와 set에 넣어주었다. 이렇게 하면 가능한 모든 부분 문자열이 중복없이 set에 들어가고 최종적으로는 set의 사이즈를 출력하면 될 것이다. 

[6321번: IBM 뺴기 1](https://www.acmicpc.net/problem/6321)
> '2001: 스페이스 오디세이'는 아서 C. 클라크의 소설이자 스탠리 큐브릭 감독의 영화이다. 이 작품에서 우주선은 토성으로 가고 있다. 긴 여행동안 선원들은 모두 정체 상태에 빠져있고, 두 선원은 깨어나 있다. 우주선은 인공지능 컴퓨터 HAL이 조정하고 있다. HAL은 점점 이상하게 행동하더니 선원들을 죽이기 시작했다. 자세한 이야기는 소설을 읽거나 영화를 보면 알 수 있다. 영화가 유명해지고 난 이후에 사람들은 '2001: 스페이스 오디세이'에 나오는 인공지능 컴퓨터인 HAL의 뜻에 관심을 가졌다. HAL은 휴리스틱 알고리즘 (Heuristic ALgorithm)의 약자이다. 하지만, HAL의 각 글자를 알파벳 다음 순서로 쓰면 IBM이 되기 때문에, IBM과 연관이 있다고 믿는 사람이 매우 많다. 컴퓨터의 이름이 주어졌을 때, 각 글자를 알파벳 다음 순서로 써서 출력하는 프로그램을 작성하시오.

* 접근 방법: 아스키 코드 연산으로 쉽게 해결할 수 있을 것 같다. 조건에 이름의 최대길이가 50이라고 주어져서 문자열 길이에 대해 신경쓸 필요도 없고 Z문자가 있으면 아스키코드 대문자 A의 바로 이전이 64로 문자를 바꿔주면 된다.

[4659번: 비밀번호 발음하기](https://www.acmicpc.net/problem/4659)
> 좋은 패스워드를 만드는것은 어려운 일이다. 대부분의 사용자들은 buddy처럼 발음하기 좋고 기억하기 쉬운 패스워드를 원하나, 이런 패스워드들은 보안의 문제가 발생한다. 어떤 사이트들은 xvtpzyo 같은 비밀번호를 무작위로 부여해 주기도 하지만, 사용자들은 이를 외우는데 어려움을 느끼고 심지어는 포스트잇에 적어 컴퓨터에 붙여놓는다. 가장 이상적인 해결법은 '발음이 가능한' 패스워드를 만드는 것으로 적당히 외우기 쉬우면서도 안전하게 계정을 지킬 수 있다. 회사 FnordCom은 그런 패스워드 생성기를 만들려고 계획중이다. 당신은 그 회사 품질 관리 부서의 직원으로 생성기를 테스트해보고 생성되는 패스워드의 품질을 평가하여야 한다. 높은 품질을 가진 비밀번호의 조건은 다음과 같다. 1. 모음(a,e,i,o,u) 하나를 반드시 포함하여야 한다. 2. 모음이 3개 혹은 자음이 3개 연속으로 오면 안 된다. 3. 같은 글자가 연속적으로 두번 오면 안되나, ee 와 oo는 허용한다. 이 규칙은 완벽하지 않다;우리에게 친숙하거나 발음이 쉬운 단어 중에서도 품질이 낮게 평가되는 경우가 많이 있다.

* 접근 방법: 문자열을 읽어와서 하나씩 문자형 변수로 읽으면서 조건을 모두 검사한다. 각 조건마다 플래그 변수를 두어서 최종적으로 플래그가 모두 통과조건에 해당할 경우에만 acceptable로 판정한다. 자음모음 여부는 해당 문자가 a, e, i, o, u 중 하나면 모음으로, 아니면 자음으로 판정하고 모음이 하나라도 나오면 1번 조건에 대한 플래그를 킨다. 그리고 자음모음이 연달아 나올때마다 그 갯수를 세서 3이 넘으면 2번 조건에 대한 플래그를 키고 두 글자가 연달아 나오면 e나 o인지 확인하고 아닐경우에 플래그를 키는 방식으로 순회를 진행한다. 
