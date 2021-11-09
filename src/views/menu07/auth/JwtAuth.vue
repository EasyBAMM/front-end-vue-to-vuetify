<!-- 컴포넌트 UI 정의 -->
<template>
  <v-card>
    <v-card-title>JwtAuth</v-card-title>
    <v-card-text>
      <!-- 로그인 -->
      <login-form />

      <v-divider light class="mt-4 mb-4" />

      <!-- 회원가입 -->
      <join-form/>

    </v-card-text>
  </v-card>
</template>

<script>
import LoginForm from "./LoginForm.vue";
import JoinForm from './JoinForm.vue';

export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "JwtAuth",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: { LoginForm, JoinForm },
  // 컴포넌트 데이터 정의
  data() {
    return {
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