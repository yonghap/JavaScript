# Promise

비동기 처리에 사용되는 객체이며, 비동기 처리의 완료 또는 실패 결과 값을 나타냅니다.
비동기는 특정 코드의 실행이 완료될 때까지 기다리지 않고 다음 코드를 먼저 수행하는 자바스크립트의 특성입니다. <br>
이 비동기 객체의 실행에는 상태가 존재합니다.

<br>
<br>

> **pending** : 약속을 수행 전이다. <br>
> **fulfilled** : 약속이 지켜진 상태이다. <br>
> **rejected** : 약속이 지켜지지 못한 상태이다. <br>
> **settled** : 약속이 어떤 결과든 완료된 상태이다.
 
 <br>
 <br>

## 1. Promise 기초

```javascript
function sum(a, b) {
	return Promise(function (resolve, reject) {
	    setTimeout(function () {
	        if (typeof a !== 'number' || typeof b !== 'number') {
	            return reject(new TypeError('Inputs muse be numbers'));
            }
            resolve(a + b);           
        }, 1000);
    });
}

var myPromise = sum(10, 5);

myPromise.then(function (result) {
    // 성공시
    document.write('10 + 5 :', result);
    return sum(null, "foo");
}).then(function () { 
    // 실패시
}).catch(function (err) {
    // 오류발생시
    console.error(err);
})
```

<br><br>

## 2. 여러개의 Promise

promise1, promise2가 Promise 객체이므로 all 메소드 사용이 가능합니다.


```javascript
var promise1 = new Promise(function (resolve, reject) {
    setTimeout(function () {
        resolve('1st Promise');
    },3000);
});

var promise2 = new Promise(function (resolve, reject) {
    setTimeout(function () {
        resolve('2nd Promise');
    },5000);
});

Promise.all([promise1, promise2]).then(function (result) {
    console.log('Completed', result); // ['1st Promise', '2nd Promise'] 
})
```

<br>
<br>

## 3. 바로 실행되는 Promise

```javascript
var promise1 = new Promise(function (resolve, reject) {
    setTimeout(function () {
        resolve('1st Promise');
    },3000);
}).then(function (result) {
    console.log(result); // '1st Promise'
})
```