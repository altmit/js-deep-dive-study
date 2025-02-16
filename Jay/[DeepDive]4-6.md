# 4장 변수

### 변수

- 하나의 값을 저장하기 위해 확보한 메모리 공간을 의미한다.

- 메모리에 2진수로 저장한다.

- 식별자는 값이 아닌 메모리 주소를 기억한다.

- js는 메모리 제어가 불가능하다.

### 식별자

- 변수이름만 식별자가 아니다. (함수, 변수, 클래스 등)

### 변수 선언

**종류**

- var, let, const

**var 의 단점**

- 블록 레벨의 스코프가 아니다.
- 함수 레벨 스코프이다.

**자바스크립트 변수 선언 단계**

- 선언단계 : 이름을 등록해 자바스크립트 엔진에 변수의 존재를 알린다.
- 초기화 단계 : 값을 저장하기 위한 메모리 공간을 확보하고 undefined로 초기화한다.

**실행 컨텍스트**

- 변수명은 실행 컨텍스트에 등록된다.

- 실행 컨텍스트는 자바스크립트 엔진이 소스코드를 평가한다.

- 그리고 실행에 필요한 환경 제공하며 실행 결과를 관리한다.

- 엔진에서 변수명, 변수 값을 객체로 등록한다.

### 호이스팅

```jsx
var socre;
```

선언과 초기화를 동시에 한다.

암묵적으로 undefined로 초기화한다.

```jsx
console.log(score); // undefined

var score; // 변수 선언문
```

referenceError가 발생할것 같지만 에러 없이 undefined를 출력한다.

변수 선언이 런타임이 아니라 그 이전 단계에서 먼저 실행되기 때문이다.

**변수 선언문이 코드의 선두로 끌어 올려진 것처럼 동작하는 자바스크립트 고유의 특징 변수 호이스팅이다.**

변수 뿐 아니라 var, let, const, function, function\* class 모두 호이스팅된다.

### 값의 할당

```jsx
var score; // 변순 선언
score = 80; // 값의 할당

var score = 80; // 변수 선언과 값의 할당
```

둘은 정확히 동일하게 동작한다.

엔진에서 2개의 문으로 나눠 각각 실행한다.

**선언은 소스코드가 순차적으로 실행되는 시점인 런타임 이전에 먼저 실행되지만 값의 할당은 런타임에 실행된다.**

```jsx
console.log(score); // undefined

var score;
score = 80;

console.log(score); // 80

console.log(score); // undefined

var score = 80;

console.log(score); // 80
```

---

<img width="589" alt="스크린샷 2023-04-01 오후 6 56 36" src="https://user-images.githubusercontent.com/41321198/229279422-3337600a-5c99-44f7-9ecf-1247ce7591c3.png">

**변수 값을 할당할 때 이전 값 undefined가 저장되어 있던 메모리 공간을 지우고 그 메모리 공간에 할당 값 80을 새롭게 저장하는 것이 아니라 새로운 메모리 공간을 확보하고 그곳에 할당 값 80을 저장한다.**

```jsx
console.log(score);

score = 80;
var score;

console.log(score);
```

### 값의 재할당

```jsx
var score = 80;
score = 90;
```

var로 선언과 초기화를하는 과정도 재할당이라 할 수 있다.

초기화와 마찬가지로 새로운 공간을 만들고 그곳의 값에 해당 숫자를 넣는다.

### 식별자 네이밍 규칙

- 특수문자를 제외한 문자, 숫자, \_, $ 를 포함할 수있다.
- \_, $ 의 경우는 시작 문자로 사용해야 한다.
- 예약어는 사용불가

# 5장 표현식과 문

### 리터럴

리터럴은 사람이 이해할 수 있는 문자 또는 약속된 기호를 사용해 값을 생성하는 표기법

리터럴은 값을 생성하기 위해 미리 약속한표기법이라 할 수 있다.

### 표현식

평가될 수 있는 문을 의미한다.

즉 표현식이 평가되면 새로운 값을 생성하거나 기존 값을 참조한다.

표현식은 값으로 평가된다.

### 문

문은 프로그램 구성의 기본 단위이자 최소 실행 단위

문은 여러 토큰으로 구성된다. 토큰은 문법적 의미를 가지며 더 이상 나눌 수 없는 코드의 기본 요소

### 표현식인 문과 표현식이 아닌 문

표현식인 문과 표현식이 아닌 문을 구별하는 가장 간단한 방법은 변수에 할당해 보는 것이다.

```jsx
var foo = var x; // 표현식이 아닌 문은 값 처럼 사용 불가
```

표현식이 아니기 때문에 값으로 평가될 수 없다.

```jsx
var x; // 표현식이 아닌 문

x = 100; // 표현식인 문

var foo = (x = 100); // 표현식인 문은 값처럼 사용 가능
```

---

![1 PNG](https://user-images.githubusercontent.com/41321198/229279425-d6173998-d5b6-4c76-9abf-44d84f180ef8.png)

**크롬 개발자 도구에서 표현식이 아닌 문을 실행하면 undefined를 출력한다 이를 완료 값이라 한다.**

**표현식인 문을 실행하면 평가된 값을 반환한다.**

# 6장 데이터 타입

원시타입 : 숫자, 문자열, 불리언, undefined, null, 심벌

객체타입 : 객체, 함수, 배열등

### 숫자

js는 다른 언어와 다르게 숫자타입 한개만 존재한다.

**64비트 부동소수점 형식의 2진수로 저장된다.**

2진수, 8진수, 16진수를 표현하기 위한 데이터 타입을 제공하지 않기 때문에 이를 참조하면 모두 10진수로 나온다.

```jsx
var binary = 0b01000001;
var octal = 0o101;
var hex = 0x41;

console.log(binary); // 65
console.log(octal); // 65
console.log(hex); // 65
console.log(binary === octal);
console.log(octal === hex);
```

js는 정수만을 위한 타입은 없다. 모두 실수로 처리한다.

따라서 정수로 표시된 수끼리 나누더라도 실수가 나올 수있다.

```jsx
console.log(1 === 1.0);
console.log(4 / 2);
console.log(3 / 2);
```

특별한 값 표현도있다.

- Infinity : 양의 무한대
- -Infinity : 음의 무한대
- NaN : 산술 연산 불가(not a number)

### 템플릿 리터럴

es6부터 새로운 문자열 표기법이다.

백틱(``)을 사용해 표현한다.

```jsx
var template = `template literal`;
console.log(template);
```

**멀티라인 문자열**

일반 문자열 내에서는 줄바꿈이 불가하다.

그래서 줄바꿈, 공백을 표현하려면 **이스케이프 시퀀스**를 사용해야 한다.

템플릿 리터럴에서는 그냥 공백과 줄바꿈이 사용 가능하다

```jsx
var test = "hello\nworld";
console.log(test);

var test = `hello
world`;
console.log(test);
```

둘의 출력은 같다.

**표현식 삽입**

문자열의 경우 + 를 사용하여 삽입 가능하다.

템플릿 리터럴에는 표현식 삽입이 가능하다.

```jsx
var hello = "hello";

console.log(hello + " " + "world");

var hello = "hello";
console.log(`${hello} world`);
```

둘의 출력은 같다.

### 불리언 타입

true, false를 나타낸다.

### undefined

undefined는 개발자가 의도적으로 할당하기 위한 값이 아니라 자바스크립트 엔진이 변수를 초기화할 때 사용하는 값이다.

undefined 값을 개발자가 직접 할당하는것은 본래 취지와 어긋날뿐더러 혼란을 줄 수 있어 권장하지 않는다.

### null

프로그래밍 언어에서 null은 변수에 값이 없다는 것을 의도적으로 명시할 때 사용한다.

### 심볼

변경 불가원시 타입이다.

다른값과 중복되지 않는 유일무이한 값이다.

### 데이터 타입의 필요성

데이터를 2진수로 저장한다.

만약 숫자 65를 저장했다.

2진수로 저장하면 “0100 0001” 값을 저장하게 된다.

만약 이 값을 문자열로 해석하면 ‘A’가 될 것이고, 숫자로 해석하면 65가 된다.

그렇기 때문에 타입이 필요하다.

- 타입에 따라 메모리 공간의 크기를 결정하기 위해
- 참조할 때 한 번에 읽어야할 메모리 공간의 크기를 결정하기 위해
- 메모리에서 읽어 들인 2진수를 어떻게 해석할지 결정하기 위해

### 동적 타이핑

**동적 타입 언어와 정적 타입 언어**

c나 자바같은 정적타입 언어는 선언할 때 변수에 할당할 수 있는 타입을 선언해야한다.

```jsx
char c;

int num;
```

정적 타입 언어는 타입을 변경할 수 없다.

컴파일 시점에 타입을 체크한다.

타입이 맞지 않으면 에러가 뜬다.

자바스크립트는 타입을 선언하지 않는다.(동적 타입)

typeof연산자로 변수 타입을 확인할 수 있다.

```jsx
var foo;
console.log(typeof foo); // undefined

foo = 3;
console.log(typeof foo); // number

foo = 'Hello';
console. log(typeof foo); // string

foo = true;
console.log(typeof foo); // boolean

foo = null;
console.log(typeof foo); // object

foo = Symbol(); // 심벌
console. log(typeof foo); // symbol

foo = {}; // 객체
console. log(typeof foo); // object

foo = []; // 배열
console. log(typeof foo); // object

foo = function () 43; // 함수
console.log(typeof foo); // function
```

자바스크립트의 변수는 선언이 아닌 할당에 의해 타입이 결정된다.

재할당에 의해 변수의 타입은 언제든지 동적으로 변할 수 있다.

### 동적 타입 언어와 변수

언어에 유션성이 높지만 신뢰성이 떨어진다.

- 변수가 많을 수록 오류가 생길 확률이 높으며, 변수 남발 금물이다.
- 변수의 유효범위(스코프)를 최대한 좁게만들자.
- 전역 변수는 최대한 사용하지 않는다. 어디서든 참조/변경이 가능하면 의도치 않은 변경으로 코드에 영향을 줄 가능성이 있다.
- 변수보는 상수를 이용해 값의 변경을 억제한다.
- 변수 이름은 변수의 목적이나 의미를 파악할 수 있도록 네이밍한다.
