<!-- 컴포넌트 UI 정의 -->
<template>
<v-card>
    <v-card-title>Child</v-card-title>
    <v-card-text>
      <p>userId 단방향 바인딩: {{ $store.state.userId }}</p>
      <p>userId 단방향 바인딩: {{ $store.getters.getUserId }}</p>
      <v-text-field v-model="$store.state.userId" label="userId 양방향 바인딩"></v-text-field>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "Child",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: {},
  // 컴포넌트 데이터 정의
  data() {
    return {};
  },
  // 컴포넌트 메소드 정의
  methods: {},
  computed: {
    computedUserId() {
      //   return this.$store.state.userId;
      //   return this.$store.getters.getUserId;
      return this.$store.getters["getUserId"];
    },
  },
};
</script>

<!-- 컴포넌트 스타일 정의 -->
<style scoped>
/* scoped: 전역 범위X, 컴포넌트 범위 */
</style>