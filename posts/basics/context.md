# 실행 컨텍스트, 스코프, 호이스팅 (Context, Scope, Hoisting)

<br>

## 1. 실행 컨텍스트

컨텍스트는 실행 가능한 자바스크립트 코드 블록이 실행되는 환경입니다.

###  컨텍스트 개념
 
```javascript
console.log('Global context');

function ExContext1() {
    console.log('This is ExContext1');
}

function ExContext2() {
    ExContext1();
    console.log('This is ExContext2');
}

ExContext2();
```

컨텍스트를 그림으로 표현하면 아래와 같습니다.

![ExContext](https://user-images.githubusercontent.com/7742074/97782292-0cff3280-1bd4-11eb-9429-24e8569b9537.jpg)

전역 컨텍스트가 가장 먼저 실행되고, <br>
다른 함수 호출이 발생하면 새로운 컨텍스트가 만들어지고 실행되며,<br>
종료되면 반환됩니다.

<br>

## 2. 스코프

스코프는 변수가 사용될 수 있는 범위입니다.<br>
스코프는 전역(글로벌) 스코프와 지역 스코프로 나뉘고,<br>
지역 스코프는 블록 스코프와 함수 스코프로 나뉩니다.

### 전역 스코프

```javascript
const hello = 'some value';

function sayHello() {
    console.log(hello); 
}

sayHello(); // some value
console.log(hello); // some value
```

### 지역 스코프

#### 함수 스코프

함수 내에서만 엑세스 할 수 있습니다.

```javascript
function sayHello() {
    const hello = 'Hello World';
    console.log(hello); 
}

sayHello(); // Hello World
console.log(hello); // Error
```

#### 블록 스코프

{} 블록내에서만 엑세스 할 수 있습니다.<br>
'const','let'으로 선언할 수 있습니다.<br>
함수는 중괄호로 선언되어야 하므로 블록 스코프는 함수 스코프의 하위요소 입니다.

```javascript
{
    const hello = 'Hello World';
    console.log(hello);
}

console.log(hello); // Error
```

<br>

## 3. 호이스팅

function으로 선언된 함수가 현재 스코프의 가장 상단으로 이동하는것을 호이스팅이라고 합니다.<br>
함수 표현식으로 선언된 함수는 호이스팅 되지 않습니다.

### 호이스팅 O

```javascript
sayHello();

function sayHello() {
    console.log('Hello World');
}
```

```javascript
function sayHello() {
    console.log('Hello World');
}
sayHello();
```

### 호이스팅 X

```javascript
sayHello() // Error
const sayHello = function () {
    console.log('Hello World');
}
```

<br>

###### 참고자료

* 인사이드 자바스크립트 (한빛미디어)
* <a target="_blank" href="https://css-tricks.com/javascript-scope-closures/">JavaScript Scope and Closures by Zell Liew </a>