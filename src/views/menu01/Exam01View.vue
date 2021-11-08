<!-- 컴포넌트 UI 정의 -->
<template>
  <v-card>
    <v-card-title>Exam01View</v-card-title>
    <v-card-text>선언적 방식 화면 이동</v-card-text>
    <v-card-actions>
      <v-btn small class="mr-2 white--text" color="#2196F3" to="/menu01/exam02view"
        >/menu01/exam02view</v-btn
      >
      <v-btn small class="mr-2 white--text" color="#2196F3" v-bind:to="`/menu01/exam02view`"
        >/menu01/exam02view</v-btn
      >
      <v-btn small class="mr-2 white--text" color="#2196F3" :to="{ path: '/menu01/exam02view' }"
        >/menu01/exam02view</v-btn
      >
      <v-btn small class="mr-2 white--text" color="#2196F3" :to="{ name: 'menu01_exam02view' }"
        >/menu01/exam02view</v-btn
      >
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "Exam01View",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: {},
  // 컴포넌트 데이터 정의
  data: function () {
    return {};
  },
  // 컴포넌트 메소드 정의
  methods: {},
};
</script>

<!-- 컴포넌트 스타일 정의 -->
<style scoped>
/* scoped: 전역 범위X, 컴포넌트 범위 */
</style>