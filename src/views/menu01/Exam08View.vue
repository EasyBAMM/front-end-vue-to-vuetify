<!-- 컴포넌트 UI 정의 -->
<template>
  <v-card>
    <v-card-title>Exam08View</v-card-title>
    <v-card-text>
      <div>kind: {{ $route.query.kind }}</div>
      <div>color: {{ $route.query.color }}</div>
      <div>kind: {{ kind }}</div>
      <div>color: {{ color }}</div>
    </v-card-text>
    <v-divider />
    <v-card-actions>
      <v-btn @click="goHome()" small class="mr-2 white--text" color="#2196F3">홈으로 이동</v-btn>
      <v-btn @click="goBack()" small class="mr-2 white--text" color="#2196F3">뒤로 이동</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "Exam08View",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: {},
  // 컴포넌트 데이터 정의
  data: function () {
    return {};
  },
  // 컴포넌트 메소드 정의
  methods: {
    goHome() {
      this.$router.push("/");
    },
    goBack() {
      this.$router.go(-1);
    },
  },
  // 컴포넌트가 생성된 후 실행되는 메소드
  created() {
    console.log(this.$route);
  },
  props: ["kind", "color"],
};
</script>

<!-- 컴포넌트 스타일 정의 -->
<style scoped>
/* scoped: 전역 범위X, 컴포넌트 범위 */
</style>