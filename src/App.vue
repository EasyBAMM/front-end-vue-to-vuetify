<template>
  <v-app>
    <app-header :drawer="drawer" @drawer-event="handleDrawer" />
    <v-navigation-drawer v-model="drawer" absolute temporary>
      <app-menu />
    </v-navigation-drawer>

    <v-main>
      <v-container fluid>
        <router-view></router-view>
      </v-container>
    </v-main>
    <v-footer color="secondary" dark> <div class="mx-auto">H.J.B</div></v-footer>
  </v-app>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppMenu from "./components/AppMenu.vue";
export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "App",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: { AppMenu, AppHeader },
  // 컴포넌트 데이터 정의
  data() {
    return { drawer: false };
  },
  // 컴포넌트 메소드 정의
  methods: {
    handleDrawer() {
      this.drawer = !this.drawer;
    },
  },
  created() {
    this.$store.dispatch("loadAuth");
  }
};
</script>
