<!-- 컴포넌트 UI 정의 -->
<template>
  <modal-dialog-template :dialog="dialog">
    <template v-slot:header> 로그인 </template>
    <template v-slot:body>
      <v-form v-on:submit.prevent="handleSubmit" ref="form" v-model="valid" lazy-validation>
        <v-text-field label="Email address" required></v-text-field>
        <v-text-field label="Password" required></v-text-field>
        <v-checkbox label="Check me out" value="Check me out"></v-checkbox>
      </v-form>
    </template>
    <template v-slot:footer>
      <v-btn @click="$emit('close')" small class="mr-2 white--text" color="#2196F3">로그인 </v-btn>
      <v-btn @click="$emit('close')" small class="mr-2 white--text" color="#2196F3">취소</v-btn>
    </template>
  </modal-dialog-template>
</template>

<script>
import ModalDialogTemplate from "@/components/menu02/ModalDialogTemplate.vue";
export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "DialogB",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: { ModalDialogTemplate },
  // 컴포넌트 데이터 정의
  data() {
    return {};
  },
  // 컴포넌트 메소드 정의
  methods: {},
  props: ["dialog"],
};
</script>

<!-- 컴포넌트 스타일 정의 -->
<style scoped>
/* scoped: 전역 범위X, 컴포넌트 범위 */
</style>