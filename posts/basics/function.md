# 함수 (function)

<br>

## 1. 함수 선언 방식

함수의 선언은 선언문 방식, 익명 함수 방식, 생성자 함수 방식이 있습니다.<br>
더글러스 크락포드는 함수 호이스팅 문제로 함수 표현식 사용을 권장하고 있습니다.

### 선언문 방식

```javascript
function add(x, y) {
    return x + y;
}

console.log(add(3,4)); // 7
```

### 표현식 방식

```javascript
var add = function (x, y) {
    return x + y;
}
```

익명 함수는 호이스팅이 되지 않습니다.
따라서 아래와 같은 코드는 오류가 발생 합니다.


```javascript
console.log(add(3,4));

var add = function (x, y) {
    return x + y;
}

// ERROR
```

### 생성자 선언 방식

```javascript
var add = new Function('x', 'y', 'return x + y');
```

<br>

## 2. 함수의 형태

함수의 다양한 선언 방식 이외에도 다양한 형태가 있습니다.
콜백 함수, 즉시 실행 함수, 내부 함수, 리턴 함수 등이 있습니다.

### 콜백 함수

특정 시점이나 이벤트가 발생했을 때 실행합니다.

```javascript
window.onload = function () {
    alert('Callback Function');
}
```

### 즉시 실행 함수

함수를 정의함과 동시에 실행합니다.
외부 코드에서 함수 내부의 변수에 접근할 수 없어 프라이빗을 유지하거나,
함수의 선언과 동시에 실행하기 위해서 쓰입니다.

```javascript
(function (x, y) {
    return x + y;
})(3,4);

// 7
```

```javascript
(function IIEF_local() {
    // private 변수
    let foo;
    let bar;
})
```

```javascript
let result = (function () {
    // 리턴하는 IIEF
    return 'Hello World';
}());
```

### 내부 함수

함수 내부에 선언된 함수입니다.
내부 함수 child에서는 부모함수에 선언된 a를 리턴합니다.

```javascript
function parent() {
    var a = 100;
    var child = function () {
        console.log(a);
    }
    
    return child;
}

var inner = parent();
inner();
// 100
```


### 리턴 함수

함수도 일반 값처럼 리턴할 수도 있습니다.
첫 호출에는 a가 출력되지만 다음 호출에는 리턴 함수가 호출 됩니다.

```javascript
var self = function () {
    console.log('a');
    return function () {
        console.log('b');
    }
}

self = self(); // a
self(); // b
```

<br>

## 3. 함수도 객체이다

함수도 객체입니다.
코드 실행뿐만 아니라 일반 객체처럼 프로퍼티를 가질 수 있습니다.
주로 프로토타이핑에 쓰입니다.

```javascript
function add(x, y) {
    return x + y;
}

add.result = add(3, 2);
add.status = 'OK';

console.log(add.result); // 5
console.log(add.status); // OK
```

<br>

###### 참고자료

* 인사이드 자바스크립트 (한빛미디어)
* 모던 웹을 위한 JavaScript/jQuery 입문