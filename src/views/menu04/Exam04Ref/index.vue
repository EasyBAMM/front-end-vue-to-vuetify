<!-- 컴포넌트 UI 정의 -->
<template>
  <v-card>
    <v-card-title>Exam04Ref</v-card-title>
    <v-card-text>
      <p>data: {{ data }}</p>
      <v-divider class="mt-2 mb-2" />
      <v-btn @click="handleChildData" small class="mr-2 white--text" color="#2196F3"
        >자식 데이터 읽기</v-btn
      >
      <v-btn @click="handleChildMethod" small class="mr-2 white--text" color="#2196F3"
        >자식 메소드 호출</v-btn
      >
      <v-divider class="mt-2 mb-2" />
      <child ref="childRef" />
      <v-divider class="mt-2 mb-2" />

      <v-text-field ref="inputRef" v-model="inputData"></v-text-field>
      <v-btn @click="handleInputFocus" small class="mr-2 white--text" color="#2196F3"
        >요소 포커스 주기</v-btn
      >
      <v-btn @click="handleInputValue" small class="mr-2 white--text" color="#2196F3"
        >요소의 값 변경</v-btn
      >
    </v-card-text>
  </v-card>
</template>

<script>
import Child from "./Child.vue";
export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "Exam04Ref",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: { Child },
  // 컴포넌트 데이터 정의
  data() {
    return {
      data: "parent-data",
      inputData: ""
    };
  },
  // 컴포넌트 메소드 정의
  methods: {
    parentMethod() {
      console.log("parentMethod() 실행");
    },
    handleChildData() {
      console.log(this.$refs.childRef.data);
    },
    handleChildMethod() {
      this.$refs.childRef.childMethod();
    },
    handleInputFocus() {
      this.$refs.inputRef.focus();
    },
    handleInputValue() {
      // this.$refs.inputRef.value += "a";
      this.inputData += "a";
    },
  },
};
</script>

<!-- 컴포넌트 스타일 정의 -->
<style scoped>
/* scoped: 전역 범위X, 컴포넌트 범위 */
</style>