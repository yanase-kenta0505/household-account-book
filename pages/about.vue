<template>
  <v-app>
    <v-app-bar elevation="0" color="#E3F2FD" max-height="80px">
      <div
        class="ml-10"
        style="font-size:30px;width:350px;height:80px;line-height:80px;font-weight:bold"
      >
        MONEY TEACHER
      </div>
    </v-app-bar>
    <div id="aboutUs-top" class="d-flex flex-column align-center pt-15">
      <h1>『MONEY　TEACHERとは』</h1>
      <p>
        面倒な家計管理で大事な時間を無駄にしていませんか？ <br />
        家計をどう見直せば良いか分からない <br />
        家計改善の相談をしたいけど相談できる人がいない。相談にお金をかけたくない
        <br />
      </p>
      <h2>その悩みすべて『MONEY　TEACHER』にお任せください</h2>
      <v-icon x-large class="mt-15">mdi-arrow-down-drop-circle-outline</v-icon>
    </div>
    <div
      id="aboutUs-cando"
      ref="observe_element"
      :class="{ bgChange: bgChange }"
    >
      <transition name="slideIn">
        <div v-show="slideIn">
          <h2>私たちが提供できること</h2>
          <div class="threeItem d-flex justify-lg-space-around mt-15">
            <div class="manegment">
              <p>管理</p>
            </div>
            <div class="fix">
              <p>見直し</p>
            </div>
            <div class="consultation">
              <p>相談</p>
            </div>
          </div>
        </div>
      </transition>
    </div>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      observer: null,
      bgChange: false,
      slideIn: false
    };
  },
  mounted() {
    const option = {
      root: null,
      rootMargin: "0px",
      threshold: [0.5]
    };
    this.observer = new IntersectionObserver(entries => {
      const entry = entries[0];
      if (entry && entry.isIntersecting) {
        console.log(entry);
        console.log("画面に入ったよ");
        this.bgChange = true;
        this.slideIn = true;
      }
    }, option);
    const observe_element = this.$refs.observe_element;
    this.observer.observe(observe_element);
  }
};
</script>

<style lang="scss" scoped>
#aboutUs-top {
  width: 100%;
  height: 100%;
  background-color: #e3f2fd;
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
#aboutUs-cando {
  width: 100%;
  height: 700px;
  background-color: #e3f2fd;
  &.bgChange {
    background-color: #e3f2fd;
  }
  & h2 {
    font-size: 40px;
    text-align: center;
  }
  & .threeItem {
    width: 100%;
    height: 100px;
    & > div {
      width: calc(100% / 3);
      & p {
        text-align: center;
        font-size: 25px;
      }
    }
  }
}

.slideIn-enter {
  transform: translateY(350px);
  opacity: 0;
}
.slideIn-enter-active {
  transition: transform 1s, opacity 1s;
}
.slideIn-enter-to {
  transform: translateY(0);
  opacity: 1;
}
</style>
