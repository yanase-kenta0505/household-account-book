<template>
  <v-app>
    <div id="a"></div>
    <div id="b" ref="observe_element">この要素を監視します。</div>
  </v-app>
</template>

<script>
export default {
  data() {
    return { observer: null };
  },
  mounted() {
    const option = {
      root: null,
      rootMargin: "0px",
      threshold: [0.25]
    };
    this.observer = new IntersectionObserver(entries => {
      const entry = entries[0];
      if (entry && entry.isIntersecting) {
        console.log(entry);
        console.log("画面に入ったよ");
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
  height: 300px;
  background-color: red;
}
</style>
