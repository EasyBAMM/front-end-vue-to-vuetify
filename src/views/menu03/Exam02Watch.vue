<!-- 컴포넌트 UI 정의 -->
<template>
<v-card>
    <v-card-title>Exam02Watch</v-card-title>
    <v-card-text>
      <v-form v-on:submit.prevent="handleSubmit" ref="form" v-model="valid" lazy-validation>
        <v-text-field
          v-model="userId"
          label="UserId"
          required
        ></v-text-field>
        <v-text-field
          v-model="product.name"
          label="Name"
          required
        ></v-text-field>
        <v-text-field
          v-model="product.company"
          label="Company"
        ></v-text-field>
        <v-text-field
          v-model.number="product.price"
          :background-color="`${bgColor}`"
          label="Price"
        ></v-text-field>
      </v-form>
    </v-card-text>
    <v-divider />
    <v-card-actions>
      <v-btn @click="handleButton()" small class="mr-2 white--text" color="#2196F3">product 객체 변경</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "Exam02Watch",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: {},
  // 컴포넌트 데이터 정의
  data() {
    return {
      userId: "user1",
      product: {
        name: "정장",
        company: "한섬",
        price: 100000,
      },
      bgColor: "",
    };
  },
  // 컴포넌트 메소드 정의
  methods: {
    handleButton() {
      this.product = {
        name: "정장2",
        company: "한섬2",
        price: 200000,
      };
    },
  },
  // 컴포넌트 데이터 감시 정의
  watch: {
    /* 변경데이터 감시 */
    userId(newValue, oldValue) {
      console.log("newValue: ", newValue);
      console.log("oldValue: ", oldValue);
      console.log("this.userId: ", this.userId);
    },
    /* 객체데이터 감시 */
    product: {
      deep: true,
      handler(newValue, oldValue) {
        console.log("newValue: ", newValue);
        console.log("oldValue: ", oldValue);
      },
    },
    "product.name"(newValue, oldValue) {
      console.log("newValue: ", newValue);
      console.log("oldValue: ", oldValue);
      console.log("this.userId: ", this.product.name);
    },
    "product.price"(newValue, oldValue) {
      if (newValue < 0) {
        this.bgColor = "danger";
      } else if (newValue >= 0 && newValue <= 100000) {
        this.bgColor = "success";
      } else {
        this.bgColor = "primary";
      }
    },
  },
};
</script>

<!-- 컴포넌트 스타일 정의 -->
<style scoped>
/* scoped: 전역 범위X, 컴포넌트 범위 */
</style>