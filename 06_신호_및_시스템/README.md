# Overview
- 이 과목에서는 signal과 system에 대한 기본 개념을 배우고 signal을 분석하고 디자인하는 방법을 배운다.
- signals and system은 전자통신(과거에는 전기통신)을 하기 위해서 나온 개념이다. 즉 전자공학이라는 것은 통신공학에서 나왔는데 이 과목은 통신에서도 가장 기본이 되는 지식이고 통신에 대해 좀 더 공부하고 싶다면 디지털신호처리(digital signal process) 또는 통신공학 이라는 과목을 추가로 수강하면된다.
- 신호 및 시스템은 회로를 전공하는 사람, 제어를 전공하는 사람, ai system을 만드는 사람 모두에게 중요하다.
- 신호 및 시스템은 electrical engineering에서 매우 중요한 과목이다.

# Content
> The **concept** of signals and systems
1. Concept of signals and systems
2. Linear time-invariant(LTI) system

input signal -> system -> output signal 으로 이루어지는 일련의 과정을 continuous time domain, discrete time domain, frequency domain 에서 살펴볼 것이다. 신호는 시간의 함수로 나타나는 전류/전압 또는 음성이나 시간과 공간좌표의 함수로 나타나는 영상이 있을 수 있다. signal의 형태를 크게 continuous, discrete vs periodic, non periodic으로 2*2로 분류할 수 있다. 그리고 시스템은 input signal을 어떤 처리를 통해 output signal을 생성하는 장치인데 쉽게 말해 함수라고 생각하면 된다. 우리가 보통 시스템이라고 이야기하는 것의 예시를 몇가지 들어보자. 기지국과 기지국 사이에서 무선 통신을 통해 데이터가 전달되면서 신호에 잡음이 섞일 수 있는데 이 잡음을 효율적으로 제거하는 시스템 또는 데이터를 압축하는 과정에서 데이터의 소실이 일어났을 때 복원하는 시스템 등이 있을 수 있다. 옛날에 [이 글](https://www.facebook.com/dongsoo.lee.104/posts/10160268851347967)의 댓글 중 MPEG 압축개념의 초기 발명자가 국내분이었던 걸로 안다로 시작하는 글이 있는데 압축 이야기를 하다가 왜 갑자기 통신 알고리즘으로 이야기 흐름이 바뀌길래 뭔가 했었는데 결국 압축도 크게는 communications theory에서 중요하게 다루는 개념이라 그렇게 말했던 것 같다.

그리고 이 과목에서 실제로 오일러 공식($e^{i\theta} = cos\theta + i sin\theta)$을 기반으로 signal을 표현하게 되는데 이러한 complex형태의 signal이라는게 실제로 존재하는 것이 아니라 이렇게 표현하면서 얻는 수학적인 이점이 너무 크기 때문에 사용한다. ~~복소함수학이 이렇게 유용하게 쓰이고 있었구나싶다~~

> **How to analyze** linear time-invariant systems by using time-domain and frequency-domain approaches

3. Fourier series representation of periodic signals
    - periodic signal(composed of sinusoids)을 푸리에 급수의 형태로 표현할 수 있다.
    - 매우 강력한 representation 방법이다.
4. Continuous-time fourier transform(CTFT)
    - 푸리에 변환으로 continuous-time signal을 frequency domain으로 변환하여 분석한다.
5. Discrete-time fourier transform
    - 푸리에 변환으로 discrete-time signal을 frequency domain으로 변환하여 분석한다.
6. Time and frequency characterization of signals and system
    - discrete-time signal, continuous-time signal 이 들어가서 다시 discrete-time signal, continuous-time signal이 나오는 system을 time domain과 frequency domain에서 분석하는 법을 배운다.
    - time domain에서 anaysis든, design이든, synthesis 등을 해보려고 하는데 잘 안되면 그럼 frequency domain에서 같은 작업들을 해본다. 그리고 반대로 frequnecy domain에서 잘안된다? 그럼 time domain에서 해본다. 이런 방법들을 배우는 것이 이 과목의 핵심이다. (물론 어떤 특수한 형태에서만 이것이 가능하다는 한계가 있다는 것도 알고있자)

Fourier series 또는 Fourier transform 모두 **시간 영역의 신호를 주파수 영역의 신호로 변환** 하게 되는데 fourier series는 (유한한) periodic signal에 대해서만 변환할 수 있는 반면에 fourier series는 nonperiodic series에도 적용이 가능하다. frequency domain은 시스템을 설계할 때 해석이 용이해지는 장점이있다. 그리고 time domain signal을 frequency domain 으로 변환하여 분석하는데 representation만 달라질 뿐이지 신호 자체가 바뀌는 것은 아니다. 여기까지가 신호를 분석하는 것과 관련된 내용이고 이 아래부터 신호를 새로 디자인하거나 합성을 하게된다.

> **How to design** linear time-invariant systems by using time-domain and frequency-domain apporoaches

7. Laplace transform
    1. continuous signal과 그 system을 설계하는 방법(물론 분석에서도 사용가능)
    2. 제어 분야에서도 매우 중요하다. 자동제어 같은 과목 들어보면 laplace tranform을 한학기 동안한다.
8. Z-transform
    1. discrete signal과 그 system을 설계하는 방법(물론 분석에서도 사용가능)
    2. 디지털 신호처리 과목 들어보면 z-transform을 계속 듣게될거다.
    3. digital circult 또는 디지털 제어를 할 때도 나오는 개념이다.

> **How to convert** a continuous-time signal to a discrete-time signal, and vice versa

9. Sampling
    - sampling을 통해서 continuous time signal(아날로그 신호)을 discrete-time signal(디지털 신호)로 변환시킨다.
    - 한국이 옛날에 소니나 산요의 음향기기회사들의 오디오에서 잡음을 줄이는 기술을 쫓아갈 수 없어서 국내 회사들 제품을 쓰면 고장난게 아닌가 싶을 정도였다. 한국 전자회사들이 일본 전자회사들을 따라잡고 극복할 수 있었던 가장 중요한 계기는 electrical system들이 디지털화 되기 시작한 후 부터다. 
    - 과거에는 수학, 논리적인 operation들을 아날로그 서킷으로 구현했는데 이후에 디지털 서킷으로 구현되면서 우리가 일본을 역전했다. 아날로그 시그널을 디지털화 하는 것이 중요한데, 이 과정을 수학적으로 모델링한 것이 sampling이라는 것이다.
    - digital signal processor, cpu, digital controller들이 많이 생기면서 특정 논리 기능을 수행하는 회로를 디지털 서킷이나 디지털 시스템으로 구현하기 시작했다. 
        
        <details>
        <summary>digital signal processor(DSP) </summary>
        <div>
        digital signal processor는 디지털 신호를 처리하는 processor로 디지털 신호면 무엇이든 처리하는 장치를 말하며 카메라나 음향기기 등에 탑재되며 GPU도 DSP의 일종에서 출발했다. 현재 디지털 회로 시스템에서 구현되는 형태를 보면 애초부터 맨바닥에서 설계하는 경우는 매우 드물며, 소프트웨어로 구현된 프로그램을 초고속으로 처리하기 위해 필요로 하는 만큼의 성능을 보장하는 범용 DSP 개발 킷에 전용 프로그램을 작성하고 탑재하는 형태를 수행한다. 즉, 특정 기능을 수행하는데 소프트웨어만으로 가능은 하지만 더 빠른 처리 속도가 필요한 경우 이를 하드웨어로 구현하여 빠른 속도로 처리하는데 사용된다. 그래서 실시간으로 무엇을 처리해야하는 기기에는 필수 요소로 여러개가 들어간다. 일상생활에서 사용하는 기기는 물론, 디지털 회로가 장착된 통신분야(항공기, 유도탄, 레이더 등)에도 반드시 들어간다. 지금은 이 의미가 확대되어 주 프로세서를 대신하여 여러가지 복잡한 연산들을 진행하는 데에 쓰이는 특수 프로세서라는 의미를 가지는 경우가 많다. 이쯤되면 cpu, 메모리와 함께 디지털 시대의 꽃이라고 할만하다 (출처링크 : https://namu.wiki/w/Digital%20Signal%20Processor#s-3)
        </div>
        </details> 

# 참고
푸리에 급수 (by 3Blue1Brown)
- (정리 예정)
- Taylor series 가 approximation for a function이라면 Fourier series 는 approximation for a periodic signal이다.

푸리에 변환(by 3Blue1Brown)
- 복잡해보이는 signal을 받았을 때 pure한 frequency를 가진 signal로 decompose할 수 있을까? 여기서부터 시작한다.
- 어떤 신호의 intensity-time 그래프를 2차원 평면상의 원에 감는다고 생각하자. 특정 시점에서 원에 감긴 벡터의 크기는 그래프의 높이(intensity)와 같다.
- 그리고 그 원에 감긴 그래프가 질량을 가진다고 생각하자. 감는 진동수를 바꾸면 감긴 그래프의 모양이 변할텐데 그에 따라 감긴 그래프의 무게중심도 함께 변하게된다. 감는 진동수에 대해 무게 중심의 x좌표를 그래프로 나타냈을 때 갑자기 높은 peak 지점이 그래프에 나타내게 되는데, 이 지점이 intensity-time graph의 진동수(초당 진동수)와 감는 진동수(초당 회전수)가 같아 지는 지점이다.
- 실제로 임의의 두개의 진동수를 가진 신호를 더한 새로운 신호를 가지고 위와 같은 방법으로 감는 진동수와 무게중심의 x좌표 그래프로 나타냈을 때 두개의 봉우리 지점이 생기게되는데, 새로운 신호를 이 두 봉우리 지점의 진동수를 가진 두개의 pure한 진동수를 가진 신호로 다시 decompose 할 수 있다는 것이다.
- 특정 intensity-time 그래프에서 frequenry-cos 그래프로 변환을 하게 되면 특정 진동수에 높은 봉우리가 있는 그래프로 변환이 될 것인데, 이 과정을 푸리에 변환 과정이라하고 반대로 특정 봉우리를 없애는 등의 조작을 통해 다시 intensity-time 그래프로 변환을 하게 되는데 이 과정을 역(inverse)푸리에 변환이라고한다. 
- rough하게 설명했을 때 푸리에 변환한것을 다시 푸리에 변환하면 원래 함수와 비슷한 함수를 얻는다는데 나중에 좀 더 찾아보자.
- 원래 $g(t)$라는 intensity-time 그래프가 있고 이를 감는 진동수 f를 변수로 그래프를 원에 감는 행위를 2차원 평면상에 표현한다고 했을 때 $g(t)e^{-2\pi ift}$ 라는 식으로 표현할 수 있다. 그리고 무게 중심을 구하기 위해서 각 그래프 위의 점을 무한개 가까이 선택하고 더한 후 점의 개수로 나누어 다음과 같은 식을 얻을 수 있는데 $\frac{1}{t_2 - t_1} \int_{t1}^{t2} -g(t)e^{-2\pi i t} dt$ 이 수식은 감긴 그래프의 무게 중심을 가리키게된다.
- 실제 푸리에 변환은 $\frac{1}{t_2 - t_1}$ 항이 없애는데, 이는 무게중심 자체를 보는 것이 아니라 무게 중심 방향 벡터에 n초만큼이 곱해진 형태로 나타나게되어 어떤 진동수가 오랜 시간 지속될수록 그 진동수에서의 푸리에 변환 값이 커지게된다. 하지만 시간이 지날수록 원에 감긴 그래프가 고르게 분포하는 효과가 생기기 때문에 실제로 원에 감긴 전체 그래프의 무게중심의 크기는 서로 상쇄가 되어 무게중심이 특정 방향으로 무한히 증가하는 형태가 되진않는다.
- 그래서 푸리에 변환의 최종 식은 진동수의 형태로 나타나며 아래처럼 나타낼 수 있다. 
$$\hat{g}(f) = \int_{t_1}^{t_2} g(t)e^{-2\pi ift}dt$$


# Reference

신호 및 시스템 개요
- https://www.youtube.com/watch?v=cRRd7uAj9es&list=PL2fxOURY4wI6M9MIXhn119lMd5iiBgnt-

Fourier Series
- https://www.youtube.com/watch?v=r6sGWTCMz2k&t=138s

Fourier Transform
- https://www.youtube.com/watch?v=spUNpyF58BY&
- https://www.youtube.com/watch?v=MBnnXbOM5S4 
