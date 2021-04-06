# Promise

비동기 처리에 사용되는 객체입니다.<br>
비동기는 특정 코드의 실행이 완료될 때까지 기다리지 않고 다음 코드를 먼저 수행하는 자바스크립트의 특성입니다.


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
    document.write('10 + 5 :', result);
    return sumb(null, "foo");
}).then(function () {
}).catch(function (err) {
    console.error(err);
})
```