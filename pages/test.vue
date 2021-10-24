<template>
  <v-app>
    <div id="a"></div>
    <div id="b" ref="observe_element">
      <p>この要素を監視します。</p>
      <transition name="apper">
        <div id="c" v-show="none === false"></div>
      </transition>
    </div>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      observer: null,
      none: true
    };
  },
  mounted() {
    const option = {
      root: null,
      rootMargin: "0px",
      threshold: [1]
    };
    this.observer = new IntersectionObserver(entries => {
      const entry = entries[0];
      if (entry && entry.isIntersecting) {
        console.log(entry);
        console.log("画面に入ったよ");
        this.none = false;
      }
    }, option);
    const observe_element = this.$refs.observe_element;
    this.observer.observe(observe_element);
  }
};
</script>

<style lang="scss" scoped>
#a {
  width: 100%;
  height: 700px;
  background-color: blue;
}
#b {
  widows: 100%;
  height: 500px;
  background-color: red;
  & #c {
    width: 200px;
    height: 200px;
    background-color: green;
    margin: 100px auto 0;
    &.none {
      display: none;
    }
  }
}

.apper-enter {
  transform: translateY(350px);
  opacity: 0;
}
.apper-enter-active {
  transition: transform 2s, opacity 2s;
}
.apper-enter-to {
  transform: translateY(0);
  opacity: 1;
}
</style>
