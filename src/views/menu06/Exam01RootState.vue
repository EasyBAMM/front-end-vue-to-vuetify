<!-- 컴포넌트 UI 정의 -->
<template>
  <v-card>
    <v-card-title>Exam01RootState</v-card-title>
    <v-card-text>
      <h6>[Root State 읽기]</h6>
      <p>userId 단방향 바인딩: {{ $store.state.userId }}</p>
      <p>userId 단방향 바인딩: {{ $store.getters.getUserId }}</p>
      <p>userId 단방향 바인딩: {{ getUserId() }}</p>
      <p>userId 단방향 바인딩: {{ computedUserId }}</p>
      <v-text-field v-model="$store.state.userId" label="userId 양방향 바인딩"></v-text-field>
      <v-divider class="mt-2 mb-2" />
      <h6>[Root State 변경]</h6>
      <v-text-field v-model="userId" label="Component userId 양방향 바인딩"></v-text-field>
      <div class="mt-2">
        <v-btn @click="changeUserIdByMutation" small class="mr-2 white--text" color="#2196F3"
          >userId 변경(Mutation 동기 방식)</v-btn
        >
        <v-btn @click="changeUserIdByAction" small class="mr-2 white--text" color="#2196F3"
          >userId 변경(Action 비동기 방식)</v-btn
        >
      </div>
      <child class="mt-2" />
    </v-card-text>
  </v-card>
</template>

<script>
import Child from "./Child.vue";
export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "Exam01RootState",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: { Child },
  // 컴포넌트 데이터 정의
  data() {
    return {
      userId: "",
    };
  },
  // 컴포넌트 메소드 정의
  methods: {
    getUserId() {
      //   return this.$store.state.userId;
      //   return this.$store.getters.getUserId;
      return this.$store.getters["getUserId"];
    },
    changeUserIdByMutation() {
      this.$store.commit("setUserId", this.userId);
    },
    changeUserIdByAction() {
      this.$store.dispatch("setUserIdByAsync", { userId: this.userId, duration: 3000 });
    },
  },
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