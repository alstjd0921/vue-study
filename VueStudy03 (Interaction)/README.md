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

아래는 [vote counter.html](<https://github.com/alstjd0921/vue-study/blob/master/VueStudy03%20(Interaction)/vote%20counter/vote%20counter.html>) 코드의 일부이다.

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

그리고 그냥 그 메서드에 클릭 이벤트 리스너를 바인딩했더니 앞의 경우와 동일하게 동작하는것을 확인할 수 있었다.

```html
<button v-on:click="upvote" class="btn btn-default">
  Upvote! {{ upvotes }}
</button>
```

## 이벤트 수식어

아래는 [calculator.html](<https://github.com/alstjd0921/vue-study/blob/master/VueStudy03%20(Interaction)/Calculator/calculator.html>)의 일부이다.

```html
<button type="submit" v-on:click.prevent="calculate" class="btn btn-primary">
  Calculate
</button>
```

v-on뒤에 붙은 **.prevent**가 이벤트 수식어이며 onsubmit 이벤트의 기본 동작을 취소하는 역할을 해준다.  
이를 제거하고 버튼을 누르면 계산을 수행하는 대신 폼을 제출하고 페이지가 다시 로드되기만 할 것이다.

Vue에서는 이벤트에 대한 기본 동작을 방지하기 위해 v-on에 대해 6가지 이벤트 수식어를 제공한다. 수식어는 점으로 표시된 접미사이다.

- .stop
- .prevent
- .capture
- .self
- .once
- .passive

## 키 수식어

폼에 버튼이 없거나 버튼이 전혀 없어야 경우에는 키보드 이벤트를 감지하는 방법도 있다.

키보드 이벤트를 감지해야하면 필연적으로 키 코드를 자주 확인하게 될 것이다.  
예를 들어 엔터의 키 코드는 13이다. 엔터를 감지하기 위해선 아래와 같이 작성해야 할 것이다.

```html
<input v-model="a" v-on:keyup.13="calculate" />
```

아스키코드 전부 외우고 다니는 사람 흔치 않듯이 키 코드를 전부 외우고 다니는 변태는 많지 않을 것이다. Vue는 일반적으로 많이 사용하는 키의 별칭을 제공한다.

- enter
- tab
- delete
- esc
- space
- up
- down
- left
- right

## computed 속성

Vue의 인라인 표현식은 편리하지만 로직이 복잡해지면 코드를 읽기 힘들어질 것이다. 이때 computed 속성을 사용하여 해결할 수 있다.

computed 속성이란 다른 요인에 따라 값이 바뀌는 변수로, 객체 속성으로 사용할 수 있는 함수처럼 작동한다.  
단, computed 속성은 의존하는 요소가 변경될 때마다 값이 다시 평가되는 차이점이 있다.

Vue에서는 Vue 인스턴스 안의 computed 객체에 computed 속성을 정의한다.

아래는 [computed.html](<https://github.com/alstjd0921/vue-study/blob/master/VueStudy03%20(Interaction)/computed%20property/computed.html>)의 일부이다.

```javascript
new Vue({
  el: "#app",
  data: {
    a: 1,
    b: 1,
    operator: "+"
  },
  computed: {
    c: function() {
      switch (this.operator) {
        case "+":
          return (this.c = this.a + this.b);
          break;
        case "-":
          return (this.c = this.a - this.b);
          break;
        case "*":
          return (this.c = this.a * this.b);
          break;
        case "/":
          return (this.c = this.a / this.b);
          break;
      }
    }
  }
});
```

[calculator.html](<https://github.com/alstjd0921/vue-study/blob/master/VueStudy03%20(Interaction)/Calculator/calculator.html>)에서 메서드 안에 있는 것들을 computed 속성 c로 옮기는 작업과 버튼을 제거하는 작업밖에 하지 않았다.

의존하는 요소가 변경될 때마다 값이 다시 평가되는 특징 덕분에 버튼이나 이벤트, 그 어떤 것도 필요하지 않다.
