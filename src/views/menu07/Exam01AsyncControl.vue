<!-- 컴포넌트 UI 정의 -->
<template>
  <v-card>
    <v-card-title>Exam01AsyncControl</v-card-title>
    <v-card-text>
      <div>
        <v-btn @click="handleBtn1" small class="mr-2 white--text" color="#2196F3"
          >비동기 작업1</v-btn
        >
        <v-btn @click="handleBtn2" small class="mr-2 white--text" color="#2196F3"
          >비동기 작업1</v-btn
        >
      </div>
      <div v-if="loading" class="mt-3">
        <v-progress-circular indeterminate color="primary"></v-progress-circular>
      </div>
      <div v-if="!loading" class="mt-3">처리결과: {{ result }}</div>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "Exam01AsyncControl",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: {},
  // 컴포넌트 데이터 정의
  data() {
    return {
      loading: false,
      result: "",
    };
  },
  // 컴포넌트 메소드 정의
  methods: {
    work() {
      const promise = new Promise((resolve, reject) => {
        setTimeout(() => {
          resolve("점심 먹으러 갑시다.");
        }, 3000);
      });
      return promise;
    },
    handleBtn1() {
      this.loading = true;
      this.work()
        .then((result) => {
          this.result = result;
        })
        .catch((error) => {})
        .finally(() => {
          this.loading = false;
        });
    },
    async handleBtn2() {
      this.loading = true;
      try {
        const result = await this.work();
        this.result = result;
      } catch (error) {
        //
      } finally {
        this.loading = false;
      }
    },
  },
};
</script>

<!-- 컴포넌트 스타일 정의 -->
<style scoped>
/* scoped: 전역 범위X, 컴포넌트 범위 */
</style>