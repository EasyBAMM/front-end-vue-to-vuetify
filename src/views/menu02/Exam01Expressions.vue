<!-- 컴포넌트 UI 정의 -->
<template>
  <v-card>
    <v-card-title>Exam01Expressions</v-card-title>
    <v-card-text>
      <h5>상품정보</h5>
      <p>번호: {{ no }}</p>
      <p>이름: {{ name }}</p>
      <p>회사: {{ company }}</p>
      <p>가격: {{ price }}</p>
      <p>가격: {{ getPrice() }}</p>
      <p>판매여부: {{ sale ? "판매" : "품절" }}</p>
    </v-card-text>
    <v-divider />
    <v-card-actions>
      <v-btn @click="changeData()" small class="mr-2 white--text" color="#2196F3">변경</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "Exam01Expressions",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: {},
  // 컴포넌트 데이터 정의
  data: function () {
    return {
      no: 1,
      name: "미니백",
      company: "클레인",
      price: 300000,
      sale: true,
    };
  },
  // 컴포넌트 메소드 정의
  methods: {
    getPrice() {
      return this.price;
    },
    changeData() {
      this.price += 1000;
      this.sale = !this.sale;
    },
  },
};
</script>

<!-- 컴포넌트 스타일 정의 -->
<style scoped>
/* scoped: 전역 범위X, 컴포넌트 범위 */
</style>