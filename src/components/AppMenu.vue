<!-- 컴포넌트 UI 정의 -->
<template>
  <v-list nav dense>
    <v-list-item>
      <v-list-item-content>
        <v-list-item-title class="text-h6"> Application </v-list-item-title>
        <v-list-item-subtitle>Vue to Vuetify</v-list-item-subtitle>
      </v-list-item-content>
    </v-list-item>
    <v-divider />

    <v-list-item-group active-class="deep-purple--text text--accent-4">
      <!-- <v-list-group :value="false" prepend-icon="mdi-home"> -->
      <v-list-group :value="false">
        <template v-slot:activator>
          <v-list-item-content>
            <v-list-item-title>Vue Home</v-list-item-title>
          </v-list-item-content>
        </template>
        <v-list-item to="/">
          <v-list-item-title>Home</v-list-item-title>
        </v-list-item>
        <v-list-item to="/about">
          <v-list-item-title>About</v-list-item-title>
        </v-list-item>
      </v-list-group>

      <v-list-group :value="false">
        <template v-slot:activator>
          <v-list-item-content>
            <v-list-item-title>Menu01 : Routing</v-list-item-title>
          </v-list-item-content>
        </template>
        <v-list-item to="/menu01/exam01view">
          <v-list-item-title>선언적 방식 화면 이동</v-list-item-title>
        </v-list-item>
        <v-list-item to="/menu01/exam02view">
          <v-list-item-title>프로그래밍 방식 화면 이동</v-list-item-title>
        </v-list-item>
        <v-list-item to="/menu01/exam03view">
          <v-list-item-title>중첩 라우팅</v-list-item-title>
        </v-list-item>
        <v-list-item to="/menu01/exam04view">
          <v-list-item-title>이름이 있는 뷰</v-list-item-title>
        </v-list-item>
        <v-list-item to="/menu01/exam05view">
          <v-list-item-title>URL 데이터 전달</v-list-item-title>
        </v-list-item>
      </v-list-group>
      <v-list-group :value="false">
        <template v-slot:activator>
          <v-list-item-content>
            <v-list-item-title>Menu02 : Component</v-list-item-title>
          </v-list-item-content>
        </template>
        <v-list-item to="/menu02/exam01expressions">
          <v-list-item-title>표현식 바인딩</v-list-item-title>
        </v-list-item>
        <v-list-item to="/menu02/exam02directives">
          <v-list-item-title>디렉티브 바인딩</v-list-item-title>
        </v-list-item>
        <v-list-item to="/menu02/exam03attrbinding">
          <v-list-item-title>속성 바인딩</v-list-item-title>
        </v-list-item>
        <v-list-item to="/menu02/exam04formbinding">
          <v-list-item-title>양방향 바인딩</v-list-item-title>
        </v-list-item>
        <v-list-item to="/menu02/exam05forrepeatbinding">
          <v-list-item-title>반복 바인딩</v-list-item-title>
        </v-list-item>
        <v-list-item to="/menu02/exam06computedbinding">
          <v-list-item-title>계산된 바인딩</v-list-item-title>
        </v-list-item>
        <v-list-item to="/menu02/exam07template">
          <v-list-item-title>템플릿 컴포넌트</v-list-item-title>
        </v-list-item>
      </v-list-group>
      <v-list-group :value="false">
        <template v-slot:activator>
          <v-list-item-content>
            <v-list-item-title>Menu03 : Event Handling & Wathch</v-list-item-title>
          </v-list-item-content>
        </template>
        <v-list-item to="/menu03/exam01eventhandling">
          <v-list-item-title>이벤트 처리</v-list-item-title>
        </v-list-item>
        <v-list-item to="/menu03/exam02watch">
          <v-list-item-title>데이터 변경 감시</v-list-item-title>
        </v-list-item>
      </v-list-group>
      <v-list-group :value="false">
        <template v-slot:activator>
          <v-list-item-content>
            <v-list-item-title>Menu04 : Data Delivery</v-list-item-title>
          </v-list-item-content>
        </template>
        <v-list-item to="/menu04/exam01props">
          <v-list-item-title>부모에서 자식으로 전달(props 이용)</v-list-item-title>
        </v-list-item>
        <v-list-item to="/menu04/exam02eventemit">
          <v-list-item-title>자식에서 부모로 전달(event 이용)</v-list-item-title>
        </v-list-item>
        <v-list-item to="/menu04/exam03inject">
          <v-list-item-title>의존 데이터 삽입(inject 이용)</v-list-item-title>
        </v-list-item>
        <v-list-item to="/menu04/exam04ref">
          <v-list-item-title>Ref를 이용한 접근</v-list-item-title>
        </v-list-item>
      </v-list-group>
      <v-list-group :value="false">
        <template v-slot:activator>
          <v-list-item-content>
            <v-list-item-title>Menu05 : LifeCycle Hooks</v-list-item-title>
          </v-list-item-content>
        </template>
        <v-list-item to="/menu05/exam01lifecyclehook">
          <v-list-item-title>라이프사이클 훅</v-list-item-title>
        </v-list-item>
      </v-list-group>
      <v-list-group :value="false">
        <template v-slot:activator>
          <v-list-item-content>
            <v-list-item-title>Menu06 : Vuex State Management</v-list-item-title>
          </v-list-item-content>
        </template>
        <v-list-item to="/menu06/exam01rootstate">
          <v-list-item-title>루트 상태 읽기 및 변경</v-list-item-title>
        </v-list-item>
        <v-list-item to="/menu06/exam02counterstate">
          <v-list-item-title>하위 상태 읽기 및 변경</v-list-item-title>
        </v-list-item>
      </v-list-group>
      <v-list-group :value="false">
        <template v-slot:activator>
          <v-list-item-content>
            <v-list-item-title>Menu07 : Axios AJAX</v-list-item-title>
          </v-list-item-content>
        </template>
        <v-list-item to="/menu07/exam01asynccontrol">
          <v-list-item-title>비동기 작업 중에 보여줄 스피너</v-list-item-title>
        </v-list-item>
        <v-list-item to="/menu07/auth/jwtauth">
          <v-list-item-title>JWT 인증</v-list-item-title>
        </v-list-item>
        <v-list-item to="/menu07/board/list">
          <v-list-item-title>게시물 목록</v-list-item-title>
        </v-list-item>
      </v-list-group>
    </v-list-item-group>
  </v-list>
</template>

<script>
export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "AppMenu",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: {},
  // 컴포넌트 데이터 정의
  data() {
    return {};
  },
  // 컴포넌트 메소드 정의
  methods: {},
};
</script>

<!-- 컴포넌트 스타일 정의 -->
<style scoped>
/* scoped: 전역 범위X, 컴포넌트 범위 */
</style>