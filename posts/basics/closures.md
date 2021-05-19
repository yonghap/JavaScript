# 클로저 (Closures)

클로저란 생명 주기가 끝난 외부 함수의 변수를 참조하는 함수를 클로저라고 합니다.

<br>

##  1. 클로저 개념 
 
```javascript
function makeFunc() {
    var name = "Mozila";
    function displayName() {
        alert(name);
    }
    return displayName;
}
var myFunc = makeFunc();
myFunc(); // Mozila
```

makeFunc 함수가 끝나면 name 변수에 더 이상 접근할 수 없게 예상하는 것이 일반적입니다.<br>
하지만 위 예제의 경우 함수를 리턴하고 리턴하는 함수가 클로저를 생성하게 됩니다.

myFunc은 makeFunc이 실행될 때 생성된 displayName 함수의 인스턴스에 대한 참조입니다.<br>
displayName의 인스턴스는 변수 name이 있는 스코프에 대한 참조를 유지합니다.


```javascript
function makeAdder(x) {
    var y = 1;
    return function(z) {
        y = 100;
        return x + y + z;
    }
}

var add5 = makeAdder(5);
var add10 = makeAdder(10);
// 클로저에 저장됩니다.

console.log(add5(2)); // 107 (5+100+2)
console.log(add10(2)); // 112 (10+100+2)

```

<br>

## 2. 클로저 예제

### private 메소드

```javascript
var counter = (function() {
    var privateCounter = 0;
    function changeBy(val) {
        privateCounter += val;
    }
    return {
        increment: function() {
            changeBy(1);
        },
        decrement: function() {
            changeBy(-1);
        },
        value: function() {
            return privateCounter;
        }
    };   
})();

console.log(counter.value()); // logs 0
counter.increment();
counter.increment();
console.log(counter.value()); // logs 2
counter.decrement();
console.log(counter.value()); // logs 1
```

위 예제의 경우 privateCounter 변수나 changeBy 함수에 접근할 수 없으며,<br>
세 개의 퍼블릭 함수를 통해서만 접근이 가능합니다.

<br>

## 3. 클로저 실수

### 변경된 private 변수

```javascript
function func() {
    var x = 1;
    return {
        func1 : function () { console.log(++x); },
        func2 : function () { console.log(-x);}
    }
}

var f = func();
f.func1();
f.func2();
// 이미 x 라는 변수가 변경되어 있어 원치 않는 결과값이 나옵니다.
```

### 반복문내의 순차적 실행

```javascript
function count(s) {
    for (var i = 1; i <= s; i++ ) {
        setTimeout(function () {
            console.log(i);
        },i * 1000);
    }
}
count(4); // 5,5,5,5,5
// 반복문은 이미 반복이 끝나고 i가 5인 상태에서 setTimeout의 함수가 실행됩니다. 
```


```javascript
function counter(s) {
    for (var i = 1; i <= s; i++ ) {
        (function (currentI) {
            setTimeout(function () {
                console.log(currentI);
            },currentI * 1000);
        })(i);
    }
}
counter(4);
// 루프를 돌때마다 i 값을 매개변수로 가지는 함수가 실행됩니다.
```

<br>

## 4. 클로저에서의 var와 let

### var

```javascript
function showHelp(help) {
    document.getElementById('help').innerHTML = help;
}

function setupHelp() {
    var helpText = [
        {'id': 'email', 'help': 'Your e-mail address'},
        {'id': 'name', 'help': 'Your full name'},
        {'id': 'age', 'help': 'Your age (you must be over 16)'}
    ];

    for (var i = 0; i < helpText.length; i++) {
        (function() {
            var item = helpText[i];
            document.getElementById(item.id).onfocus = function() {
                showHelp(item.help);
            }
        })(); // Immediate event listener attachment with the current value of item (preserved until iteration).
    }
}

setupHelp();
```

### let

```javascript
function showHelp(help) {
    document.getElementById('help').innerHTML = help;
}

function setupHelp() {
    var helpText = [
        {'id': 'email', 'help': 'Your e-mail address'},
        {'id': 'name', 'help': 'Your full name'},
        {'id': 'age', 'help': 'Your age (you must be over 16)'}
    ];

    for (var i = 0; i < helpText.length; i++) {
        let item = helpText[i];
        document.getElementById(item.id).onfocus = function() {
            showHelp(item.help);
        }
    }
}

setupHelp();
```

함수 스코프인 var와 블록 스코프인 let에 따라 클로저의 사용 방법이 다릅니다.

<br>

###### 참고자료

* 인사이드 자바스크립트 (한빛미디어)
* <a target="_blank" href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Closures">클로저 - JavaScript | MDN </a>