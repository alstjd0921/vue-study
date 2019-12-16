# Interaction

## 이벤트 처리

HTMl 이벤트는 DOM 엘리먼트에서 일어나며 Vue는 이러한 이벤트에 반응한다.

다음은 HTML 이벤트의 몇 가지 예시이다.

- 웹 페이지가 완전히 로드됨
- 입력 폼의 수정
- 버튼 클릭
- 폼 제출

이벤트 처리는 말 그대로 위와 같은 이벤트가 발생할 때 어떤 동작을 하도록 만드는 것이다.

Vue에선 이벤트를 감지할 때 v-on 디렉티브를 사용한다. 이벤트 유형은 인자로 표시하며, 예를 들어 'v-on:click'은 마우스 클릭을 감지한다.

### 인라인 이벤트 핸들링

아래는 vote counter.html 코드의 일부이다.

```html
<button v-on:click="upvotes++" class="btn btn-default">
  Upvote! {{ upvotes }}
</button>
```

데이터에 upvotes 변수가 선언되어있는 상태다. click에 대한 이벤트 리스너를 바인딩하고 upvotes++라는 명령문을 작성했으며 버튼을 누를때마다 upvote에 +1이 되는 것을 확인할 수 있었다.

### 메서드를 이용한 이벤트 처리

앞에서는 인라인으로 이벤트를 처리했지만 vote counter.html을 약간 수정하여 이번에는 메서드를 이용해 이벤트를 처리해볼 것이다.

우선 아래와 같이 methods 객체 안에 upvote라는 메서드를 정의했다.

````javascript
methods: { upvote: function() { this.upvotes++; } } ```
````

그리고 그냥 그 메서드에 클릭 이벤트 리스너를 바인딩했더니 앞의 것과 동일하게 동작하는것을 확인할 수 있었다.

```html
<button v-on:click="upvote" class="btn btn-default">
  Upvote! {{ upvotes }}
</button>
```
