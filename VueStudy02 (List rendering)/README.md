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

아래는 [v-for array traversal.html](<https://github.com/alstjd0921/vue-study/blob/master/VueStudy02%20(List%20rendering)/v-for%20array%20traversal/v-for%20array%20traversal.html>) 코드의 일부이다. 'item in array' 형태의 구문을 확인할 수 있을 것이다.

```html
<ul class="list-group">
  <li class="list-group-item" v-for="story in stories">
    Someone said "{{ story }}"
  </li>
</ul>
```

#### 객체 배열 순회

아래는 [v-for object array traversal.html](<https://github.com/alstjd0921/vue-study/blob/master/VueStudy02%20(List%20rendering)/v-for%20array%20traversal/v-for%20object%20array%20traversal.html>) 코드의 일부이다. 일반 배열 순회할 때와 크게 다른점은 없다.

```html
<ul class="list-group">
  <li class="list-group-item" v-for="story in stories">
    {{ story.writer }} said "{{ story.plot }}"
  </li>
</ul>
```

### 객체 프로퍼티 순회

객체의 프로퍼티를 순회할 때도 v-for을 사용할 수 있다. 아래는 [v-for property traversal.html](https://github.com/alstjd0921/vue-study/blob/master/VueStudy02%20(List%20rendering)/v-for%20property%20traversal/v-for%20property%20traversal.html) 코드의 일부이다.

```html
<ul class="list-group">
  <li class="list-group-item" v-for="(value, key, index) in story">
    {{index}} : {{key}} : {{ value }}
  </li>
</ul>
```

value는 물론이고 key와 index도 각각 두 번째와 세 번째 인자로 지정할 수 있다.
