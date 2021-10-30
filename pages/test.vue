<template>
  <v-app>
    <acount-edit></acount-edit>
  </v-app>
</template>

<script>
import PostDialog from "~/.nuxt/components/post-dialog.vue";
import AcountEdit from "~/.nuxt/components/acount-edit.vue";
export default {
  components: { PostDialog , AcountEdit}
};
</script>
