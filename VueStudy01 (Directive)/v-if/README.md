# v-if

v-show와 v-if를 바꿔도 잘 작동한다.

v-show와의 차이점은 DOM에 유지되느냐 유지되지 않느냐의 차이이다. (v-if가 지정된 엘리먼트가 유지되지 않음)

간혹 여러 엘리먼트를 한 번에 토글해야 하는 경우엔 \<template> 엘리먼트에서 v-if를 사용하면 된다. 이를 래퍼로 사용하는 것이 가능하다. (v-show를 template에 사용하는것은 불가)