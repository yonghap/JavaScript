# Promise

비동기 처리에 사용되는 객체입니다.<br>
비동기는 특정 코드의 실행이 완료될 때까지 기다리지 않고 다음 코드를 먼저 수행하는 자바스크립트의 특성입니다.
이 비동기 객체의 실행에는 상태가 존재합니다.

> **pending** : 약속을 수행 전이다.
> **fulfilled** : 약속이 지켜진 상태이다.
> **rejected** : 약속이 지켜지지 못한 상태이다.
> **settled** : 약속이 어떤 결과든 완료된 상태이다. 

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