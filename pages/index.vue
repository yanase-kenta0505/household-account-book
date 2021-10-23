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
              <nuxt-link to="about" class="mr-5">アプリについて</nuxt-link>
              <nuxt-link to="signUp" class="mr-5">新規会員登録</nuxt-link>
              <nuxt-link to="login" class="mr-5">ログイン</nuxt-link>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
      <v-row id="main" class="d-flex">
        <v-col cols="5">
          <div id="explanation-box">
            <div id="cards" class="d-flex flex-column align-center pt-16">
              <v-card class="mb-5"><p>家計の管理</p></v-card>
              <v-card class="mb-5"><p>家計の見直し</p></v-card>
              <v-card class="mb-5"><p>家計の相談</p></v-card>
            </div>
            <div id="arrow-box"></div>
            <div id="explanation-text"><p>このアプリ1つで解決します</p></div>
          </div>
        </v-col>
        <v-col cols="7">
          <img id="top-img" src="/toppage-image.png" alt=""
        /></v-col>
      </v-row>
    </v-row>
  </v-app>
</template>

<style lang="scss" scoped>
#container {
  width: 100%;
  flex: initial;

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
  & #main {
    width: 100%;
    flex: initial;
    height: 600px;
    margin: 0;
    & #top-img {
      height: 600px;
    }
    & #explanation-box {
      width: 100%;
      height: 100%;
      & #cards {
        width: 100%;
        height: 270px;
        & .v-card {
          width: 60%;
          height: 70px;
          & p {
            width: 100%;
            height: 100%;
            font-size: 30px;
            font-weight: bold;
            text-align: center;
            line-height: 70px;
          }
        }
      }
      & #arrow-box {
        width: 200px;
        height: 50px;
        margin: 80px auto 20px;
        background-image: url("/arrow.png");
        background-size: contain;
        background-position: center;
      }
      & #explanation-text{
          width: 80%;
          height: 30px;
          margin: 0 auto;
          & p{
              font-size: 25px;
              color: rgb(187, 61, 61);
              text-align: center;
          }
      }
    }
  }
}
</style>
