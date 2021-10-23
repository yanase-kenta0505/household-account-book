<template>
  <v-app style="overflow:hidden;">
    <v-row id="container" class="mx-0 mt-0 mb-0 ">
      <v-row id="header" no-gutters class="d-flex justify-space-between">
        <v-col id="main-text" cols="4" class="mt-5 ml-15 px-0 pt-0 pb-0"
          >MONEY TEACHER
        </v-col>
        <v-col cols="6" id="nav" class="mt-5 px-0 pt-0 pb-0">
          <v-row style="nav-box" no-gutters class="ml-10 d-flex justify-end">
            <v-col cols="7" class="mr-5 d-flex justify-end">
              <nuxt-link style="color:white;" to="about" class="mr-5"
                >アプリについて</nuxt-link
              >
              <nuxt-link style="color:white;" to="signUp" class="mr-5"
                >新規会員登録</nuxt-link
              >
              <nuxt-link style="color:white;" to="login" class="mr-5"
                >ログイン</nuxt-link
              >
            </v-col>
          </v-row>
        </v-col>
      </v-row>
      
    </v-row>
  </v-app>
</template>

<style lang="scss" scoped>
#container {
  width: 100%;
  height: 100%;
  flex: initial;
  display: block;
  background-image: url("/money-manege.jpg");
  background-size: cover;
  background-position: bottom;
  & #header {
    flex: initial;
    height: 80px;
    width: 100%;
    & #main-text {
      font-size: 40px;
      font-weight: bold;
      color: rgba(36, 89, 204, 0.7);
    }
    & #nav {
      //   background-color: pink;
      & #nav-box {
        width: 100%;
      }
    }
  }
  
}
</style>
