<template>
  <v-app>
    <follow></follow>
  </v-app>
</template>

<script>
import PostDialog from "~/.nuxt/components/post-dialog.vue";
import AcountEdit from "~/.nuxt/components/acount-edit.vue";
import Follow from "~/.nuxt/components/follow.vue";
export default {
  components: { PostDialog, AcountEdit, Follow }
};
</script>
