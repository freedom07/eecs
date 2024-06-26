# 파일 개념
파일은 운영체제에 의하여 정의되고 구현되는 추상적인 자료형이다. 파일은 논리 레코드의 연속으로써, 바이트, 행(길이가 고정 또는 가별) 또는 좀 더 복합적인 자료 항목들이다. 운영체제는 다양한 레코드형을 사용자에게 제공하거나 아니면 사용자가 프로그램상으로 정의하도록 해준다.

운영체제의 가장 중요한 문제는 논리적인 파일을 하드 디스크나 NVM 장치 같은 실제 저장장치에 어떻게 매핑 시키느냐이다. 보통 물리 레코드 크기는 논리 레코드 크기와 일치하기 때문에 논리 레코드를 물리 레코드에 연관시켜야한다. 이 작업은 운영체제에 의하여 제공되거나 사용자의 응용 프로그램에서 할 수 있다.

파일 속성

파일 연산

파일 유형

파일 구조

파일의 내부 구조

# 접근 방법
파일이 사용될 때는 정보가 반드시 접근되어 컴퓨터 메모리로 읽혀야 한다. 일부 시스템에서는 파일에 대해 단 하나의 접근 방법만 제공하는 운영체제도 있지만 대부분 많은 접근 방법을 지원하며 특정 응용 프로그램에 적합한 것을 선택하는 것이 주요 설계 문제이다.

순차접근

직접접근

기타 접근 방법
- 색인 : 찾고자 하는 레코드가 있으면 색인을 찾아 그에 대응하는 포인터를 얻는다. 그 포인터를 사용하여 파일에 직접 접근하여 원하는 레코드를 얻는다

# 디렉토리 구조
디렉토리는 파일 이름을 상응하는 파일 제어 블록으로 바꾸어 주는 심볼 테이블로 볼 수 있다. 디렉토리에 대한 연산은 아래와 같다.
- 파일 찾기
- 파일 생성
- 파일 삭제
- 디렉토리 나열
- 파일의 재명명
- 파일 시스템의 순회

1단계 디렉토리

2단계 디렉토리

트리구조 디렉토리

비순환 그래프 디렉토리
- 링크: 공유 파일(공유 디렉토리)를 구현하는 여러가지 방법 중 하나로, 새로운 디렉토리 항목을 만드는 것으로, 링크는 다른 파일이나 서브 디렉토리를 가리키는 포인터다.
- 여기서 문제점은 순환이 발생하지 않도록 어떻게 보장하느냐는 것이다.

일반 그래프 디렉토리

# 보호
정보가 컴퓨터에 저장되어 있을 때 물리적인 손상(신뢰성의 문제)과 부적절한 접근(보호의 문제)로부터 안전하길 원한다. 파일 시스템은 읽기나 쓰기 시의 오류와 같은 하드웨어 문제, 전류의 급격한 변화나 단절, 헤드 크래시, 먼지, 극한 온도 등으로 파괴 될 수 있기 때문에 백업이 중요하다. 보호는 여러가지 방법으로 제공될 수 있다. 

접근의 유형
- 읽기, 쓰기, 실행, 추가, 삭제, 리스트, 속성 변경

접근 제어
- 여러 사용자는 각 파일과 디렉토리에 대해 서로 다른 접근이 필요할 수 있는데 이를 구현하는 일반적인 방법은 각 파일과 디렉토리에 접근 제어 리스트(access control list, ACL)을 두는 것이다. 이 리스트는 특정 파일에 대해 누가, 어떤 연산을 사용할 수 있는지를 기술한다.
- 사용자 분류
    - 소유자
    - 그룹
    - 기타: 시스템에 있는 다른 사용자들

다른 보호 방법

# 메모리 사상 파일(Memory-Mapped Files)
open(), read(), wrtie() 시스템 콜을 사용하여 디스크에 있는 파일을 순차적으로 읽는 다고 생각해보자. 이런 방식을 사용하면 파일이 매번 엑세스 될 때마다 시스템 콜을 해야하고 디스크에 접근해야한다. 이 방법 말고 디스크 입출력을 메모리 참조 방식(가상 메모리 기법을 사용)으로 대신할 수도 있다. 이것을 메모리 사상 접근 방식이라고 부른다. 즉 가상 주소 공간 중 일부를 관련된 파일에 할애하는 것을 말한다.

기본 기법
- 파일의 메모리 사상은 프로세스 페이지 중 일부분을 디스크에 있는 파일의 블록에 매핑한다.