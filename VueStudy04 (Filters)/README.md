# Filters

## 필터링된 결과 출력

데이터를 변경하지 않고 필터링된 배열을 출력해야하는 경우가 있다.  
이 경우 배열을 걸러내어 렌더링된 결과를 반환하는 메서드를 만들어 해결이 가능하다.

아래는 filter.html의 일부

```javascript
methods: {
    check: function(show) {
        return this.table.filter(function(array) {
            return array.show === show;
        });
    }
}
```

## computed property 사용

computed property로도 배열을 필터링할 수 있다.

아래는 filter(computed).html의 일부

```javascript
computed: {
    check: function() {
        return this.table.filter(function(array) {
            return array.cnt > 25;
        });
    }
}
```

### 간단한 검색 구현

변수에 바인딩된 input을 추가하여 배열을 동적으로 필터링할 수 있다.  
이를 이용해 간단한 검색 기능을 구현해볼 수 있다.

아래는 search.html의 일부

```javascript
search: function() {
  let query = this.query;
    return this.table.filter(function(el) {
      return el.string.includes(query);
    });
}
```
