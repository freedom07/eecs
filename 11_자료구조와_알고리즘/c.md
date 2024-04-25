> Edited in 2019.5.18
```
아래의 정리노트는 패스트캠퍼스의 올인원패키지 컴퓨터공학의 나동빈님의 강좌와 유뷰트의 [두들낙서] 님의 두들낙서의 C/C++강좌를 바탕으로 정리하였습니다.
```

# c
소스코드
(전처리기)
advanced 소스코드
(컴파일러)
목적코드
(링커)
실행파일

## 변수와 상수
라이브러리 불러오기
- c/c++에서는 #include 명령어를 이용해 다양한 라이브러리를 불러올 수 있다.

메인함수
- c/c++에서는 다양한 함수가 사용될 수 있으나 프로그램은 항상 메인(main)함수로부터 시작된다 (entry point)
- 함수는 반환 값(return value)이 없을 수도 있으나 메인함수에서는 항상 0을 반환하는 것이 일반적이다.

변수의 선언
```c
int a;
int a = 7;
```

기본 출력
- <stdio.h> 헤더 파일에 선언된 printf() 함수를 이용해서 기본적인 정수 데이터를 출력한다.

변수의 초기화와 쓰레기 값
- 초기화 되지 않은 변수는 쓰레기 값이 들어간다.
- 정적변수로 선언된 것은 기본적으로 0으로 값이 초기화된다.



기본적인 자료형

- int
- long long
- double
- string
- bool
- char

형변환 : 자료형을 다른 자료형으로 바꾸는 작업

```c
#include <stdio.h>

int main() {
    int math = 90, korean = 95, english = 96;
    int sum = math + korean + english;
    // 정수 / 정수 = 정수
    // double avg = sum / 3;
    
    double avg = (double)sum / 3
    
    printf("%f\n", avg); // 93.666667
}
```

sizeof 함수

```c
#include <stdio.h>

int main() {
    // 4 1 4 8
	printf("%d %d %d %d\n", sizeof(int), sizeof(char), sizeof(float), sizeof(double));

	int a; char b; float c double d;
    //4 1 4 8
	printf("%d %d %d %d\n", sizeof(a), sizeof(b), sizeof(c), sizeof(d));
}
```

## 기본 입출력
`scanf()` 는 c언어에서 특정한 변수에 값을 넣기 위해서 사용한다. Visual Studio는 기본적으로 취약한 함수를 사용할 수 없도록 제한한다. 따라서 `_CRT_SECURE_NO_WARNINGS`를 적용한다. 또는 `scanf_s`를 써도된다.

`&`는 특정 변수의 주소를 의미한다. 실제로 컴퓨터는 특정한 메모리의 주소에 접근하여 데이터를 수정하므로 `&`를 이용하는 것이다. 그렇다면 메모리 주소에 얼마만큼의 크기로 데이터를 쓸 지 결정해야한다. `printf()`는 단순히 데이터를 넘기고, `scanf()`는 입력 받을 주소를 나타내기 위해 `&`를 사용한다. 
```c
#include <stdio.h>
#define _CRT_SECURE_NO_WARNINGS

int main() {
    int a, b;
    
    scanf("%d%d", &a, &b);
    printf("%d + %d = %d\n", a, b, a+b);
}
```
형식 지정자(format specifiers): 데이터들을 화면에 출력하기 위해서 각각 형식 지정자가 존재한다. c언어에서 입력 받거나 출력할 때는 형식지정자를 적절히 따라야한다.

| format specifiers | size | desc|
|---|--|--|
|%d| int (4b)          | %d를 이용해서 정수형 데이터를 입력 및  출력 한다.    |
|%lld| signed long long(8b)     | %lld를 이용해서 큰 정수형 데이터를 입력 및 출력한다. |
|$lf| double (8b)       | 입력시 %lf, 출력시 %f로 큰 실수형 데이터를 처리한다. |
|%f| float (4b)        | %f를 이용해서 실수형 데이터를 입력 및 출력한다.      |
|%s| string (제한없음) | %s를 이용해서 문자열 데이터를 입력 및 출력한다.      |
|%c| char (1b)         | %c를 이용해서 문자 데이터를 입력 및 출력한다.        |


## 연산자
삼항 연산자
````c
#include <stdio.h>

int main(void){
    int a = 7, b = 7;
    printf("%d\n", (a==b) ? 100 : -100);
    return 0;
}
````

비트 연산자 : 비트단위의 연산을 수행할 수 있다.
- ~ : 부정
- & : 그리고
- | : 또는
- ^ : 배타적 (같으면 0, 다르면 1)
- << : 왼쪽 시프트
  - 왼쪽 시프트를 수행하면 2배 증가하고 오른쪽 시프트를 수행하면 2로 나눈 값이 반환된다. 

## 배열
```c
int a[10] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
```

문자열과 배열
- 원시적인 c언어는 기본적으로 자체적인 문자열 자료형을 제공하지 않는다. 따라서 c언어에서는 문자를 여러개 묶어 놓는 형태로 문자열을 표현한다. c++에서는 이러한 불편함을 알고 있기 때문에 자체적으로 string 자료형을 제공한다. 

```c
char a[20] = "Hello world"
```

문자열 선언 : 기본적으로 문자열을 선언할 때 문자열의 크기보다 배열의 크기가 크도록 해야하며 %s라는 형식 지정자를 사용한다. 

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {
    char a[20];
    scanf("%s", &a);
    printf("%s\n", a);
}
```

배열을 매개변수로 넘기기

```c
#include <stdio.h>

void printArr(int arr[4]) {
	for (int i = 0; i < 4; i++) {
		arr[i] *= 2;
	}
}


int main() {
	int arr[4] = { 1, 2, 3, 4 };
	printArr(arr);

	// 출력 :2 4 6 8
	// printArr은 call-by-reference 함수이다.
	for (int i = 0; i < 4; i++) {
		printf("%d ", arr[i]);
	}
}
```

## 포인터
포인터는 변수의 주소를 저장하는 변수이다. 포인터를 선언할 때 내가 가리킬 변수형을 적고 * 하고 포인터의 이름을 적어주면서 포인터를 선언한다. 

```c
// pointer example 1
#include <stdio.h>

int main() {
    int a = 20;
    
    int *ptr_a;
    
    // a의 주소를 ptr_a에 저장해라.
    ptr_a = &a;
    
    printf("a의 값 : %d\n", a); // 20
    printf("a의 주소값 : %d\n", &a); // 1617232
    printf("ptr_a에 저장된값 : %d\n", ptr_a); //  1617232
    printf("ptr_a가 가르키는 변수의 값 : %d\n", *ptr_a); // 20
}
```

```c
// pointer example 2
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {
	int a = 5;
	int *b = &a; // b는 a를 가리킨다
	int **c = &b; // c는 b를 가리킨다.
	printf("%d\n", &a); // a 주소값
	printf("%d\n", *b); // a값
	printf("%d\n", b); // a 주소값
	printf("%d\n", &b); // b 주소값
	printf("%d\n", **c); // a 값
	printf("%d\n", *c); // a 주소값
	printf("%d\n", c); // b 주소값
	printf("%d\n", &c); // c 주소값
	system("pause");
	return 0;
}
```

```c
// pointer example 3
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {
	int a[] = { 1, 2, 3, 4, 5 };
	int *b = a;
	printf("%d\n", &b); //18217036
	printf("%d\n", b); // 18217048
	printf("%d\n", *b); // 1
	printf("%d\n", &b[0]); // 18217048
	printf("%d\n", &b[1]); // 18217052
	printf("%d\n", &b[2]); // 18217056
	printf("%d\n", &b[3]); // 18217060
	printf("%d\n", &b[4]); // 18217064
	system("pause");
	return 0;
}
```

## 문자
char : 1바이트 정수형이다. char는 문자를 저장할 때 좋은 변수이지만 모든 문자를 담을 수 있는게 아니라 반각문자만 담을 수 있다. 반각문자는 다음과같다. (ABCabc12345_+!@#$%^%*) 그리고 반각문자가 아닌것은 한자, 한글, 일본어 등이있다.

ASCII : 문자를 숫자랑 대응시켜주는 표준으로([링크](https://goo.gl/8MMQCe)) c프로그램의 문자는 아스키코드를 따른다. 아스키 코드는 0~127 중 1바이트로 구성되며 주요 문자를 출력하도록 해준다. (ex. 0: 48, A: 65, a: 97)

```c
#include<stdio.h>

char a = 65;
printf("%d", a); // 65

printf("%c\n", a); // A
printf("%c\n", 'A'); // A
printf("%d\n", 'A') // 65
```

char 자체에 숫자를 넣어서 처리할 수 있다. 우리 눈에는 문자로 보이지만 컴퓨터가 해석을 할 때는 숫자로 해석한다. 

```c
#include <stdio.h>

int main(void) {
    char a = 65;
    printf("%c\n", a);
}
```
개행문자도 아스키코드로 관리한다. 기본적으로 아스키코드가 숫자로 표현되었듯이 내부적으로 모든 문자들은 숫자로 관리된다. 그리고 문자 입출력함수 중 하나인 `getchar()` 는 단 하나의 문자를 입력받는다.
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {
	int a;
	char c;
    int temp;
	scanf("%d", &a);
	printf("%d\n", a);
	while((temp = getchar()) != EOF && temp != '\n') {}
	scanf("%c", &c);
	printf("%c\n", c);
	return 0;
}
```

## 문자열
`char arr[] = "abc"` 라는 의미는 `char arr[]  = { 'a', 'b', 'c', '\0'};` 이다. 끝에 `null` 문자가 있다. 문자열은 컴퓨터 메모리 구조상에서 마지막에 `null`값을 포함하는데 `null`은 문자열의 끝을 알리는 목적으로 사용된다. `printf` 함수를 실행하면 컴퓨터는 내부적으로 `null`을 만날 때까지 출력한다. 문자열을 출력하거나 뒤에 나올 문자열에 관련된 함수를 실행시키면 `\0`이 문자열의 중간에 나오면 그 이후로는 처리하지 않는다. 참고로 c++ 에서는 string 이라는 자료형이 있으며 char와 배열의 형태로 된 문자열은 c에서만 주로 쓴다.

```c
// string example 1

#include <stdio.h>

int main() {
    // 불편함
    // char arr[100] {'h', 'e', 'l', 'l', 'o'};
	
    char arr[] = "Hello world!";
    // 문자열을 한번에 출력하고 싶을 때 %s를 쓰면됨
    printf("%s\n", arr);
}
```

```c
// string example 2

#include <stdio.h>

int main() {
    char arr[] = "Hello world!";
    printf("배열의 크기: %d\n", sizeof(arr) / sizeof(char));
    // 문자의 길이는 13인데 계산결과는 14이다.
}
```

```c
// string example 3

#include <stdio.h>

int main() {
    char s[100];
    
    // &s하면 에러가난다.
    scanf("%s", s);
    printf("%s\n", s);
}
```

문자열 형태로 포인터를 사용하면 포인터에 특정한 문자열 주소를 넣게된다. 다음 코드는 "Hello world"문자열을 읽기 전용으로 메모리 공간에 넣은 뒤에 그 위치를 처리한다. 이러한 문자열을 '문자열 리터럴' 이라고 말하며 이는 컴파일러가 알아서 메모리 주소를 결정한다.

문자열은 배열로 처리되고 배열은 포인터로 치환될 수 있다. 포인터로 문자열을 선언했다고해도 기존의 배열처럼 처리가능하다.

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {
	char *a = "Hello world";
	printf("%s\n", a);
	return 0;
}
```

```c
// string example 4 - 문자열을 매개변수로 받아 공백을 제거한 후 출력해보기
#include <stdio.h>

void printf_noSpace(const char str[]) {
	for (int i = 0; str[i] != '\0'; i++) {
		if (str[i] != ' ') {
			printf("%c", str[i]);
		}
	}
}

int main() {
	printf_noSpace("Hello world\n");
}
```

## 함수
``` c
#include <stdio.h>

// return을 만나는 즉시 함수가 종료된다.
int noMeaning() {
    printf("first\n");
    return 1;
    printf("second\n");
    return 2;
} 

int main() {
    int a;
    a = noMeaning();
    printf("반환된 값 : %d\n", a);
}

// first
// 반환된 값 : 1
```

```c
#include <stdio.h>

// return을 만나는 즉시 함수가 종료된다.
void noMeaning() {
    printf("first\n");
    return;
} 

int main() {
    noMeaning();
}
```

### call by value vs call by reference

상황 1. 두 수의 값을 바꾸기로 했을 때

```c
// call by value

#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

void swap(int x, int y) {
	int tmp = x;
	x = y;
	y = tmp;
}

int main() {
	int a, b;
	scanf("%d%d", &a, &b);

	// a와 b가 바뀌지않는다.
	swap(a, b);
	printf("a = %d, b = %d\n", a, b);
}
```

```c
// call by reference
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

void swap(int *x, int *y) {
	int tmp = *x;
	*x = *y;
	*y = tmp;
}

int main() {
	int a, b;
	scanf("%d%d", &a, &b);

	// a와 b가 바뀐다.
	swap(&a, &b);
	printf("a = %d, b = %d\n", a, b);
}
```

## 재귀함수(recursion)

```c
// recursion example 1

#include <stdio.h>

void rec(int n) {
	if (n > 5) return;
	printf("n=%d\n", n);
	rec(n + 1);
 }

int main() {
	rec(1);
}
```

```c
// recursion example 2 - ƒactorial
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int factorial(int a) {
    if (a == 1) return 1;
    else return a * factorial(a - 1);
}

int main(void) {
    int n;
    printf("n 팩토리얼을 계산합니다.");
    scanf("%d", &n);
    printf("%d\n", factorial(n));
}
```

```c
// recursion example 3
#include <stdio.h>

void rec(int n) {
    if (n == 0) {
        return;
    }
    printf("%d", n);
    rec(n-1);
    printf("%d", n);
}

int main() {
    rec(5);  // 5432112345
}
```

##Prototype
아래 코드는 잘못된 코드이다. 아래 코드는 실행이되지 않는다. `main()` 함수안에서 `drawSquare()`를 찾을 수 없기 때문이다. 이를 막기 위해 prototype이란 개념을 도입한다. 함수가 어떻게 생겼는지만 알려주고(선언하고) 정의는 나중으로 미룬다. 그리고 함수를 호출한다.

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

// 걷기
void walk(int distance) {
	printf("%dcm를 걸었습니다.\n", distance);
}

// 돌기
void rotate(int angle) {
	printf("%d도 회전했습니다.\n", angle);
}

int main() {
	drawSquare();
}

void drawSquare() {
	for (int i = 1; i <= 4; i++) {
		walk(10);
		rotate(90);
	}
}
```

아래는 수정된 코드이다.
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

// 타입만 적어줘도된다.
// void walk(int);
void walk(int distance);

// void rotate(int);
void rotate(int angle);

// void drawSquare();
void drawSquare();

int main() {
	drawSquare();
}
 
void drawSquare() {
	for (int i = 1; i <= 4; i++) {
		walk(10);
		rotate(90);
	}
}

// 걷기
void walk(int distance) {
	printf("%dcm를 걸었습니다.\n", distance);
}


// 돌기
void rotate(int angle) {
	printf("%d도 회전했습니다.\n", angle);
}
```





## 컴퓨터가 변수를 처리하는 방법
프로그램 메모리 주소
1. 컴퓨터에서 프로그램이 실행되기 위해서는 프로그램이 메모리에 적재(Load) 되어야한다.
2. 당연히 프로그램의 크기를 충당할 수 있을 만큼 메모리 공간이 있어야한다.
3. 일반적인 컴퓨터의 운영체제는 메모리 공간을 네가지로 구분하여 관리합니다.
    - 스택 영역 (지역변수, 매개변수)
    - 힙 영역 (동적할당변수)
    - 데이터 영역 (전역변수, 정적변수)
    - 코드영역 (소스코드)

전역변수
- 전역변수란 프로그램의 어디서든 접근 가능한 변수를 말한다.
- main 함수가 실행되기도 전에 프로그램의 시작과 동시에 메모리에 할당된다.
- 프로그램의 크기가 커질수록 전역변수로 인해 프로그램이 복잡해질 수 있다.
- 메모리의 데이터 영역에 적재된다.

지역변수
- 지역변수란 프로그램에서 특정한 블록에서만 접근할 수 있는 변수를 말한다.
- 함수가 실행될 때마다 메모리에 할당되어 함수가 종료되면 메모리에서 해제된다.
- 메모리의 스택영역에 기록된다.

정적변수
- 정적변수란 특정한 블록에서만 접근할 수 있는 변수이다.
- 프로그램이 실행될 때 메모리에 할당되어 프로그램이 종료되면 메모리에서 해제된다.
- 메모리의 데이터 영역에 적재된다

```c
#include <stdio.h>

void process() {
    // 프로그램 실행과 동시에 메모리에 적재된다.
    static int a = 5;
    a = a + 1;
    printf("%d\n", a);
}

int main(void) {
    process(); // 6
    process(); // 7
    process(); // 8
    return 0;
}
```

레지스터 변수
- 레지스터 변수란 메인 메모리 대신 CPU의 레지스터를 사용하는 변수이다. 
- 레지스터는 매우 한정되어 있으므로 실제로 레지스터에서 처리될지는 장담할 수 없다.
- 레지스터 변수를 사용하면 일반 변수를 사용할 때보다 더 빠르게 처리될 것이라는 기대를 할 수 있다.

함수의 매개변수 처리
1. 값에 의한 전달: 값에 의한 전달 방식은 단지 값을 전달하므로 함수내에서 변수가 새롭게 생성된다.
2. 참조에 의한 전달: 참조에 의한 전달 방식은 주소를 전달하므로 원래의 변수 자체에 접근 할 수 있다.

```c
// 값에 의한 전달방식

#include <stdio.h>

void add(int a, int b) {
    printf("%d\n", a + b);
}

int main(void) {
    int a = 7;
    add(a, 10);
    printf("%d\n", a); // 7
    return 0;
}
```

```c
// 참조에 의한 전달방식

#include <stdio.h>

void add(int *a) {
    *a = (*a) + 10;
}

int main(void) {
    int a = 7;
    add(&a);
    printf("%d\n", a); // 17
    return 0;
}
```

## 다차원배열과 포인터배열
배열은 포인터와 동일한 방식으로 동작한다. 배열의 이름은 배열의 원소의 첫번째 주소가 된다. 유일한 차이점이라고 하면, 포인터는 변수이며 배열의 이름은 상수이다.

```c
#include <stdio.h>

int main(void) {
    int a[5] = {1, 2, 3, 4, 5};
    // a와 &a[0]은 같다.
    printf("%d\n", a);
    printf("%d\n", &a[0]);
}
```

포인터 배열의 구조 분석
- 배열의 이름은 배열의 첫번째 원소의 주소라는 것을 기억한다.
- 포인터는 연산을 통해 자료형의 크기만큼 이동한다.
  - 예시) 크기가 10인 double(8 bytes)형 배열을 선언했을 때 배열의 시작 주소가 X라고 한다. 배열의 마지막 원소의 주소는? X+72
- 배열을 포인터처럼 사용해 각 원소에 접근할 수도 있다

```c
// 포인터를 배열처럼 사용할 수 있다.

#include <stdio.h>

int main(void) {
    int a[5] = {1, 2, 3, 4, 5};
    int *b = a;
    printf("%d\n", b[2]);
    return 0;
}
```

```c
// pointer example 1

#include <stdio.h>

int main(void) {
	int a[5] = { 1, 2, 3, 4, 5 };
	for (int i = 0; i < 5; i++) {
		printf("%d", *(a+i));
	}
	system("pause");
	return 0;
}
```

```c
// pointer example 2
// int *ptr = &a 일 때 ptr + 1은 실제로 ptr에 4byte가 더해진다. 

int main() {
    int arr[10] = {1, 2, 3, 4 ,5 ,6, 7, 8, 9, 10};
    
    // 표현1
    for (int i = 0; i < 10; i++) {
 		printf("%d ", arr[i]);       
    }
    
    // 표현2
    for (int i = 0; i < 10; i++) {
        printf("%d ", *(arr+i));
    }
    printf("\n");
    
    // 표현3
    for (int *ptr = arr; ptr < arr + 10; ptr++) {
        printf("%d ", *ptr);
    }
    printf("\n");
}
```

```c
// pointer example 3

#include <stdio.h>

int main(void) {
	int a[5] = { 1, 2, 3, 4, 5 };
	int *p = a;
	printf("%d\n", *(p++)); // 1
	printf("%d\n", *(++p)); // 3
	printf("%d\n", *(p + 2)); // 5

	system("pause");
	return 0;
}
```

```c
// pointer example 4
// 2차원 배열 또한 포인터로 처리할 수 있다. (뒤에 나올 배열포인터와 관련있음)

#include <stdio.h>

int main(void) {
	int a[2][5] = { {1, 2, 3, 4, 5}, {6, 7, 8, 9, 10} };
	// 특정한 행을 가리키는 포인터를 만들었다. 아래는 2차원배열이다.
	int(*p)[5] = &a[0];
	for (int i = 0; i < 5; i++) {
		printf("%d", p[0][i]);
	}
	return 0;
}
```

```c
// pointer example 5

#include <stdio.h>

// a[i] == *(a + i) = *(ptr + i) = *(i + ptr) = i[ptr]
// 실제로 c언어에서 a[b]를 인식할 때 *(a + b)로 바꾸어서 처리하는 것 같다.

int main() {
	int a[3] = {1, 2, 3};
	int *ptr = a;
	for (int i = 0; i < 3; i++) {
		printf("%d", i[ptr]); // 신기하게도 이게 실행이됨, 실무에서는 안쓰는게좋음.
	}
}
```

```c
// pointer example 5
// 1. ptr == &ptr[0]
// 2. *ptr == ptr[0]
// 3. ptr + 1 == ptr에 sizeof(*ptr)을 더한 값이다.

int main() {
    int arr[3] = { 1, 2, 3};
    
    printf("arr = %d\n", arr); // 1636420
    printf("arr + 1 = %d\n" ,arr + 1); // 1636424
    printf("&arr == %d\n", &arr); // 1636420
    printf("&arr + 1 %d\n", &arr + 1);  // 1636432
}
```

## 배열포인터
배열 포인터 : 배열자체를 가리키는 포인터

```c
int main() {
    int arr[3] = { 1, 2, 3};
    
    int(*ptr_arr)[3]; // 길이 3인 int형 배열을 가리키는 포인터를 선언
    ptr_arr = &arr;
    
    // 1 2 3
    for (int i = 0; i < 3; i++) {
        printf("%d ", (*ptr_arr)[i]);
    }
}
```

2차원 배열과 배열 포인터 
```c
#include <stdio.h>

int main() {
    int arr[2][3] = {{1, 2, 3}, {4, 5, 6}};
    
    printf("%d\n", sizeof(arr)); // 24
    printf("%d\n", sizeof(arr[0])); // 12, 0번째 행 전체를 하나의 배열로본다.
    printf("%d\n", sizeof(arr[0][0])); // 4
    
    // arr[0] = {1, 2, 3}
    // arr[1] = {4, 5, 6}
}
```

정말 중요한 예제
```c
/*
    arr가 1차원뿐만 아니라 2, 3차원 모두 해당된다.
    1. arr == &arr[0] (이 사실이 제일 중요한 것 같다)
	2. *arr == arr[0]
	3. ptr + 1 == ptr에 sizeof(*ptr)을 더한값
*/

#include <stdio.h>

int main() {
    int arr[2][3] = {{1, 2, 3}, {4, 5, 6}};
    
    // ptr은 3개짜리 배열을가지고있고 첫번째 행의 배열의 주소값을 의미한다.
    // int (*ptr)[3] = arr;
    int (*ptr)[3] = &arr[0];
    
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 3; j ++){
            printf("%d ", ptr[i][j]);
        }
        printf("\n");
    }
    // ptr은 행 전체를 가리키는 포인터이기 때문에 ptr에 1이 더해질 때 마다 그 다음행을 가리키기 때문에 ptr + 1을 할 때마다 그 다음 행을 가리킨다고 이해해도된다.
    // 그래서 prt[i] == arr[i]이며 ptr[i][j] == arr[i][j]이고 ptr == arr이라고 할 수 있다.
    
    // int arr[3] = {1, 2, 3}이 있을 때 int *ptr = arr로 하면 ptr을 배열처럼 사용할 수 있었듯이(ptr[0], ptr[1], ptr[2]) 이차원배열을 포인터로 치환하고 싶다면 이차원배열의 한 행을 가리킬 수 있는 포인터를 만들고 그 배열 포인터에다가 arr를 집어넣기만 하면된다. 배열포인터가 이차원배열 역할을 할 수 있다.
}
```

```c
// 배열포인터 예제1

#include <stdio.h>

int main() {
	int arr[3] = { 1, 2, 3 };

	int(*ptr_arr)[3]; // 길이 3인 int형 배열을 가리키는 포인터를 선언
	ptr_arr = &arr;

    // 19922216 19922228 19922240
    // 12byte씩 증가한다.
	for (int i = 0; i < 3; i++) {
		printf("%d ", ptr_arr + i);
	}
}
```

```c
// 배열포인터 예제2 (위 아래 차이)

#include <stdio.h>

int main() {
	int temp[3] = { 1, 2, 3 };
    // int *arr = &temp 는 에러뜸
    int *arr = temp;

	printf("%d\n", arr); // 100
	printf("%d", arr + 1); // 104
}
```

```c
#include <stdio.h>

int main() {
	int temp[3] = { 1, 2, 3 };
	int(*arr)[3] = &temp;
    // int *arr = temp는 에러뜸
    

	printf("%d\n", arr); // 100
	printf("%d", arr + 1); // 112
}
```

```c
// 배열포인터 예제3

#include <stdio.h>

int main() {
    int arr[2][3] = {{1, 2, 3}, {4, 5, 6}};
    
    // row에 1을 더하게 되면 12바이트 뒤의 주소값 즉 두번째 행을 가리키게된다.
    // col은 그냥 포인터변수이다. 포인터 변수에 값이 저장된 것이다.
    // row는 3개짜리 배열을 가리키고 있으므로 *row 자체가 하나의 배열(칸 1개 배열)을 의미하게된다. 따라서 col에는 *row, 즉&(*row)[0]이 들어가게된다.
    
    /*
    출력
    123
    345
    */
    for (int(*row)[3] = arr; row < arr + 2; row++) {
        for (int *col = *row; col < *row + 3; col++) {
            printf("%d", *col);
        }
        printf("\n");
    }
}
```

## 포인터 배열
배열 포인터 : 배열을 가리키는 포인터, 포인터가 1개짜리다.

포인터 배열 : 포인터들이 배열, 포인터가 여러개다.

```c
#include <stdio.h>

int main() {
    // 배열 포인터
    // int (*ptr)[4] : 4개짜리 int형 배열을 가리키는 포인터
	
    // 포인터 배열
    int a =10;
    int b = 20;
    int c = 30;
    int d = 40;
    int *ptr[4];
    
    ptr[0] = &a;
    ptr[1] = &c;
    ptr[2] = &d;
    ptr[3] = &b;
    
    printf("%d %d %d %d\n", *ptr[0], *ptr[1], *ptr[2], *ptr[3]);
}
```

```c
#include <stdio.h>

int main() {
    char str[] = "Hello"; // null문자까지 합쳐서 6개의 char배열이 만들어지는데 이것을 문자열이라고 부름
    
    printf("%s\n", str);
    printf("%s\n", &str[0]); // %s는 0번째 칸의 주소를 알려주면, 0번째 칸을 가리키는 포인터를 적어주면 null문자가 나올 때까지 순서대로 출력해준다.
}
```

```c
#include <stdio.h>

int main() {
	char strings[3][10] = {"Hello", "World", "Yun"};
   	char *p_str[3];
    
    for (int i =0 ; i < 3; i++){
        p_str[i] = &strings[i][0];
        // p_str[i] = strings[i]
    }
    
    for (int i = 0; i < 3; i++){
        printf("%s\n", strings[i]);
        printf("%s\n", &strings[i][0]);
        // strings[i] 자체가 배열이자 포인터다.
    }
}
```

### 예시 문제 1
```
100개 이하의 정수를 입력받아 첫 줄에 짝수 번째 숫자들을 순서대로 출력하고, 다음 줄에 홀수 번째 숫자들을 순서대로 출력하는 프로그램을 만들어보세요.

입력 예

7

3 1 4 1 5 9 2



출력 예

1 1 9

3 4 5 2
```

풀이1
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>

int main() {
	int size;
	scanf("%d\n", &size);
	int *numptr = (int *)malloc(sizeof(int) * size);
	for (int i = 0; i < size; i++) {
		scanf("%d", (numptr + i));
	}

	for (int i = 0; i < size; i++) {
		if ((i+1) % 2 == 0) {
			printf("%d ", numptr[i]);
		}
	}
	printf("\n");
	for (int i = 0; i < size; i++) {
		if ((i+1) % 2 == 1) {
			printf("%d ", numptr[i]);
		}
	}
	free(numptr);
}
```

풀이2

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>

int main() {
	int n;
	int arr[105];

	scanf("%d", &n);
	for (int i = 0; i < n; i++) {
		scanf("%d", &arr[i]);
	}

	for (int i = 1; i < n; i += 2) {
		printf("%d ", arr[i]);
	}
	printf("\n");

	for (int i = 0; i < n; i += 2) {
		printf("%d ", arr[i]);
	}
}
```

### 예시문제 2

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>

int main() {
	int arr[3][3] = { 0 };

	printf("%d\n", &arr[0][0]); //100
	
    // arr[0]은 0번째 행(1개의 배열)을 의미한다.
	// arr[0] 첫번째 주소값인데 &arr[0][0]과 같은 말이다.
    printf("%d\n", arr[0] + 1); // 104
	
    // &arr은 이차원배열전체를 가리키게되고 &arr[0]은 첫번째 행 전체를 의미한다. 여기서 1을 더하면 다음 행을 가리키게된다.
	printf("%d\n", &arr[0] + 1); // 112
	
    // 위랑 같은 의미이다.
	printf("%d\n", arr + 1); // 112
	
    // arr은 이차원배열을 가리키고 1을 더하면 36을 더하게된다.
	printf("%d\n", &arr + 1); // 136
}
```

arr + 1을 생각할 때
1. 첫번째방식
     - 2차원배열이거나 1차원배열일 때 그냥 배열을 쓰게되면 첫번째 요소의 값을 의미한다. 2차원배열의 첫번째 요소는 첫번째 행이고 1차원배열의 첫번째요소는 첫번째 칸이다. 그래서 arr라는 2차원배열이 정의되어있고 arr+1을 했을 때 arr는 첫번째 행을 가리키게되고 1을 더하게되면 다음행을 가리키게된다. arr라는 1차원배열이 정의되어있을 때 첫번째요소는 첫번째칸이고 arr+1을 하게되면 두번째칸을 나타내게된다. 
2. 두번째방식
    - &arr[0] + 1이라고 생각한다. 



### 1차원 배열

```c
int arr[3] = {1, 2, 3};
int *ptr = arr
```

라고 나타내면 ptr을 1차원배열처럼 쓸 수 있다.


### 2차원 배열

```c
int arr[2][3] = {{1, 2, 3}, {4, 5, 6}};
int (*ptr)[4] = arr
```
라고 나타냈을 때 ptr을 2차원배열처럼 쓸 수 있다. 그냥 `arr`은 `&arr[0]`으로 바꾸어 생각하면 편하다.

## 동적 메모리할당
일반적으로 c언어에서 배열의 경우 사전에 적절한 크기만큼 할당해주어야한다. 우리가 원하는 만큼만 메모리를 할당해서 사용하고자 한다면 동적 메모리 할당을 사용한다. 동적이라는 말의 의미는 '프로그램 실행 도중에'라는 의미이다. c언어에서는 `malloc()`함수를 이용해 원하는 만큼의 메모리 공간을 확보할 수 있다. `malloc()`은 메모리 할당에 성공하면 주소를 반환하고, 그렇지 않으면 NULL을 반환한다. malloc()은 <stdlib.h> 라이브러리에 정의되어있다. 

동적으로 할당된 변수는 메모리의 힙영역에 저장된다. 전통적인 c언어에서는 스택에 선언된 변수는 따로 메모리 해제를 해주지 않아도된다. 반면에 동적으로 할당된 변수는 반드시 free() 함수로 메모리 해제를 해주어야한다. 메모리 해제를 하지 않으면 메모리 내의 프로세스 무게가 더해져 언젠가는 오류가 발생한다. 메모리 누수(Memory Leak) 방지는 코어 개발자의 핵심 역량이다. `malloc()`과 `free()` 함수는 한쌍이다. `free()`를 통해 메모리 해제를 한다.

```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    int *a = malloc(sizeof(int));
    printf("%d\n", a);
    free(a);
    a = malloc(sizeof(int));
    printf("%d\n", a);
    free(a);
    return 0;
}
```

### 동적으로 문자열 처리하기
일괄적인 범위의 메모리를 모두 특정한 값으로 설정하기 위해서는 `memset(포인터, 값, 크기)`을 사용한다. 한 바이트 씩 값을 저장하므로 문자열 배열의 처리 방식과 흡사하다. 따라서 `memset()`는 <string.h> 라이브러리에 선언되어있다.

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(void) {
    char *a = malloc(100);
    memset(a, 'A', 100);
    for (int i = 0; i < 100; i++) {
        printf("%c", a[i]);
    }
    return 0;
}
```

이차원 배열 만들기 예제 (원래는 free 함수를 사용해야하는데 여기서는 생략했다)
```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    // 3개의 행 만들기
    int** p = (int**)malloc(sizeof(int*) * 3);
    for (int i = 0; i < 3; i++) {
        // 3개의 열 만들기
        *(p + i) = (int*)malloc(sizeof(int) * 3);
    }
    for (int i = 0; i < 3; i++){
        for (int j = 0; j < 3; j++) {
            *(*(p + i) + j) = i * 3 + j;
        }
    }
    for (int i = 0; i < 3; i++){
        for (int j = 0; j < 3; j++){
            printf("%d", *(*(p + i) + j));
        }
        printf("\n");
    }
    return 0;
}
```

```
(패스트캠퍼스 강의 댓글 중)

이전 강의 내용을 살펴보시면 *는 포인터 연산자이며, 실습 과정으로 (int *)를 이용하여 int 형을 가리키는 포인터 변수를 직접 선언하여 사용한 적이 있습니다. 이 때 포인터 변수도 '변수' 이므로 메모리 공간에 할당되어야 합니다. 그래서 그에 맞는 정해진 크기가 존재합니다. 이는, 항상 고정된 것은 아니며 일반적인 컴퓨터의 경우 포인터가 8 Bytes 혹은 4 Bytes 크기를 가진다고 이해하실 수 있습니다.

포인터는 변수의 주소를 저장하기도 하지만
배열 그 자체를 나타낼때도 사용돼요.
(엄연히 따지자면 배열의 첫번째칸의 주소를 나타내요)
일단 다른거 다 제껴두고 이야기하자면
포인터 = 배열
포인터의 포인터 = 배열의 배열 (이차원 배열)
이라고 할 수 있어요.
이런게 가능한 이유는 배열의 내부동작에 있어요.
배열은 값을 첫번째 칸을 기준으로 일정한 간격으로 메모리에 저장하여
첫번째 칸의 위치(주소)만 알면 배열 내의 어떤 칸에도 접근 가능하다는 장점이 있어요.
첫번째 칸의 주소만 알면 된다는 특징 때문에
배열을 단순히 첫번째 칸의 주소(포인터)로 표현할 수 있는 거에요.

example)
// 10칸짜리 배열 생성 (int 값 10개)
// 여기서 포인터 a 는 a[0]의 주소
// *a 와 a[0] 는 같다
int* a = (int*)malloc(sizeof(int) * 10);
// 그럼 a[1]은?
a[1] = 5;
// 둘다 똑같이 출력된다
printf("%d\n", a[1]);     // 일반적인 배열값 접근법

printf("%d\n", *(a+1)); // 첫번째 칸을 기준으로 + 1 칸의 포인터로부터 값을 가져온다

(int**)를 붙인건 그 형태로 변환할거야! 라는 뜻이에요. malloc함수는 기본적으로 void* 형태를 반환하는데, 
이 void*는 어떤 형태의 포인터로도 변신할 수 있는 만능 자료형이에요. 어찌보면 자료형이 없다고 할 수 있죠.
이전까진 딱히 변환하지 않아도 문제가 없었는데 이중포인터로의 변환은 필요하기 때문에 갑자기 추가된 것 같아요.

포인터도 따지고보면 메모리의 크기를 명확히 상수로 반환할 수 있는 자료형이 맞긴 해요.
어떤 자료형의 포인터인지 상관없이 포인터는 주소를 저장하고 있기 때문에  4바이트로 고정되어 있어요.(32비트 빌드 기준).
```

## 함수 포인터
C언어 프로그램의 모든 함수는 내부적으로 포인터 형태로 관리할 수 있다. C언어에서는 함수의 이름을 이용해 특정한 함수를 호출한다. 함수 이름은 메모리 주소를 반환한다.

```c
#include <stdio.h>

void function() {
    printf("It's my function");
}

int main(void) {
    printf("%d\n", function); //14095326
    return 0;
}
```

```c
// 함수 포인터는 특정한 함수의 반환 자료형을 지정하는 방식으로 선언할 수 있다.
// 함수 포인터를 이용하면 형태가 같은 서로 다른 기능의 함수를 선택적으로 사용할 수 있다. 

#include <stdio.h>

void myFunction() {
    printf("It's my function.");
}

void yourFunction() {
    printf("It's your function.);
}

int main(void) {
    void(*fp)() = myFunction;
    fp(); // It's my function
    fp = yourFunction;
    fp(); // It's your function
    return 0;
}
```

```c
// 매개변수 및 반환 자료형이 있는 함수포인터

#include <stdio.h>

int add(int a, int b) {
    return a + b;
}

int sub(int a, int b) {
    return a - b;
}

int main(void) {
    int(*fp)(int, int) = add;
    printf("%d\n", fp(10 ,3));
    fp = sub;
    printf("%d\n", fp(10 ,3));
    return 0;
}
```

```c
// 함수포인터를 반환하여 사용하기
// 반환자료형 (*이름)(매개변수) = 함수명

#include <stdio.h>

int add(int a, int b) {
     return a + b;
}

int (*process(char* a))(int, int) {
    printf("%s\n", a);
    return add;
}

int main(void) {
    printf("%d\n", process("10과 20을 더해보겠습니다.")(10, 20));
    return 0;
}
```

## 구조체
구조체를 활용하여 자신만의 자료형을 만들 수 있다. 여러개의 변수를 묶어 하나의 객체를 표현하고자 할 때 구조체를 사용할 수 있다.

구조체의 정의와 선언

```c
struct structName {
    // 자료형1 변수명1;
    // 자료형2 변수명2;
}
```

한명의 학생에 대한 정보를 담고있는 구조체
```c
struct Student {
    char studentId[10];
    char name[10];
    int grade;
    int major;
}
```

구조체의 변수의 선언과 접근
```c
struct Student s;
strcpy(s.studentId, "20155168);
strcpy(s.name, "Yun Jegal");
s.grade = 4;
strcpy(s.major, "컴퓨터공학과")
```

구조체의 정의와 선언
- 하나의 구조체 변수만 사용하는 경우 정의와 동시에 선언을 할 수도 있다.
- 이 경우 변수는 전역 변수로 사용된다.
```c
struct Student {
    char studentId[10];
    char name[10];
    int grade;
    char major[51];
} s;
```

```c
struct Student {
    char studentId[10];
    char name[10];
    int grade;
    char major[51]; 
} s = {"20155168", "Yun Jegal", 3, "컴퓨터공학과"};
```

더 짧게 구조체 정의하기
- typedef 키워드를 이용하면 임의의 자료형을 만들 수 있으므로 선언이 더 짧아진다. 원래는 `struct Student s`와 같이 앞에 struct를 붙여야지 구조체 자료형인지 알 수 있는데 귀찮기 때문에 아래 코드의 의미는 `struct Student`를 그냥 `Student`라고 부르겠다는 의미이다.

```c
#include <stdio.h>

typedef struct Student {
    char studentId[10];
 	char name[10];
    int grade;
    char major[51];
} Student;

int main(void) {
    Student s = {"20155168", "Yun Jegal", 3, "컴퓨터공학과"}
}
```

익명 구조체의 개념이 등장하여, 구조체 이름 부분을 비워놓아도된다.
```c
typedef struct {
    char studentId[10];
 	char name[10];
    int grade;
    char major[51];
} Student;
```

구조체가 포인터 변수로 사용되는 경우 내부 변수에 접근할 때 화살표(->)를 사용한다.

typedef(type + definition)형을 정의한다. 예를들어 unsigned short int age를 usi age라고 축약해서 자료형을 정의한다. 

int를 Int32로 새로 정의함

```c
#include <stdio.h>

int main() {
	typedef int Int32;
	Int32 n = 20;

	printf("%d\n", n);
}
```

배열을 새롭게 정의

```c
#include <stdio.h>

int main() {
	typedef int Pair[2];
	Pair point = { 3, 4 }; // int point[2] = {3, 4};
}
```

포인터를 새롭게 정의
```c
#include <stdio.h>

int main() {
	typedef const char *String;

	String name = "Yun"; // char *name = "Yun";
	printf("이름: %s\n", name);
}
```

```c
#include <stdio.h>

// 구조체는 주로 전역변수로 많이쓴다.
// struct Point {int x, y;}
typedef struct { int x, y; } Point;

int main() {
	Point p;

    // p = {3, 4} 로 해도됨
	p.x = 3;
	p.y = 4;

	printf("%d %d", p.x, p.y);

}
```
