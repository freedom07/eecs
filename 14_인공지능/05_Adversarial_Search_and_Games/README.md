이전의 여러가지 탐색(BFS, DFS, $A^*$, GBFS, Hill-Climbing, Local Beam, Simulated-Annealing)들은 전부 Single Agent 환경에서의 탐색 문제이다. 이 장에서는 다른 에이전트들이 우리의 에이전트를 방해하는 환경을 살펴본다. 즉 둘 이상의 Multi Agent 가 서로 상충하는 목표를 가지고 활동하는 경쟁적 환경(competitive environment)과 그런 환경에서 발생하는 대립 검색(adversarial search) 문제들을 살펴본다. 예를들어 바둑 또는 체스와 같은 게임환경이 그렇다. Multi Agent의 경우도 마찬가지로 현재 노드에서부터 Tree의 형태로 Expanding 되는 것은 동일하다고 볼 수 있다. Adversarial Search 에서는 Game Tree라고 부르기도한다.

적대적 탐색에서의 완전성/최적성 ([참고링크](https://cs-ssupport.tistory.com/432))
- 일반적인 Signle Agent 에서의 탐색의 completeness/optimality의 의미는 다음과같다.
  - completeness: 주어진 탐색에서 반드시 solution을 찾을 수 있는가?
  - optimality: 찾은 solution이 전체적으로 최적의 solution인가?
- 적대적 탐색에서의 completeness/optimality는 약간 다르다.
  - completeness: 여러 state 중 결정을 내릴 수 있는가?
  - optimality: 여러 state 중 내린 결정이 최적의 결정인가?

# Game (게임이론)
대립 에이전트들을 대립 게임 트리 검색(adversarial game-tree search) 기법들을 이용해서 명시적으로 모형화하는 것이다.
1. 한정된 범주의 게임들로 시작해서 최적의 수(move == 에어전트의 ‘동작’)를 정의하고, 그 수를 찾아내는 알고리즘인 최소최대 검색 알고리즘을 소개한다. 참고로 ‘국면’은 에이전트의 ‘상태’를 의미한다.
    - 최소 최대 검색 알고리즘
    - 가지치기(pruning)
    - 시간이 충분하지 않을 때 적당한 선에서 검색을 마치고 수를 선택하기
2. 검색을 마치고 누가 이겼는지 판정
    - 평가함수(evaluation function)
    - 그 상태에서 끝까지 게임을 여러번 빠르게 모의 실행한 결과들의 평균으로 승자를 판정

## Games vs search problems

## Types of games
||Determinisic|Change|
|--|--|--|
|Perfect information| chess, checkers, go, othello| backgammon monopoly|
|Imperfect information|battleships, blind tictactoe| bridge, poker, scrabble, nuclear war|

## Two-player zero-sum game(2인용 제로섬 게임)
체스나 바둑 등 인공지능 공동체에서 가장 자주 연구하는 게임들을 이론가들은 결정론적, 2인용, 교대식(turn-taking), 완전정보(perfect information, 완전 관측 가능과 같은 말), 제로섬(zero-sum, 한 플레이어에게 좋은 것이 다른 플레이어에게 나쁜 것, 윈-윈이 없다) 게임으로 분류한다.

## Game Tree(2-player, deterministic, turns)

# Optimal decisions in games (게임의 최적 결정)
최소최대 가치(minmax value): 한 상태의 최소최대 가치는 두 플레이어가 그 상태로부터 게임을 끝까지 최적으로 플레이한다고 가정하고 계산한, 그 상태에서의 효용 가치(MAX를 위한)이다. 종료 상태의 최소최대 가치는 그냥 그 종료 상태의 효용 가치임이 자명하다.

## Minimax algorithm(최소 최대 알고리즘)

## Optimal decisions in multiplayer games (다인용 게임의 최적 결정)

# $\alpha-\beta$ pruning(알파베타 가지치기)
(해당 알고리즘 매우 중요함)

([설명 참고](https://merry-nightmare.tistory.com/173))
최소최대 검색의 문제점은 조사해야할 게임 상태의 수가 게임 트리 깊이에 지수적이라는 점이다. 지수를 완전히 제거하는 알고리즘은 없지만, 지수를 실질적으로 반감하는 것은 가능하다.

최대최소검색이 깊이 우선 방식임을 기억하자. 따라서 주어진 한 시점에서 살펴봐야할 것은 트리의 경로 하나에 있는 노드뿐이다.

## Heuristic $\alpha - \beta$ search (발견적 알파 베타 트리 검색)
제한된 계산 시간을 최대한 활용하는 방법 하나는 검색을 일찍 중단(cut off)하고 발견적 평가 함수를 상태들에 적용하는 것이다. 이는 비말단 노드들을 마치 말단 노드들인 것처럼 취급하는 것에 해당한다. 알고리즘 구현의 관점에서는, 상태의 효용을 ‘계산’하는 utility 함수 대신 효용을 ‘추정’하는 eval 함수를 사용한다.

# Imperfect Real-Time Decision(불완전한 실시간의 결정)

## Evaluation function(평가 함수)

## Cutting off search(검색 중단)

## Forward pruning(순방향 가지치기)

## Monte Carlo Tree Search(몬테카를로 트리검색)
Monte Carlo Methods

# Stochastic Games(확률적 게임)
주사위를 굴리거나, 카드를 섞는 등 운(change)이 작용하는 게임들을 논의하고, 불완전 정보(imperfect information)가 포함된 게임(포커 또는 브리지 등)도 논의한다.

## Partially observable games(부분 관측 가능 게임)

## Kriegspiel(크리그슈필: 부분 관측 가능 체스)
