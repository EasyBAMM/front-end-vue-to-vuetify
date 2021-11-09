<!-- 컴포넌트 UI 정의 -->
<template>
  <v-card>
    <v-card-title>게시물 목록</v-card-title>
    <v-card-text>
      <div v-if="page != null">
        <v-simple-table>
          <template v-slot:default>
            <thead>
              <tr>
                <th class="text-center" style="width: 70px">번호</th>
                <th class="text-center">제목</th>
                <th class="text-center" style="width: 90px">글쓴이</th>
                <th class="text-center" style="width: 120px">날짜</th>
                <th class="text-center" style="width: 70px">조회수</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="board in page.boards" :key="board.bno">
                <td class="text-center">{{ board.bno }}</td>
                <td>
                  <router-link
                    :to="`/menu07/board/read?bno=${board.bno}&pageNo=${page.pager.pageNo}&hit=true`"
                    >{{ board.btitle }}</router-link
                  >
                </td>
                <td class="text-center">{{ board.mid }}</td>
                <td class="text-center">{{ new Date(board.bdate).toLocaleDateString() }}</td>
                <td class="text-center">{{ board.bhitcount }}</td>
              </tr>
            </tbody>
          </template>
        </v-simple-table>
        <div class="d-flex flex-row justify-center align-center mt-2">
          <v-btn @click="changePageNo(1)" icon small class="mr-1">
            <v-icon>mdi-chevron-double-left </v-icon>
          </v-btn>
          <v-btn
            v-if="page.pager.groupNo > 1"
            @click="changePageNo(page.pager.startPageNo - 1)"
            icon
            small
            class="mr-1"
          >
            <v-icon>mdi-chevron-left</v-icon>
          </v-btn>
          <v-btn
            @click="changePageNo(pageNo)"
            fab
            small
            :class="`ml-1 mr-1 ${
              pageNo != page.pager.pageNo ? 'white gray--text' : 'primary white--text'
            }`"
            v-for="pageNo in range(page.pager.startPageNo, page.pager.endPageNo)"
            :key="pageNo"
          >
            {{ pageNo }}
          </v-btn>
          <v-btn
            v-if="page.pager.groupNo < page.pager.totalGroupNo"
            @click="changePageNo(page.pager.endPageNo + 1)"
            icon
            small
            class="mr-1"
          >
            <v-icon>mdi-chevron-right </v-icon>
          </v-btn>
          <v-btn @click="changePageNo(page.pager.totalPageNo)" icon small class="mr-1">
            <v-icon>mdi-chevron-double-right </v-icon>
          </v-btn>
        </div>
      </div>
      <v-card-actions class="justify-end">
        <v-btn to="/menu07/board/writeForm" small class="mr-2 white--text" color="#2196F3"
          >글작성</v-btn
        >
      </v-card-actions>
    </v-card-text>
    <alert-dialog
      v-if="alertDialog"
      :dialog="alertDialog"
      :loading="loading"
      :message="alertDialogMessage"
      @close="alertDialog = false"
    />
  </v-card>
</template>

<script>
import board from "@/apis/board";
import AlertDialog from "@/components/menu07/AlertDialog.vue";

export default {
  // 컴포넌트의 대표이름(devtools에 나오는 이름)
  name: "List",
  // 추가하고 싶은 컴포넌트 등록(import something from "/path")
  components: { AlertDialog },
  // 컴포넌트 데이터 정의
  data() {
    return {
      loading: false,
      alertDialog: false,
      alertDialogMessage: "",
      page: null,
    };
  },
  // 컴포넌트 메소드 정의
  methods: {
    changePageNo(pageNo) {
      // 같은 컴포넌트 내에서 URL만 변경
      this.$router.push(`/menu07/board/list?pageNo=${pageNo}`).catch(() => {});
      // URL 변경을 감시하는 Watch에서 데이터 가져옴
    },

    getBoardList(pageNo) {
      this.loading = true;
      this.alertDialog = true;
      board
        .getBoardList(pageNo)
        .then((response) => {
          this.loading = false;
          this.alertDialog = false;
          this.page = response.data;
          // console.log(response.data);
        })
        .catch((error) => {
          if (error.response) {
            if (error.response.status === 403) {
              this.loading = false;
              this.alertDialog = false;
              this.$router.push("/menu07/auth/jwtauth");
            }
          } else {
            this.loading = false;
            this.alertDialogMessage = "네트워크 통신오류";
          }
        });
    },

    range(start, end) {
      const arr = [];
      for (let i = start; i <= end; i++) {
        arr.push(i);
      }
      return arr;
    },
  },
  // 컴포넌트가 생성될 때 실행되는 Hook
  created() {
    let pageNo = this.$route.query.pageNo !== "undefined" ? this.$route.query.pageNo : 1;
    this.getBoardList(pageNo);
  },
  watch: {
    // 브라우저의 뒤로 가기 버튼을 이용해서 URL이 변경되었을 때 데이터 갱신을 위해 $route 감시
    $route(to, from) {
      // URL이 변경되면 해당 페이지 내용을 가져오기
      this.getBoardList(to.query.pageNo !== "undefined" ? to.query.pageNo : 1);
    },
  },
};
</script>

<!-- 컴포넌트 스타일 정의 -->
<style scoped>
/* scoped: 전역 범위X, 컴포넌트 범위 */
</style>