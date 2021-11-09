<!-- 컴포넌트 UI 정의 -->
<template>
  <modal-dialog-template :dialog="dialog">
    <template v-slot:header>알림</template>
    <template v-slot:body>
      <div v-if="loading" class="mt-3">
        <v-progress-circular indeterminate color="primary"></v-progress-circular>
      </div>
      <div v-if="!loading">{{ message }}</div>
    </template>
    <template v-slot:footer>
      <v-btn color="green darken-1" text @click="$emit('close')"> 닫기 </v-btn>
    </template>
  </modal-dialog-template>
</template>

<script>
import ModalDialogTemplate from "../menu02/ModalDialogTemplate.vue";

export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "AlertDialog",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: { ModalDialogTemplate },
  // 컴포넌트 데이터 정의
  data() {
    return {};
  },
  // 컴포넌트 메소드 정의
  methods: {},
  props: ["dialog", "message", "loading"],
};
</script>

<!-- 컴포넌트 스타일 정의 -->
<style scoped>
/* scoped: 전역 범위X, 컴포넌트 범위 */
</style>