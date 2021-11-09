<!-- 컴포넌트 UI 정의 -->
<template>
  <v-card>
    <v-card-title>Exam01LifeCycleHook</v-card-title>
    <v-card-text>
      <p>data: {{ data }}</p>
      <v-btn @click="changeData()" small class="mr-2 white--text" color="#2196F3">변경</v-btn>
      <v-divider class="mt-2 mb-2" />
      <child :data="data" />
    </v-card-text>
  </v-card>
</template>

<script>
import Child from "./Child.vue";

export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "Exam01LifeCycleHook",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: { Child },
  // 컴포넌트 데이터 정의
  data() {
    return {
      data: "",
    };
  },
  // 컴포넌트 메소드 정의
  methods: {
    changeData() {
      this.data += Math.floor(10 * Math.random());
    },
  },
  // LifeCycleHook 정의
  beforeCreate() {
    console.log("beforeCreate state");
  },
  created() {
    console.log("created state");
  },
  beforeMount() {
    console.log("beforeMount state");
  },
  mounted() {
    console.log("mounted state");
  },
  beforeUpdate() {
    console.log("beforeUpdate state");
  },
  updated() {
    console.log("updated state");
  },
  beforeDestroy() {
    console.log("beforeDestroy state");
  },
  destroyed() {
    console.log("destroyed state");
  },
};
</script>

<!-- 컴포넌트 스타일 정의 -->
<style scoped>
/* scoped: 전역 범위X, 컴포넌트 범위 */
</style>