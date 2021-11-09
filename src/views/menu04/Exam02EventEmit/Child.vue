<!-- 컴포넌트 UI 정의 -->
<template>
  <v-card>
    <v-card-title>Child</v-card-title>
    <v-card-text>
      <h6>[자식 -> 부모]</h6>
      <v-btn @click="handleBtn1()" small class="mr-2 white--text" color="#2196F3"
        >child-event-1 emit</v-btn
      >
      <v-btn @click="handleBtn2()" small class="mr-2 white--text" color="#2196F3"
        >child-event-2 emit</v-btn
      >
      <v-divider class="mt-2 mb-2"/>
      <h6>[부모 -> 자식 -> 부모 -> 자식]</h6>
      <p class="mb-2">부모로 부터 받은 counter: {{ counter }}</p>
      <v-btn @click="handleBtn3()" small class="mr-2 white--text" color="#2196F3"
        >counter 증가요청(자식->부모)</v-btn
      >
      <v-btn @click="handleBtn4()" small class="mr-2 white--text" color="#2196F3"
        >counter 감소요청(자식->부모)</v-btn
      >
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
    return {
      data1: "child-value1",
      data2: 100,
    };
  },
  // 컴포넌트 메소드 정의
  methods: {
    handleBtn1() {
      // 이벤트 발생
      this.$emit("child-event-1", this.data1);
    },
    handleBtn2() {
      // 이벤트 발생
      this.$emit("child-event-2", this.data1, this.data2);
    },
    handleBtn3() {
      // 이벤트 발생
      this.$emit("counter-increment", 10);
    },
    handleBtn4() {
      // 이벤트 발생
      this.$emit("counter-decreasement", 10);
    },
  },
  props: ["counter"],
};
</script>

<!-- 컴포넌트 스타일 정의 -->
<style scoped>
/* scoped: 전역 범위X, 컴포넌트 범위 */
</style>