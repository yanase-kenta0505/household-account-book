<template>
  <v-app>
    <v-app-bar elevation="0" color="#E3F2FD" dense>
      <v-app-bar-title
        class="ml-10"
        style="font-size:30px;width:350px;height:80px;line-height:80px;font-weight:bold"
        >MONEY TEACHER</v-app-bar-title
      >
    </v-app-bar>
    <div id="aboutUs-top" class="d-flex flex-column align-center ">
      <h1>『MONEY　TEACHERとは』</h1>
      <p>
        面倒な家計管理で大事な時間を無駄にしていませんか？ <br />
        家計をどう見直せば良いか分からない <br />
        家計改善の相談をしたいけど相談できる人がいない。相談にお金をかけたくない
        <br />
      </p>
      <h2>その悩みすべて『MONEY　TEACHER』にお任せください</h2>
    </div>
    <div id="aboutUs-main">

    </div>
  </v-app>
</template>

<style lang="scss" scoped>
#aboutUs-top {
  width: 100%;
  height: 700px;
  background-color: #e3f2fd;
  padding-top: 150px;
  & h1 {
    font-size: 60px;
    // margin-top: 50px;
    margin-bottom: 30px;
  }
  & p {
    font-size: 20px;
    text-align: center;
    line-height: 2.5em;
    margin-bottom: 40px;
  }
  & h2 {
    font-size: 30px;
  }
}
#aboutUs-main{
    width: 100%;
    height: 500px;
    background-color: pink;
}
</style>
