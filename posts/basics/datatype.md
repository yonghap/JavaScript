# 데이터 타입 (Data Types)

자바스크립트의 데이터 타입에는 기본(원시) 타입과 참조 타입이 있습니다. <br>
기본 타입은 할당하면 메모리에는 값이 저장됩니다. <br> 
그러나 참조 타입은 참조값이 저장됩니다. <br>
기본 타입의 변수를 다른 변수에 할당하면 원시값이 복사되어 전달됩니다.

<br>

## 1. 기본(원시 타입)

기본 타입에는 숫자, 문자열, 불리언, null, undefined, symbol(ES6에서 추가됨)이 있습니다.

### 숫자

```javascript
var intNum = 100;
var floatNum = 0.1;
```

### 문자열

```javascript
var singleQuoteStr = 'single quote string';
```

### 불리언

```javascript
var bool = true;
```

### null

```javascript
var nullVar = null;
``` 

### undefined 

```javascript
var emptyVar;
```

### symbol

```javascript
var myPrivateMethod = Symbol();
```

<br>

## 2. 참조 타입

참조 타입에는 객체,배열,함수,정규표현식 등 원시 타입이 아닌 형태가 모두 포함됩니다.

### 객체

```javascript
var foo = new Object();

foo.name = 'foo';
foo.age = 30;
```

```javascript
var foo = {
    name : 'foo',
    age : 30
}
```

### 함수

```javascript
var add = new Function('x','y','return x + y');

function add(x,y) {
    return x + y;
}
```

### 배열

```javascript
var color = ['orange','yellow','blue','green','red'];
```

### 유사배열객체

배열에 있는 length 프로퍼티는 일반 객체에서도 사용할 수 있습니다.<br>
이처럼 배열에 있는 프로퍼티를 사용할 수 있는 객체를 유사 배열 객체라 합니다.<br>
객체에 배열에 있는 메소드를 활용하려면 apply() 메소드를 활용합니다.

```javascript
var obj = {
    name : 'foo'
}
Array.prototype.push.apply(obj, ['bar']);
// { '1' : 'bar', name : 'foo'
```

<br>

###### 참고자료

* 인사이드 자바스크립트 (한빛미디어)