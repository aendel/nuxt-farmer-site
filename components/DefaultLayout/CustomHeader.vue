<template>
  <v-card flat>
    <v-app-bar
      id="app-bar"
      color="light-green darken-2"
    >
      <v-toolbar-title>
        <v-btn text to="/" @click="$vuetify.goTo('#app-bar')">
          Farmer Site
        </v-btn>
      </v-toolbar-title>
      <v-spacer />
      <v-btn-toggle
          v-model="toggle_exclusive"
          mandatory
        >
        <v-btn text>Home</v-btn>
        <v-btn text>Storia</v-btn>
        <v-btn text>Missione</v-btn>
        <v-btn text>Chi Siamo</v-btn>
        <v-btn text>Contattaci</v-btn>
      </v-btn-toggle>
      <v-spacer />

      <!-- <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-heart</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn> -->
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
    </v-app-bar>
    <v-navigation-drawer v-model="drawer" temporary right fixed>
      <v-list nav dense>
        <v-list-item-group
          v-model="group"
          active-class="deep-purple--text text--accent-4"
        >
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
  </v-card>
</template>

<script>
import { mapGetters, mapMutations } from 'vuex'
export default {
  data() {
    return {
      drawer: false,
      group: null,
       toggle_exclusive: undefined,
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