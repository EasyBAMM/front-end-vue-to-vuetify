<!-- 컴포넌트 UI 정의 -->
<template>
  <v-card>
    <v-card-title>Exam01EventHandling</v-card-title>
    <v-card-text>
      <div>
        <h6>Event Handler</h6>
        <v-btn v-on:click="handleBtn1" name="btn1" small class="mr-2 white--text" color="#2196F3"
          >버튼1</v-btn
        >
        <v-btn
          @click="handleBtn2('vue is good', $event)"
          name="btn2"
          small
          class="mr-2 white--text"
          color="#2196F3"
          >버튼2</v-btn
        >
        <v-btn
          @click="handleBtn2('vue is good', $event)"
          name="btn3"
          small
          class="mr-2 white--text"
          color="#2196F3"
          >버튼3</v-btn
        >
        <v-divider class="mt-2 mb-2" />
        <a href="/" @click.prevent="handleLink">링크1</a>
        <v-divider class="mt-2 mb-2" />

        <v-form v-on:submit.prevent="handleSubmit" ref="form" class="d-flex align-center">
          <input type="submit" value="인풋제출" small class="mr-2 white--text blue" />
          <v-btn @click="changeData()" small class="mr-2 white--text" color="#2196F3"
            >버튼제출</v-btn
          >
          <input type="image" :src="require(`@/assets/logo.png`)" alt="" height="38px" />
        </v-form>
      </div>
    </v-card-text>
    <v-divider />
    <v-card-actions>
      <v-btn @click.ctrl="handleBtn3()" small class="mr-2 white--text" color="#2196F3">변경</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "Exam01EventHandling",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: {},
  // 컴포넌트 데이터 정의
  data() {
    return {};
  },
  // 컴포넌트 메소드 정의
  methods: {
    handleBtn1() {
      console.log("handleBtn1() 실행");
    },
    handleBtn2(arg, event) {
      console.log("arg: ", arg);
      console.log("event: ", event);
      if (event.target.name === "btn2") {
        console.log("btn2가 클릭됨");
      } else if (event.target.name === "btn3") {
        console.log("btn3이 클릭됨");
      }
    },
    handleLink() {
      console.log("링크 클릭됨");
    },
    handleSubmit() {
      console.log("Ajax 통신으로 폼 데이터 전송");
    },
    handleBtn3() {
      console.log("handleBtn3() 실행");
    },
  },
};
</script>

<!-- 컴포넌트 스타일 정의 -->
<style scoped>
/* scoped: 전역 범위X, 컴포넌트 범위 */
</style>