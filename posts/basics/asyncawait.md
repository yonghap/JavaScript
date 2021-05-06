# async

promise를 좀더 쉽고 편하게 사용할 수 있는 문법입니다.<br>
function 구문 앞에 async를 붙이면 항상 promise를 반환합니다.

<br>
<br>

## 1. async

```javascript
async function foo() {
    return 1;
}
```
위 코드는 아래 코드와 같습니다.

```javascript
function foo() {
    return Promise.resolve(1);
}
```

<br>
<br>

## 2. await

async 함수 내에서만 쓰이며 promise가 resolve나 reject 될 때까지 기다리기 위해서 사용됩니다.

```javascript
function resolve3After(x) {
    return new Promise(resolve => {
        setTimeout(() => {
            resolve(x);
        },3000);  
    })
}

async function f1() {
    var x  = await resolve3After(30);
    console.log(x); // 30
}

f1();
```

만약 값이 promise가 아니라면 해당 값은 resolve가 된 promise로 변환됩니다.

<br>
<br>

```javascript
async function f2() {
    var y = await 20;
    console.log(y); // 20
}

f2();
```

만약 promise가 reject가 되면 reject 된 값이 throw 됩니다.

<br>
<br>

```javascript
async function f3() {
    try {
        var z = await Promise.reject(20);
    } catch(e) {
        console.log(e); // 20
    }   
}

f3();
```

async, await를 사용하면 promise.then().catch()를 사용할 수 없기 때문에 try catch 문을 사용합니다.<br>
다만 아래의 예제를 사용하면 reject를 다룰 수 있습니다.

<br>
<br>


```javascript
var response = await promisedFunction().catch((err) => { console.error(err); });
```