<!-- 컴포넌트 UI 정의 -->
<template>
  <v-card>
    <v-card-title>Exam01Props</v-card-title>
    <v-card-text>
      <child-a
        :prop1="data1"
        :prop2="data2"
        :productNo="pno"
        :productKind="pkind"
        :productPrice="1000"
      />
      <v-divider />
      <child-b :product="product" v-bind="product" />
      <v-divider />
      <child-c
        :propA="3"
        :propB="5"
        :propC="7"
        :propD="'string-data'"
        :propE="9"
        :propF="{ message: 'hello vue' }"
        :propG="['red', 'green', 'blue']"
        :propI="5"
      />
    </v-card-text>
  </v-card>
</template>

<script>
import ChildA from "./ChildA.vue";
import ChildB from "./ChildB.vue";
import ChildC from "./ChildC.vue";
export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "Exam01Props",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: { ChildA, ChildB, ChildC },
  // 컴포넌트 데이터 정의
  data() {
    return {
      data1: "value1",
      data2: "value2",
      pno: "1",
      pkind: "bag",
      pprice: 1000,
      product: {
        no: 2,
        kind: "정장",
      },
    };
  },
  // 컴포넌트 메소드 정의
  methods: {},
};
</script>

<!-- 컴포넌트 스타일 정의 -->
<style scoped>
/* scoped: 전역 범위X, 컴포넌트 범위 */
</style>