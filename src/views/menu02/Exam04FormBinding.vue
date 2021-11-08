<!-- 컴포넌트 UI 정의 -->
<template>
  <v-card>
    <v-card-title>Exam04FormBinding</v-card-title>
    <v-card-text>
      <v-form v-on:submit.prevent="handleSubmit" ref="form" v-model="valid" lazy-validation>
        <v-text-field
          v-model="product.name"
          label="Name"
          required
        ></v-text-field>
        <v-text-field
          v-model="product.company"
          label="Company"
          required
        ></v-text-field>
        <v-text-field
          v-model.number="product.price"
          label="Price"
        ></v-text-field>
        <v-textarea solo v-model="product.info" label="Info"></v-textarea>
        <v-select
          v-model="product.madein"
          :items="product.items"
          label="Select"
          required
        ></v-select>
        <v-checkbox v-model="product.colors" label="black" value="black"></v-checkbox>
        <v-checkbox v-model="product.colors" label="white" value="white"></v-checkbox>
        <v-checkbox v-model="product.colors" label="red" value="red"></v-checkbox>
        <v-checkbox v-model="product.sale1" label="판매여부" value="sale1"></v-checkbox>
        <v-checkbox v-model="product.sale2" label="판매여부" value="red"></v-checkbox>
        <v-radio-group v-model="product.sex">
          <v-radio label="Man" value="man" />
          <v-radio label="Woman" value="woman" />
        </v-radio-group>
        <v-btn v-bind:disabled="disabledRegButton" small class="mr-2 white--text" color="#2196F3">
          등록
        </v-btn>
        <v-btn to="/" small class="mr-2 white--text" color="#2196F3">취소</v-btn>
      </v-form>
    </v-card-text>
    <v-divider />
  </v-card>
</template>

<script>
export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "Exam04FormBinding",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: {},
  // 컴포넌트 데이터 정의
  data() {
    return {
      product: {
        name: "홍길동",
        company: "",
        price: 0,
        colors: [],
        info: "",
        madein: "한국",
        sale1: false,
        sale2: "no",
        sex: "woman",
        items: ["미국", "한국", "독일"],
      },
    };
  },
  // 컴포넌트 메소드 정의
  methods: {
    handleSubmit() {
      console.log(this.product);
    },
  },
  // 데이터가 변경되면 자동 계산되는 속성
  computed: {
    disabledRegButton() {
      var result = this.product.name === "" || this.product.company === "";
      return result;
    },
  },
};
</script>

<!-- 컴포넌트 스타일 정의 -->
<style scoped>
/* scoped: 전역 범위X, 컴포넌트 범위 */
</style>