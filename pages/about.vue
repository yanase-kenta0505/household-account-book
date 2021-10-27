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

      <div
        ref="observe_element"
        style="widht:100%; height:1200px;"
        class="mt-16"
      >
        <transition name="slideIn">
          <div
            class="threeService d-flex flex-column align-center"
            v-if="slideIn"
            style="width:100%;height:700px"
          >
            <h2>３つのサービス</h2>
            <div
              class="cardBox d-flex justify-space-around mb-15"
              style="width:600px;margin-top:30px"
            >
              <v-btn height="50px" @click="showA">MANAGEMENT</v-btn>
              <v-btn height="50px" @click="showB">OUTGOING</v-btn>
              <v-btn height="50px" @click="showC">MATCHING</v-btn>
            </div>
            <div class="mb-10">
              <v-expand-transition mode="out-in">
                <v-card
                  width="1100px"
                  height="auto"
                  class="card1 mt-10"
                  v-show="a"
                >
                  <img src="/manegement.jpg" alt="" />
                  <p>
                    基本となる家計管理<br />
                    収支の把握することが第一歩
                  </p>
                </v-card>
              </v-expand-transition>
              <v-expand-transition mode="out-in">
                <v-card
                  width="1100px"
                  height="400px"
                  class="card2 mt-10 "
                  v-show="b"
                >
                  <img src="/outgoing.png" alt="" />
                  <p>
                    あなたの家計術を発信しよう<br />
                    あなたの家計術が誰かを助けるかもしれません<br />
                    他の人の投稿を見ることもできます<br />
                    気に入った投稿があれば『LIKE』をつけてあげましょう
                  </p>
                </v-card>
              </v-expand-transition>
              <v-expand-transition mode="out-in">
                <v-card
                  width="1100px"
                  height="400px"
                  class="card3 mt-10"
                  v-show="c"
                >
                  <p>
                    あなたの先生を見つけてみませんか<br />
                    「税金」「保険」などお金に関することは難しいことばかり<br />
                    なんでも相談してみましょう
                  </p>
                  <img src="/teacher.png" alt="" />
                </v-card>
              </v-expand-transition>
            </div>
          </div>
        </transition>
      </div>
    </div>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      observer: null,
      slideIn: false,
      a: false,
      b: false,
      c: false
    };
  },
  methods: {
    showA() {
      if (this.b === true || this.c === true) {
        this.b = false;
        this.c = false;
        setTimeout(() => {
          this.a = true;
        }, 500);
      } else if (this.a === false) {
        this.a = true;
      } else {
        this.a = false;
      }
    },
    showB() {
      if (this.a === true || this.c === true) {
        this.a = false;
        this.c = false;
        setTimeout(() => {
          this.b = true;
        }, 500);
      } else if (this.b === false) {
        this.b = true;
      } else {
        this.b = false;
      }
    },
    showC() {
      if (this.a === true || this.b === true) {
        this.a = false;
        this.b = false;
        setTimeout(() => {
          this.c = true;
        }, 500);
      } else if (this.c === false) {
        this.c = true;
      } else {
        this.c = false;
      }
    }
  },

  mounted() {
    console.log(this.slideIn);
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
  height: 1300px;
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
  & .card1 {
    position: relative;
    & img {
      width: 100%;
      width: 100%;
    }
    & p {
      min-width: 400px;
      color: white;
      font-size: 24px;
      font-weight: bold;
      background-color: transparent;
      position: absolute;
      top: 20px;
      right: 60px;
    }
  }
  & .card2 {
    position: relative;
    & img {
      height: 100%;
      width: 590px;
    }
    & p {
      position: absolute;
      right: 30px;
      top: 80px;
      font-size: 17px;
      font-weight: bold;
    }
  }
  & .card3 {
    position: relative;
    & img {
      height: 100%;
      width: 590px;
      position: absolute;
      top: 0;
      right: 0;
    }
    & p {
      position: absolute;
      top: 90px;
      left: 30px;
      font-size: 17px;
      font-weight: bold;
    }
  }
}

.slideIn-enter {
  opacity: 0;
  transform: translateY(600px);
}
.slideIn-enter-active {
  transition: transform 2.5s, opacity 3.5s;
}
.slideIn-enter-to {
  transform: translateY(0);
  opacity: 1;
}
</style>
