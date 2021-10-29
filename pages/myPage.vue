<template>
  <v-app id="inspire">
    <v-system-bar app height="80px">
      <v-icon @click="drawer = !drawer" large class="ml-10">mdi-menu</v-icon>
    </v-system-bar>

    <v-navigation-drawer v-model="drawer" app>
      <v-sheet color="grey lighten-4" class="pa-4">
        <v-avatar class="mb-4" color="grey darken-1" size="64"></v-avatar>

        <div>john@vuetifyjs.com</div>
      </v-sheet>

      <v-divider></v-divider>
      <v-list class="pt-0">
      <post-dialog link></post-dialog>
        <v-list-item v-for="(link, index) in links" :key="link.text" link>
          <v-list-item-icon>
            <v-icon>{{ link.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title @click="setIndex(index)">
              {{ link.text }}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <v-container class="py-8 px-6" fluid>
        <v-row>
          <v-col v-for="card in cards" :key="card" cols="12">
            <v-card>
              <v-subheader>{{ card }}</v-subheader>

              <v-list two-line>
                <template v-for="n in 6">
                  <v-list-item :key="n">
                    <v-list-item-avatar color="grey darken-1">
                    </v-list-item-avatar>

                    <v-list-item-content>
                      <v-list-item-title>Message {{ n }}</v-list-item-title>

                      <v-list-item-subtitle>
                        Lorem ipsum dolor sit amet, consectetur adipisicing
                        elit. Nihil repellendus distinctio similique
                      </v-list-item-subtitle>
                    </v-list-item-content>
                  </v-list-item>

                  <v-divider
                    v-if="n !== 6"
                    :key="`divider-${n}`"
                    inset
                  ></v-divider>
                </template>
              </v-list>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import PostDialog from "~/.nuxt/components/post-dialog.vue";
export default {
  components: { PostDialog },
  data: () => ({
    cards: ["Today", "Yesterday"],
    drawer: false,
    links: [
      // {
      //   icon: "mdi-send",
      //   text: "投稿"
      // },
      {
        icon: "mdi-account-heart-outline",
        text: "フォロー"
      },
      {
        icon: "mdi-thumb-up",
        text: "お気に入り"
      },
      {
        icon: "mdi-human-greeting-proximity",
        text: "DM"
      },
      {
        icon: "mdi-account-edit",
        text: "アカウント編集"
      }
    ],
    index: null
  }),
  methods: {
    setIndex(index) {
      this.index = index;
    }
  }
};
</script>
