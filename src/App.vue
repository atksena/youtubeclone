<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" app flating temporary>
      <v-list>
        <v-row class="ma-2 mb-3">
          <v-icon class="mx-4" large>mdi-video</v-icon>
          <v-toolbar-title class="align-center">
            <span class="title">VideoKod</span>
          </v-toolbar-title>
        </v-row>
        <v-list-item v-for="item in items" :key="item.icon" link>
          <v-list-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-action>
          <v-list-item-content>
            <v-list-item-title>{{ item.text }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar app clipped-left>
      <v-app-bar-nav-icon @click="drawer = !drawer" />
      <v-icon class="mx-4" large>mdi-video</v-icon>
      <v-toolbar-title class="align-center">
        <span class="title">VideoKod</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-text-field
        class="mt-5"
        placeholder="Ara..."
        single-line
        append-icon="mdi-magnify"
        color="white"
      ></v-text-field>
      <v-spacer></v-spacer>
      <v-btn class="ml-0" icon>
        <v-icon>mdi-apps</v-icon>
      </v-btn>
      <v-btn class="ma-2" icon>
        <v-icon>mdi-bell</v-icon>
      </v-btn>
      <div>
        <v-menu
          v-model="menu"
          :close-on-content-click="false"
          :nudge-width="250"
          offset-x
        >
          <template v-slot:activator="{ on }">
            <v-avatar size="40">
              <v-img v-on="on" :src="require('@/assets/avatar.png')" />
            </v-avatar>
          </template>
          <v-card>
            <v-list>
              <v-list-item>
                <v-list-item-avatar></v-list-item-avatar>
                <v-list-item-content>
                  <v-list-item-title>Sena Atak</v-list-item-title>
                  <v-list-item-subtitle>VideoKod</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
            </v-list>
            <v-divider />
            <v-list>
              <v-list-item>
                <v-list-item-icon>
                  <v-icon>mdi-cog</v-icon>
                </v-list-item-icon>
                <v-list-item-title>Ayarlar</v-list-item-title>
              </v-list-item>
            </v-list>
            <v-list>
              <v-list-item>
                <v-list-item-icon>
                  <v-switch v-model="theme" color="orange"></v-switch>
                </v-list-item-icon>
                <v-list-item-title>Dark</v-list-item-title>
              </v-list-item>
            </v-list>
            <v-card-actions>
              <v-spacer />
              <v-btn color="orange" text @click="menu = false">Çıkış Yap</v-btn>
            </v-card-actions>
          </v-card>
        </v-menu>
      </div>
    </v-app-bar>
    <v-main>
      <v-container>
        <v-row class="mb-4">
          <v-col
            sm="6"
            md="4"
            lg="3"
            xl="2"
            v-for="(item, index) in 200"
            :key="index"
          >
            <v-card>
              <v-img
                height="200px"
                :src="`https://source.unsplash.com/500x300/?random=${
                  index + 1
                }`"
                :lazy-src="`https://source.unsplash.com/500x300/?random=${
                  index + 1
                }`"
              />
              <v-card-subtitle>Number {{ item }}</v-card-subtitle>
              <v-card-text
                ><div>Başlık Alanı</div>
                <div>Başlık İçeriği</div></v-card-text
              >
              <v-card-actions>
                <v-btn color="orange" text>Kaydet</v-btn>
                <v-btn color="orange" text>Paylaş</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    items: [
      { icon: "mdi-trending-up", text: "Popüler İçerik" },
      { icon: "mdi-youtube-subscription", text: "Takip" },
      { icon: "mdi-history", text: "Geçmiş" },
      { icon: "mdi-playlist-play", text: "Popüler İçerik" },
      { icon: "mdi-clock", text: "Popüler İçerik" },
    ],
    menu: false,
    theme: false,
    drawer: false,
  }),
  watch: {
    theme: function (next) {
      this.$vuetify.theme.dark = next;
    },
  },
};
</script>
