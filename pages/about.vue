<template>
  <v-app>
    <v-app-bar elevation="0" color="#E3F2FD" max-height="80px">
      <div class="ml-10 mt-10">
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
        style="width:100%; height:1200px;"
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
              <v-btn
                v-for="(btnItem, index) in btnItems"
                :key="btnItem.id"
                height="50px"
                @click="showWindow(index)"
                >{{ btnItem.name }}</v-btn
              >
            </div>
            <div class="mb-10">
              <v-expand-transition mode="out-in">
                <v-card
                  width="1100px"
                  height="400px"
                  class="mt-10"
                  :class="[`card${index + 1}`]"
                  v-show="btnItems[index].status"
                >
                  <img :src="images[index]" />
                  <p v-html="messages[index]"></p>
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
      index: 0,
      btnItems: [
        { name: "MANAGEMENT", status: false },
        { name: "OUTGOING", status: false },
        { name: "MATCHING", status: false }
      ],
      messages: [
        "基本となる家計管理<br />収支の把握することが第一歩",
        "あなたの家計術を発信しよう<br />あなたの家計術が誰かを助けるかもしれません<br /> 他の人の投稿を見ることもできます<br /> 気に入った投稿があれば『LIKE』をつけてあげましょう",
        "あなたの先生を見つけてみませんか<br />「税金」「保険」などお金に関することは難しいことばかり<br />なんでも相談してみましょう"
      ],
      images: ["/manegement.jpg", "/outgoing.png", "/teacher.png"]
    };
  },
  methods: {
    showWindow(index) {
      if (this.index === index) {
        console.log("index同じだよ");
        this.btnItems[index].status = !this.btnItems[index].status;
      } else if (
        this.btnItems.every(btnItem => {
          btnItem.status === false;
        })
      ) {
        this.btnItems[index].status = true;
      } else {
        this.btnItems.forEach((btnItem, index) => {
          btnItem.status = false;
          console.log("indexすべてfalseにしたよ");
        });

        setTimeout(() => {
          console.log("hi");
          this.index = index;
          this.btnItems[index].status = true;
          // console.log("indexに関係するstatusをtrueにしたよ");
        }, 500);
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
.v-toolbar__content {
  & > div {
    font-size: 40px;
    width: 350px;
    height: 80px;
    line-height: 80px;
    font-weight: bold;
    color: rgba(36, 89, 204, 0.7);
    font-weight: bold;
  }
}
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
      height: 100%;
    }
    & p {
      min-width: 400px;
      color: white;
      font-size: 24px;
      font-weight: bold;
      background-color: transparent;
      position: absolute;
      top: 20px;
      right: 40px;
    }
  }
  & .card2 {
    display: flex;
    & img {
      height: 100%;
      width: 590px;
    }
    & p {
      width: calc(100%-590px);
      font-size: 17px;
      font-weight: bold;
      align-self: center;
      margin: 0 auto;
    }
  }
  & .card3 {
    display: flex;
    & img {
      height: 100%;
      width: 590px;
      order: 2;
    }
    & p {
      width: calc(100% - 590px);
      font-size: 17px;
      font-weight: bold;
      align-self: center;
      order: 1;
      margin-left: 10px;
    }
  }
}

.slideIn-enter {
  opacity: 0;
  transform: translateY(600px);
}
.slideIn-enter-active {
  transition: transform 1.5s, opacity 2.5s;
}
.slideIn-enter-to {
  transform: translateY(0);
  opacity: 1;
}
</style>
