<template>
  <div>
    <v-app-bar id="app-bar"  class="pa-0 ma-0" color="light-green darken-2"  app>
      <!-- <v-app-bar-nav-icon></v-app-bar-nav-icon> -->

      <v-toolbar-title>
        <v-btn nuxt text depressed to="/" @click="$vuetify.goTo('#app-bar')">Farmer Site</v-btn>
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <div>
        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-heart</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>
        <template v-if="!username">
          <v-btn nuxt to="/users/register" class="mx-2">
            Registrati
            <v-icon right>mdi-account-plus</v-icon>
          </v-btn>
          <v-btn nuxt to="/users/signin" dark class="mx-2" text outlined>
            <span>Accedi</span>
            <v-icon right>mdi-account-key</v-icon>
          </v-btn>
        </template>
        <template v-else>
          <v-btn @click="drawer = !drawer" dark class="mx-2" icon>
            <v-icon>mdi-account</v-icon>
          </v-btn>
          <v-btn @click="logout" dark class="mx-2" text>
            <span>Disconnetti</span>
            <v-icon right>mdi-account-off</v-icon>
          </v-btn>
        </template>
      </div>
    </v-app-bar>
    <v-navigation-drawer v-model="drawer" temporary right fixed>
      <v-list nav dense>
        <v-list-item-group v-model="group" active-class="deep-purple--text text--accent-4">
          <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-home</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Home</v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-account</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Account</v-list-item-title>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<script>
import { mapGetters, mapMutations } from 'vuex'
export default {
  data() {
    return {
      drawer: false,
      group: null,
    }
  },
  computed: {
    ...mapGetters({
      username: 'auth/username',
    }),
  },
  methods: {
    ...mapMutations({
      logout: 'auth/logout',
    }),
  },
}
</script>

<style>
</style>