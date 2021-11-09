<!-- 컴포넌트 UI 정의 -->
<template>
  <v-app-bar app hide-on-scroll>
    <v-app-bar-nav-icon @click.stop="handleDrawer"></v-app-bar-nav-icon>
    <v-toolbar-title>
      <router-link to="/" class="d-flex flex-row align-center black--text text-decoration-none">
        <div>
          <v-img :src="require('../assets/logo.svg')" contain width="30" height="30" />
        </div>
        <div>Vue to Vuetify</div>
      </router-link>
    </v-toolbar-title>
    <v-spacer></v-spacer>
    <v-btn
      tile
      small
      color="#2196F3"
      class="white--text"
      v-if="$store.state.userId === ''"
      to="/menu07/auth/jwtauth"
    >
      <v-icon left> mdi-login </v-icon>
      로그인
    </v-btn>
    <v-btn
      tile
      small
      color="#2196F3"
      class="white--text"
      v-if="$store.state.userId !== ''"
      @click="handleLogout"
    >
      <v-icon left> mdi-logout </v-icon>
      로그아웃
    </v-btn>
  </v-app-bar>
</template>

<script>
export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "AppHeader",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: {},
  // 컴포넌트 데이터 정의
  data() {
    return {};
  },
  // 컴포넌트 메소드 정의
  methods: {
    handleDrawer() {
      // 이벤트 발생
      this.$emit("drawer-event");
    },
    handleLogout() {
      this.$store.dispatch("deleteAuth");
    },
  },
  props: ["drawer"],
};
</script>

<!-- 컴포넌트 스타일 정의 -->
<style scoped>
/* scoped: 전역 범위X, 컴포넌트 범위 */
</style>