# 스크립트의 로딩

일반적으로 브라우저는 html을 파싱하다가 <script> 태그를 만나면 <br>
DOM 생성을 멈추고 스크립트의 다운로드와 실행이 끝난 뒤 DOM 생성을 재개 합니다. <br><br>

이는 DOM 생성 중 하얀 화면만 보이다가 컨텐츠 갑자기 보이게 되는 현상이 발생합니다. <br>
따라서 <script> 태그를 문서의 가장 하단에 위치하는 방법을 쓰기도 합니다. <br>
하지만 위 방법은 문서가 커질 경우 비슷한 문제가 발생합니다. <br><br>

이런 문제 때문에 defer와 async 속성을 사용합니다.

<br>
<br>

## defer

```javascript
<script type="text/javascript" defer src="example.js">
```

DOM 생성과 스크립트의 다운로드는 동시에 진행되지만 스크립트의 실행은
문서 생성이 완료된 후에 이뤄집니다.

<br><br>

## async
```javascript
<script type="text/javascript" async src="example.js">
```

DOM 생성과 스크립트의 다운로드는 동시에 진행되지고, 스크립트의 실행은 <br>
다운로드가 완료된 후 바로 실행됩니다. 이 때 DOM 생성은 멈춥니다.<br><br>

여러개의 스크립트 파일에 async가 선언되어 있을 경우, 스크립트의 실행은 제각각 실행됩니다.

<br><br>

## 스크립트 로딩의 비교

![20150405111905execution2](https://user-images.githubusercontent.com/7742074/117677038-10115600-b1e9-11eb-917c-404a228bb429.jpg)

결과적으로 먼저 로드가 되어야 하는 스크립트는 async로, <br>
DOM 컨트롤이 필요한 스크립트는 defet로 선언하여 사용합니다.