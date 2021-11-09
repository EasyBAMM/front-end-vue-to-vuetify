<!-- 컴포넌트 UI 정의 -->
<template>
<v-card>
    <v-card-title>Exam07Template</v-card-title>
    <v-card-text>
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="primary"
          dark
          v-bind="attrs"
          v-on="on"
        >
          Open Dialog
        </v-btn>
      </template>
      <v-btn @click="showModalDialogTemplate = true" small class="mr-2 white--text" color="#2196F3">Show ModalDialogTemplate</v-btn>
      <v-btn @click="showDialogA = true" small class="mr-2 white--text" color="#2196F3">Show DialogA</v-btn>
      <v-btn @click="showDialogB = true" small class="mr-2 white--text" color="#2196F3">Show DialogB</v-btn>
    </v-card-text>
    <modal-dialog-template 
    v-if="showModalDialogTemplate"
    :dialog="showModalDialogTemplate"
      @close="showModalDialogTemplate = false"
    />
    <dialog-a v-if="showDialogA" :dialog="showDialogA" @close="showDialogA = false" />
    <dialog-b v-if="showDialogB" :dialog="showDialogB" @close="showDialogB = false" />
  </v-card>
</template>

<script>
import ModalDialogTemplate from "@/components/menu02/ModalDialogTemplate.vue";
import DialogA from "./DialogA.vue";
import DialogB from "./DialogB.vue";

export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "Exam07Template",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: { ModalDialogTemplate, DialogA, DialogB },
  // 컴포넌트 데이터 정의
  data() {
    return {
      showModalDialogTemplate: false,
      showDialogA: false,
      showDialogB: false,
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