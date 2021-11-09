<template>
  <v-card>
    <v-card-title>JWT 인증</v-card-title>
    <v-card-text>
      <!-- 회원가입 -->
      <v-text-field label="User ID" v-model="user.id" required></v-text-field>
      <v-text-field label="User Name" v-model="user.name" required></v-text-field>
      <v-text-field label="User Password" v-model="user.password" required></v-text-field>
      <v-select
        v-model="user.role"
        :items="user.items"
        label="User Role"
        name="mrole"
        required
      ></v-select>
      <v-text-field label="User Email" v-model="user.email" required></v-text-field>
      <v-btn @click="handleJoin" small class="mr-2 white--text" color="#2196F3">가입</v-btn>
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
  name: "JoinForm",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: {AlertDialog},
  // 컴포넌트 데이터 정의
  data() {
    return {
      user: {
        id: "user",
        name: "사용자",
        password: "12345",
        role: "ROLE_USER",
        items: ["ROLE_ADMIN", "ROLE_MANAGER", "ROLE_USER"],
        email: "user@mycompany.com",
      },
      alertDialog: false,
      alertDialogMessage: "",
      loading: false,
    };
  },
  // 컴포넌트 메소드 정의
  methods: {
    async handleJoin() {
      try {
        this.loading = true;
        this.alertDialog = true;

        const response = await auth.join(this.user);
        this.loading = false;
        if (response.data.result === "success") {
          this.alertDialogMessage = "회원 가입 성공";
        } else if (response.data.result === "duplicated") {
          throw { message: "중복된 아이디" };
        } else if (response.data.result === "fail") {
          throw { message: "서버측 오류발생" };
        }
      } catch (error) {
        this.loading = false;
        this.alertDialogMessage = `회원 가입 실패: ${error.message}`;
      }
    },
  },
};
</script>