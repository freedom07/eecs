# 오토마타이론
강의교재: [An Introduction to Formal Languages and Automata](https://product.kyobobook.co.kr/detail/S000001732218)

## 목차
1. Introduction to automata, formal language, grammar, complexity
2. Basic for Automata, Finite Automata: DFA(Deterministic Finite Automata)
3. Finite Automata: DFA
4. Deterministic/Nondeterministic Finite Automata
5. NFA-to-DFA Transform (NFA: Non-deterministic Finite Automata)
6. Reduction of DFA and DFA States
7. Regular Expression
8. Regular Grammars, Regular Language Properties
9. Context-Free Grammars
10. Parsing Membership
11. Simplification of Context-Free Grammars
12. Memberships Algorithms for Context-Free Grammar 
13. Pushdown Automata and Context-Free Languages
14. Turing Mahcine

## 요약
오토마타는 input과 output이 있고 input에 따라 내부 state가 바뀌는 수학적인 모델을 의미한다. 쉽게 풀어서 스스로 움직이는 기계장치를 의미한다. 오토마타는 기본적으로 문자열로 주어진 입력을 읽고 유한한 내부상태를 가진다. push down automata 또는 turing machine처럼 특수한 경우에는 추가적으로 저장공간을 가질 수도 있다. 오토마타는 한번에 글자 하나를 읽으며 읽은 글자, 내부 상태, 추가 저장공간에 따라 내부 상태와 추가 저장공간을 업데이트하며 이를 멈출 때까지 반복한다.

오토마타 이론은 컴퓨터 과학의 근간이 되는 이론으로 인공지능, 컴퓨터 구조 설계, 컴파일러 설계 등에서 중요한 역할을 한다. 실제로 컴파일러를 만들기 위해 lexical analyzer를 만들 때나 syntax analyzer(parser)를 만들 때 오토마타 이론이 사용된다.

오토마타는 언어와 문법도 함께 다루게 되는데 우리가 사용하는 언어(ex. 한국어, 일본어 등) 그리고 각 언어와 관련된 문법(ex. 주어 + 서술어)들을 일반화한 개념이라고 생각하자. 프로그래밍 언어와 문법이라고 생각해도되고, 아예 새로운 언어와 문법을 생각해도된다.

처음에 촘스키가 형식언어를 4가지로 분류했다. 이 형식언어를 4가지로 분류했다는 뜻은 형식언어를 생성하기 위한 문법이 4가지가 있다는 것이고 또 각각의 언어를 받아드리는 기계가 4가지가 있다는 것이다. 그리고 문법, 언어, 기계 이 3가지가 equivanace relation 가진다. 오토마타의 종류와 그와 관련된 문법과 언어는 아래와 같다.

|Type|Grammar|Language|Machine|
|---|---|---|---|
|type 0 |무제한 문법(unrestricted grammar)|재귀적 열거가능 언어(recursively enumerable language)|Turing mahcine|
|type 1|문맥민감 문법(context-sensitive grammar)|문맥민감 언어(context-sensitive language)|Linear bounded automata|
|type 2|문맥자유 문법(context-free grammar)|문맥자유 언어(context-free language)|Push-down automata|
|type 3|정규문법(regular grammar)|정규언어(regular language)|Finite state machine(유한 상태 기계) 또는 Finite automata|

### Turing Mahcine
튜링 머신은 입력, 출력, 내부상태, 무한한 크기의 1차원 테이프 저장공간을 갖는 오토마타이다. 
튜링 머신은 재귀 열거 언어를 기술하는 기계다. 그리고 이때 사용하는 재귀 열거 언어는 현실 세계의 모든 문제들은 재귀 열거 언어로 표현할 수 있으며 튜링 기계는 기계적으로 계산가능한 모든 문제를 풀 수 있다고 추측된다 (처치 튜링 명제)

### Linear Bounded Automata
제한된 튜링 머신으로 튜링 머신처럼 무한한 길이의 테이프 위에서 계산하지 못하고, 테이프에서 입력 내용과 양쪽 끝 표시를 포함하는 부분 안에서만 계산할 수 있다. ([링크](https://ko.wikipedia.org/wiki/%EC%84%A0%ED%98%95%EC%9C%A0%ED%95%9C_%EC%9E%90%EB%8F%99_%EA%B8%B0%EA%B3%84))

### Push Down Automata
입력, 출력, 내부 상태, 무한한 크기의 스택을 갖는 저장공간을 갖는 오토마타이다. 스택에 필요한 정보를 읽거나 쓸 수 있기 때문에 유한 상태 기계보다 더 많은 언어를 받아드릴 수 있다. 실제로 입력, 저장, 연산, 출력, 제어장치로 이루어진 우리가 사용하고 있는 컴퓨터가 push down automata를 기반으로 만들어졌다. push down automata가 받아들이는 문맥자유언어는 또 다른 말로 프로그래밍 언어라고 할 수 있다.

### Finite State Machine
유한 상태 기계는 입력, 출력, 내부 상태 말고 다른 추가 저장공간을 갖지 않는 오토마타이다. 입력 문자열을 순서대로 읽으면서 읽은 글자와 내부 상태를 바꾸면서 동작한다. 유한 상태 기계가 받아들이는 언어를 정규문법으로 생성할 수 있는 정규언어인데, 우리가 보통 정규표현식이라고 하는 것도 정규언어이다. 대표적인 예시로 논리회로가 있는데, 순차적 논리회로는 유한 개의 저장공간을 가지므로 이를 내부상태로 생각해 유한 상태 기계로 표현할 수 있다 ([링크](https://namu.wiki/w/%EC%98%A4%ED%86%A0%EB%A7%88%ED%83%80))

---

# 프로그래밍 언어 및 컴파일러
강의교재 : [Compilers-Principles Techniques and Tools ](https://m.yes24.com/Goods/Detail/75840338)
compiler principles, techniques, and tools by alfred v aho monica s lam ravi sethi
## 목차
1. introduction
2. lexical analysis
3. syntax analysis
4. semantic analysis
5. intermediate code generation
6. code optimization

## 요약
Language translator
- assembler
- compiler
  - source code -> preprocessor(파일 포함, 매크로) -> 확장된 source code -> 컴파일러 -> 어셈블러 -> Relocatable object file(재배치 가능 기계코드) -> Linker -> 하나의 relocatable object file -> Loader -> Executable object file
  - 대표적인 c컴파일러가 gcc인데 이것말고 돈받고 파는 컴파일러도 존재한다.
- preprocessor
  - 기능
    - File inclusion(ex. compile-time libraries)
      - 프로그램에 헤더 파일을 포함시킨다. 즉 라이브러리를 사용할 수 있도록한다. 예를들어 #include <stdio.h> 가 포함되어있다면 이 자리에 표준 입출력과 관련된 함수들로 대체한다.
    - macro substitution
    - conditional compilation 
      - 소스코드에서  컴파일 안해도 되는 것들이 있다. 예를들어 machine depedent한 소스코드가 있는데 리눅스에서 컴파일을 하는데 윈도우에서만 돌아가도록 짠 코드는 굳이 컴파일하지 않아도 된다.
  - 컴파일러/인터프리터를 사용할 때 보조로 사용함
- interpreter
  - 고급 언어로 작성된 프로그램을 한줄 단위로 번역과 실행을한다.
- cross compiler
  - machine a에서 target code를 만들고 machine b에서 실행할 수 있도록 하는 컴파일러이다. 실제로 mac 또는 window에서 앱을 개발하고 컴파일을 한 후 스마트폰이나 태블릿에서 실행한다.
- byte code compiler

### 컴파일 과정
----------소스코드를 분석하는 부분----------
1. Lexical analysis(어휘 분석)
2. Syntax analysis(Parsing)(구문 분석)
3. Semantic analysis(의미 분석)

----------타켓코드를 생성하는 부분----------

4. Intermediate code(중간코드) 생성
5. Code optimization(코드 최적화)
6. Object code generation

영어를 번역할 때도 문장의 단어를 파악한 뒤(lexical analysis)에 각각의 단어에 대해 8개의 품사 중에 어디에 해당하는지, 문장의 어떤 구성 요소(주어, 동사, 목적어 등)에 해당하는지를 구분한다(syntax analysis) 그리고 단어만 바로 번역을 하는 것이 아니라, 한글 문법에 맞게 번역을 해야한다. (sementic analysis) 그리고 한글 단어 가운데 더 자연스러운 단어를 선택해 번역한다 (code optimization)

### 1. Lexical analysis
lexical analyzer(scanner)를 통해 구현하게 되는데 source code를 입력으로 받아 token sequence를 출력한다. 컴파일러 내부의 lexical analysis 과정을 통해 효율적이고 다루기 쉬운 정수(token number)로 바꾸어준다. c scanner, java scanner, python scanner 등을 따로 구현해야한다. 대부분의 토큰에 대해서는 token value가 필요없지만 변수명이나 number, str의 경우 값이 필요한 경우가 있다. 이 token number, token value의 쌍으로 출력한다. (32, 0), (7, 0), (4, a), ...
- 예시
    - source code: if(a > 10)
    - token: if, (, a, >, 10, )
    - token number: 32, 7, 4, 25, 5, 8, 43
    - token value: 0 0 'a' 0 10 0

위 예시처럼 토큰을 표현할 때 토큰 번호(token number)와 토큰 값(token value)의 순서쌍으로 표현한다. 토큰 번호는 각각의 토크들을 구분하기 위해 각각의 토큰들에게 고유의 내부 번호를 부여한 정수코드이고, 토큰 값은 토큰들 중에 identifer 또는 constant는 하나의 이름으로 여러번 사용할 수 있으므로 여러번 사용될 때마다 다르게 표현하는 것이 아니라 프로그래머가 사용한 값으로 구별하기 위한 값이다. 실제로 이를 symbol table의 형태로 만들어서 관리하는데, symbol table은 identifier와 constant의 name과 attribute 정보를 수집하고 저장한다. 변수, 상수의 이름이나 타입들의 정보를 테이블 형태로 정리하며 lexical analysis, code generation 등에서 사용한다. identifier 또는 상수의 토큰 값은 symbol table에서 식별자나 상수가 위치하는 포인터 값으로 표현된다.

토큰은 의미가 있는 최소 단위이다. 토큰 종류는 크게 sepecial form과 general form으로 나눌 수 있는데 special form은 언어마다 따로 정의되어있고 token value가 필요없는 반면에 general form은 token value가 필요하다.
- Special form: language designer
  - keyword(if, for, while, else, switch 등)
  - operator symbols(+, -, > 등)
  - delimiters(,, ;, (, ) 등)
- General form: programmer
  - identifer (변수명, 상수명, 클래스명 등)
  - constant(정수, 실수, string, comment 등)

### 2. Syntax analysis
syntax(구문, 문장구조) analysis는 입력을 lexical analysis의 결과인 token sequence를 받아 문장의 구조를 분석하고 주어진 문법(grammer)에 맞는지를 검사하여 올바른 문장이면 결과를 parse tree 또는 syntax tree를 출력한다. syntax analysis를 다른 말로 parsing, syntax analyzer는 parser라고도 한다. parser의 주요 기능으로 syntax checking과 tree geneation이 있는데 맨 왼쪽에 있는 토큰부터 하나씩 쭉 읽어오면서 코드가 틀렸으면 error message를 출력하고, 코드가 맞으면 prgram struction(tree 형태)를 출력한다. 

### 3. Sementic anaylsis
sementic(의미) analysis에서 가장 중요한 기능 중 하나가 type check(형 검사)이다. 각 연산자들이 규칙에 의해 허용된 operand를 가졌는가를 검사한다. 또는 예를들어 정수와 실수의 연산을 허용한다면 sementic analyer는 정수를 실수로 type conversion 등을 수행한다.

### 4. Intermediate code generator
Intermediate code(machine independent 코드)를 생성하고 나중에 최적화를 통해 최종코드를 생성한다.

### 5. Code optimizaer 
- local optimization
  - constant folding
  - eliminating redundant load, store instructions
  - strength reduction
- global optimization
  - flow analysis technique
  - common subexpression
  - moving loop invariant
  - removing unreachable code

### 6. Target code generator
Intermediate code로 부터 machine instruction 생성

