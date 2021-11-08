<!-- 컴포넌트 UI 정의 -->
<template>
  <v-card>
    <v-card-title>Ex03View</v-card-title>
    <v-card-text>
      <div>
        <h6>선언적 방식 화면 이동</h6>
        <v-btn small class="mr-2 white--text" color="#2196F3" to="/menu01/exam03view/subacoponent"
          >SubACoponent</v-btn
        >
        <v-btn small class="mr-2 white--text" color="#2196F3" to="/menu01/exam03view/subbcoponent"
          >SubBCoponent</v-btn
        >
        <h6 class="mt-2">프로그래밍 방식 화면 이동</h6>
        <v-btn small class="mr-2 white--text" color="#2196F3" @click="goUrl('a')"
          >SubAComponent</v-btn
        >
        <v-btn small class="mr-2 white--text" color="#2196F3" @click="goUrl('b')"
          >SubBComponent</v-btn
        >
      </div>
    </v-card-text>

    <div class="mt-2">
      <router-view></router-view>
    </div>
  </v-card>
</template>

<script>
export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "Exam03View",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: {},
  // 컴포넌트 데이터 정의
  data: function () {
    return {};
  },
  // 컴포넌트 메소드 정의
  methods: {
    goUrl(kind) {
      this.$router.push(`/menu01/exam03view/sub${kind}coponent`).catch(() => {});
    },
  },
};
</script>

<!-- 컴포넌트 스타일 정의 -->
<style scoped>
/* scoped: 전역 범위X, 컴포넌트 범위 */
</style>
