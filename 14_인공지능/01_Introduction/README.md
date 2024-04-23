인공지능은 처음에 인간처럼 행동할 수 있는 에이전트를 만드려고 도전했다가 여러 실패를 겪은 것 같다. 인간처럼 행동할 수 있는 기계를 만들고자 한 것부터 시작해서 여러 제약이 있는 환경(problem solving agent, search algorithms, ...)에서 최적의 문제를 풀 수 있는 다양한 알고리즘이 개발되고, 또 다시 인간처럼 행동할 수 있는 기계를 만들고자 고민하고 있는 느낌이다. 인간을 함수화(?)하여 sensor를 통하여 현상을 perceive하고 actuator를 통해서 act하는 주체라는 지능적 에이전트라는 개념을 소개한다. 사실 환경에서 주어지는 입력에 대한 반응 쌍을 1:1 로 모두 연결시켜 알려주면 좋겠지만 그러기에는 너무 복잡하다. 그래서 ‘근사’ 를 하게 되며 좋은 근사를 하기 위한 여러 agent에 대한 개념들을 소개한다. ([참고](https://cs-ssupport.tistory.com/396#2)_High_Level))

# 목차
1. What is AI
2. A brief history
3. The state of the art

# What is AI (인공지능이란 무엇인가)
- human vs rational
- thought vs behavior

| |Human|Rational|
|---|---|---|
|**Thought**|Systems that think like humans|Systems that think rationally|
|**Act**|Systems that act like humans|Systems that act rationally|


## (Like) Human
<u>**인간처럼 “행동” 할 수 있다 (Acting humanly)</u>**
- Turing Test
    - 거의 인간과 동일한 지능적 행동을 보여주는 기계의 능력에 대한 테스트
    - Thinking humanly가 아닌 Acting Humanly 관점에서 정의가 되었다. 물론 Acting Rationally는 아니다.
- The Chinese room ([아래 글 출처](https://namu.wiki/w/%EC%A4%91%EA%B5%AD%EC%96%B4%20%EB%B0%A9))
   - "기계의 인공지능 여부를 판별한다는 튜링 테스트의 결과는 실제로 어떤 기계가 지능을 갖고 있음을 증명할 수 없다"는 문제점을 지적하기 위해서 이러한 실험을 고안하였다.
   - 어느 방 안에 중국어를 모르는 사람(이하 참가자)이 들어간다. 이후 참가자는 중국어로 된 질문과 이에 대응하는 적절한 중국어 응답이 적힌 지시사항의 목록, 그리고 다른 사람과 소통하기 위한 필기도구를 제공받는다. 이 상태에서 중국인 심사관이 중국어로 질문을 써서 방 안으로 집어넣는다면, 참가자는 중국어를 전혀 모르더라도 목록을 토대로 알맞은 대답을 중국어로 써서 심사관에게 건넨다.

<u>**인간처럼 “생각” 할 수 있다 (Thinking humanly)</u>**
- human thought를 배우기 위해서는 introspect, brain imaging, psychological experiment 등이 있다.
- Neuroscience
- Theory of mind(마음 이론)
  - 심리학에서 마음 이론은 다른 사람의 마음(정신) 속에서 일어나는 일을 추측함으로써 다른 사람을 이해하는 이론을 말함
- Cognitive science
- Cognitive modeling approach

여기서 생각은 구체적인 추론을 할 수 있는 것이고 행동은 인간의 행동을 잘 모방하는 것인데, 현재 대부분의 인공지능은 입력과 출력 데이터로 인간처럼 ‘행동’하게 모델을 학습시키는 것이다. 인간처럼 생각하는 모델을 구현하는건 굉장히 어려운 작업이다.

## Rationality
<u>**합리적으로 "생각"할 수 있다(Thinking rationally): Laws of Thought approach**</u>
- Laws of Thought(ex. Syllogisms (삼단논법))

<u>**합리적으로 "행동"할 수 있다(Acting rationally): Rational agent approach**</u>
- Agent: perceive와 act를 하는 entity이다.
- <u>**Rational Agent**</u>: best outcome을 위해 act하는 agent(최선의 결과를 얻도록 행동)
  - rational behavior: 주어진 정보에 따라 목표 달성을 극대화할 수 있는 올바른 행동을 하는 것
  - 초기 수십 년 동안 rational agent는 논리적 토대 위에 구축되어 특정 목표를 달성하기 위해 계획을 만들었고 이후에는 확률과 머신러닝이 등장했다. AI는 right thing을 하는 에이전트를 연구해왔다.
  - computational limitation의 한계로 perfect rationality는 만들 수 없고 주어진 machine resource에서 best program을 디자인한다.
  - 이 강의는 rational agents를 디자인하는 것에 대해 다룬다.

## Main Topics of AI
Sencing
- 감각을 통해 인식한 정보를 개념적 표현으로 변환
- ex. 컴퓨터 비전, 음성인식, 자연어처리

Thinking
- Sensing을 통해 인식한 정보를 개념적 표현으로 조작
- ex. 지식 표현, 문제 해결 / 계획, 학습

Acting
- sencing / thinking 을 통해서 어떠한 과정들을 물리적 행동으로 수행
- ex. 로보틱스

Foundations of AI (인공지능의 기반 학문)으로 철학, 수학, 심리학, 경제학, 언어학, 신경과학 등 존재.

# AI History
1. IBM(1911): IBM이 처음에는 pos기로 시작해 후에 메인프레임을 주 제품으로 만듦(IBM은 나중에 DRAM 최초 개발(1966), 바코드 개발(1974), RISC 아키텍처 발표(1980))
2. 튜링 머신 제안(1936): 계산하는 기계를 설명하기 위해 논리적으로 구현된 장치. 오토마타의 일종이다.
3. 최초의 인공 신경망 모델 제안(1943): 최초로 신경세포(뉴런)를 수학적으로 모델링. by 메컬록, 피츠
4. 폰 노이만 구조 발표(1945): 폰 노이만이 중앙처리장치(CPU), 메모리, 프로그램의 구조를 갖는 컴퓨터 아키텍처 제안
5. 에니악(1946): 대포의 탄도 계산을 목적으로 세계 최초의 컴퓨터 제작. 폰 노이만이 제작에 참여하였으며 폰 노이만 구조가 적용됨
6. 두 신경세포간의 가중치 변화 규칙 제안(1949) : 인접한 두 뉴런이 지속적으로 활성화된다면 뉴런 사이의 connection 강도가 더 강해진다 by Hebb (참고로 헵은 신경 심리학자이다)
7. 최초의 인공 신경망 컴퓨터 SNARC(Stochastic Neural Analog Reinforcement Calculator) 제작 (1950) : by Marvin Minsky and Dean Edmonds
8. 튜링 테스트 제시 (1950)
9. 다트머스회의(Dartmouth conference, 1956): 존 매카시가 개최. 이 때 AI 라는 단어가 처음 사용. 매카시, 민스키, 섀넌, 로체스터 등의 학자와 IBM 엔지니어들이 모여 인공지능 연구 시작.
10. General problem solver(GPS) 프로젝트 (1957): 인간의 논리 구조로 일반적인 문제를 풀고자 했음
11. Lisp(1958):  컴퓨터 프로그래밍 언어 개발 by 존 매카시
12. <u>**인공지능 첫번째 봄 시작 (1960년대 초반 ~ ) : 뭔가 말만 번지르르하게 한 시대. 실제로 보여준건 딱히 없음**</u>
13. 퍼셉트론 이론 (1962): by: 프랭크 로젠블랫
14. 퍼지 이론(1965): 모호성을 다루는 논리가 퍼지 논리이고 이후 전문가 시스템을 개발하기 위한 이론적 토대가 됨.
15. 마빈 민스키가 퍼셉트론으로 XOR 문제를 풀 수 없다는 것을 증명(1969)
16. <u>**인공지능 첫번째 겨울 시작(1960년대 후반 ~ 70년대 초반(전문가 시스템 전까지))**</u>
    - **어떤 특정 영역의 문제를 풀기보다 광범위한 문제를 일반적인 방법으로 풀고자 했음**
    - **사람이 풀 수 있는 문제를 풀고 스스로 향상 시키는 기계를 만들고자 했는데 사실 지금도 잘 안되는 것들이다. 이런 것들을 풀려고 했으니 잘 안될 수 밖에 없다**
    - **인공지능 투자가 거의 대부분 끊김.**
    - **퍼셉트론으로 XOR 문제 해결 못함.**
17. <u>**인공지능 두번째 봄 시작 (1970년대 후반 ~ 1990년대 초반)**</u>
    - **인간처럼 생각하고 행동하지는 않더라도 특정 문제를 잘 풀 수 있는 인공지능을 만들어보기로 함. 예를 들어 어려운 문제를 풀려면 이미 답을 알고 있어야하고, 그러면 전문가로부터 예상 답변들을 받은 후 정답을 잘 ‘찾게’끔 문제 방향을 변경했다. 결국 산업적으로도 좋은 성과를 거둠.**
    - **전문가 시스템**의 등장
    - **MLP로 XOR 문제 해결**
18. DENTRAL(1969): 최초로 인간 전문가의 지식을 프로그램으로 만듦. 화학 분자 구조를 유추하는 프로그램(인공지능) 제작.
19. Expert system(1970) : Alternative to weak methods is to use more powerful, domain-specific knowledge. 1970년대에 지능형 기계의 문제영역을 제한해야한다는 것을 깨달음. 이전 연구의 핵심은 기초적인 추론 단계들을 연결해서 완전한 해를 찾아내야하는 범용 메커니즘 이었다면 (이를 weak method 라고 부른다) 이제는 문제영역을 제한해야한다는 것을 깨달음. 현실은 if-else를 여러번 적은 프로그램에 불과했음.
20. Back propagation 알고리즘 제안 (1970): by S. Linnainmaa
21. PROLOG(1972): 프로그래밍 언어 개발, 인공지능이나 계산 언어학 분야, 특히 프롤로그가 만들어진 목적이었던 자연언어 처리 분야에서 많이 사용됨.
22. Apple(1976~ )
23. Apple 2(1977) : 애플에서 만든 최초의 개인용 컴퓨터 (실제 최초의 개인용 컴퓨터는 1974년 출시된 '알테어(Altair) 8800))
24. Multilayer Perceptron을 Back Propagation으로 계산하는 방법을 발표 (1981) : by P. J. Werbos
25. IBM PC (1981): IBM에서 제작한 최초의 개인용 컴퓨터
26. R1(1982) : 최초의 상용적인 전문가 시스템 at Digital Equipment Corporation. 이를 시작으로 80년대에는 이를 각 기업에서 필요한 곳에 응용하기 시작함.
27. Apple Macintoch(1984): Apple에서 만든 개인용 컴퓨터. 애플에서 출시한 Mac 시리즈의 첫번째 모델. GUI를 도입한 운영체제의 보급에 큰 공헌을 함.
28. Decision Tree 제안 (1986)
29. MLP와 Back Propagation 알고리즘을 실험적으로 증명하여 XOR 문제 해결(1986) by 제프리 힌튼
30. MLP, Backpropagation을 convolution과 결합하여 MNIST 데이터 셋에 적용(1989) by Yann Lecun
31. <u>**인공지능 두번째 겨울 시작(1990년대 ~)**</u>
    - **Gradient vanishing problem**
    - **복잡한 연산 처리의 어려움**
    - **Curse of dimensionality**
    - **Overfitting**
    - **1990년대 후반 ~ 2000년대까지 신경망에 대한 연구가 잠시 줄어들고 다양한 머신러닝 알고리즘들이 제안됨.**

32. Support Vector Machine 제안 (1995): 특히 SVM과 같은 새로운 접근 방법인 커널 방법이 인기를 얻으면서 신경망은 빠르게 잊혀져감.
33. AdaBoost 알고리즘 제안 (1997)
34. IBM의 딥블루가 인간 체스 챔피언을 이김 (1997)
35. LeNet-5(1998): cnn 모델의 조상격인 모델 발표, by Yann Lecun
36. Random Forest 제안 (2001)
37. <u>**인공지능 세번째 봄 시작 (2010년대 초반 ~)**</u>
    - **2010년대 초부터 여러 딥러닝 알고리즘들이 제안됨**
38. 구글 speech to search 개발 (2008)
39. Fei-Fei Li가 대규모 이미지 넷 데이터 셋을 공개(2009)
40. IBM 왓슨, 인기 퀴즈쇼 ‘제퍼디’에서 1등 (2011)
41. Judea Pearl(확률적 접근 방식으로 유명하며 베이지안 네트워크 개발에 공헌) 튜링상(development of a calculus for probabilistic and causal reasoning) 수상 (2011)
42. 제프리 힌튼 연구팀이 이미지넷 분류 대회에서 수상. cnn 기반의 alexnet 제안 (2012)
43. Apple siri 발표(2012)
44. 구글 tensorflow 오픈소스 발표(2015)
45. 딥마인드 알파고 (2016)
46. Transformer (Attention is all you need) (2017)
47. GPT(Improving language understanding by generative pre-training) (2018.06)
48. Bert (2018.10)
49. Stable diffusion (2022)
50. CHATGPT (2022)
