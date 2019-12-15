# List rendering

Vue의 디렉티브를 이용해 다음과 같은 작업을 하는 방법을 알아보았다.

- 배열 기반의 리스트 출력
- 템플릿 반복
- 객체의 프로퍼티를 순회

## v-for

리스트의 순회를 위해 v-for 디렉티브를 사용한다. 이 디렉티브는 'item in array' 형태의 구문을 필요로한다.

### 범위

v-for 디렉티브는 정수를 받는 것이 가능하다. 리스트나 객체 대신 정수가 전달되면 템플릿이 이를 반복한다. (파이썬의 for in range 같은 느낌)

### 배열

#### 배열 순회

아래는 v-for array traversal.html 코드의 일부이다. 'item in array' 형태의 구문을 확인할 수 있을 것이다.

```html
<ul class="list-group">
  <li class="list-group-item" v-for="story in stories">
    Someone said "{{ story }}"
  </li>
</ul>
```

#### 객체 배열 순회

아래는 v-for object array traversal.html 코드의 일부이다. 일반 배열 순회할 때와 같고 순회하는 객체의 속성만 추가해주면 원하는대로 작동한다.

```html
<ul class="list-group">
  <li class="list-group-item" v-for="story in stories">
    {{ story.writer }} said "{{ story.plot }}"
  </li>
</ul>
```
