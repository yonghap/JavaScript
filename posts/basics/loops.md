# Loops  (반복문)

똑같을 명령을 일정 횟수만큼 실행합니다.

<br>
<br>

## 1. For

```javascript
for (var i =0; i < 10; i++) {
    document.write(i); // 0,1,2,3,4,5,6,7,8,9
}
````

<br>
<br>


## 2. For in  (Object)

```javascript
var students = {
    'name' : 'David',
    'age' : 25,
    'job' : 'Designer'
}

for (let i in students) {
    document.write(i); // "name,age,job"
    document.write(students[i]); // "David,25,Designer"    
}
```

<br>
<br>

## 3. For in (Array)

```javascript
var fruits = ['banana','apple','orange'];

for (let i in fruits) {
    document.write(fruits[i]); // "banana,apple,orange"
}
```

<br>
<br>

## 4. For of (ES6)

```javascript
var fruits = ['banana','apple','orange'];

for (let i of fruits) {
    document.write(i); // "banana,apple,orange"
}
```

<br>
<br>

## 5. forEach

```javascript
var fruits = ['banana','apple','orange'];

fruits.forEach((item, index) => {
    document.write(item); // "banana,apple,orange"
    document.write(index); // 0,1,2
});
```

<br>
<br>

## 6. While

```javascript
var i = 1;

while (i < 10) {
    document.write(i); // 1,2,3,4,5,6,7,,8,9
    i++;
}
```

<br>
<br>

## 7. Do While

```javascript
var i = 1;

while (i < 10) {
    document.write(i); // 2,4,8,16
    i++;
}
```

<br>
<br>

## 8. break, continue

```javascript
for (var i = 0; i < 10; i++) {
    if (i == 5) {
        break;
    }
    document.write(i); // stops and exits the cycle 0,1,2,3,4
}
```

```javascript
for (var i = 0; i < 10; i++) {
    if (i == 5) {
        continue;
    }
    document.write(i); // skips the rest of the cycle 0,1,2,3,4,5,6,7,8,9
}
```

<br>
<br>

###### 참고자료

* <a href="https://htmlcheatsheet.com/js/" target="_blank"> https://htmlcheatsheet.com/js </a>