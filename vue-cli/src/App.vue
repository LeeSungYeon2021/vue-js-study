<template>
  <div>
    <!-- 최 상단의 하나의 노드만 있어야 함. -->
      <!-- <app-header v-bind:프롭스 속성 이름="상위 컴포넌트의 데이터 이름"></app-header> -->
      <app-header 
        v-bind:propsdata="str"
        v-on:renew="renewStr"></app-header>
  </div>
</template>

<script>

// AppHeader 컴포넌트 불러오기
import AppHeader from './components/AppHeader.vue';

// new Vue({
//   data: {
//     str: 'hi'
//   }
// })
export default {
  data: function() {
    return {
      str: 'Header'
    }
  }, 
  // 기존엔 template 태그를 사용하여 태그 생성했으나,
  // 폴더에서 생성 후 import하여 사용
  components: {
    'app-header': AppHeader
  },
  methods: {
    renewStr : function() {
      this.str = 'event test'
    }
  }
}
</script>

<style>

</style>