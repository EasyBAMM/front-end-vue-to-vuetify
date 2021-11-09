<template>
  <v-card>
    <v-card-title>JWT 인증</v-card-title>
    <v-card-text>
      <!-- 로그인 -->
      <div v-if="$store.state.userId === ''">
        <v-text-field label="User ID" v-model="user.id" required></v-text-field>
        <v-text-field label="User Password" v-model="user.password" required></v-text-field>
        <v-btn @click="handleLogin" small class="mr-2 white--text" color="#2196F3">로그인</v-btn>
      </div>
      <div v-if="$store.state.userId !== ''">
        <v-btn @click="handleLogout" small class="mr-2 white--text" color="#2196F3">로그아웃</v-btn>
      </div>
    </v-card-text>
    <alert-dialog
      v-if="alertDialog"
      :dialog="alertDialog"
      @close="alertDialog = false"
      :message="alertDialogMessage"
      :loading="loading"
    />
  </v-card>
</template>

<script>
import auth from "@/apis/auth";
import AlertDialog from '@/components/menu07/AlertDialog.vue';
export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "LoginForm",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: { AlertDialog },
  // 컴포넌트 데이터 정의
  data() {
    return {
      user: {
        id: "user",
        password: "12345",
      },
      alertDialog: false,
      alertDialogMessage: "",
      loading: false,
    };
  },
  // 컴포넌트 메소드 정의
  methods: {
    async handleLogin() {
      try {
        this.loading = true;
        this.alertDialog = true;
        const response = await auth.login(this.user);
        this.loading = false;
        if (response.data.result === "success") {
          this.alertDialogMessage = "로그인 성공";
        }
        this.$store.dispatch("saveAuth", {
          userId: response.data.mid,
          authToken: response.data.jwt,
        });
      } catch (error) {
        this.alertDialog = true;
        if (error.response && error.response.status === 401) {
          this.alertDialogMessage = "로그인 실패(아이디 또는 비밀번호가 틀렸습니다).";
        } else {
          this.alertDialogMessage = "로그인 실패(네트워크 에러)";
        }
      } finally {
        this.loading = false;
      }
    },
    handleLogout() {
      this.$store.dispatch("deleteAuth");
    },
  },
};
</script>