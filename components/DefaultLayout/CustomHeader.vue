<template>
  <div
    class="fixed-header shadow-2xl bg-green-600 lg:flex lg:items-center lg:justify-between lg:p-4 md:p-2"
  >
    <div class="flex items-center justify-between">
      <div class="flex items-center">
        <div class="flex items-center">
          <img src="~/assets/iconfinder_tractor_1054956.png" class="m-2" />
          <a class="brand-title" href="#">Farmer Site </a>
        </div>
        <button @click="toggleOpen" class="px-4 cursor-pointer md:hidden">
          <svg
            v-if="isOpen"
            class="h-6 w-6"
            stroke="currentColor"
            fill="none"
            viewBox="0 0 24 24"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            ></path>
          </svg>
          <svg
            v-else
            class="w-6 h-6"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M4 6h16M4 12h16M4 18h16"
            ></path>
          </svg>
        </button>
      </div>
      <div class="hidden md:flex">
        <div class="flex items-center">
          <a class="" href="#">Home</a>
          <a class="" href="#">Storia</a>
          <a class="" href="#">Missione</a>
          <a class="" href="#">Chi Siamo</a>
          <a class="" href="#">Contattaci</a>
        </div>
        <div class="flex items-center ml-2">
          <template v-if="!username">
            <nuxt-link to="/users/signin" class="mx-2">
              <span>Accedi</span>
              <v-icon right>mdi-account-key</v-icon>
            </nuxt-link>
            <nuxt-link to="/users/register" class="button-sign-up">
              Registrati
              <v-icon right>mdi-account-plus</v-icon>
            </nuxt-link>
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
      </div>
    </div>
    <!-- Mobile -->
    <div :class="[isOpen ? '' : 'hidden', 'md:hidden']">
      <div class="flex flex-col">
        <a class="text-right mx-1 block" href="#">Home</a>
        <a class="text-right mx-1 block" href="#">Storia</a>
        <a class="text-right mx-1 block" href="#">Missione</a>
        <a class="text-right mx-1 block" href="#">Chi Siamo</a>
        <a class="text-right mx-1 block" href="#">Contattaci</a>
      </div>
      <div
        class="border-t border-green-300 flex justify-between items-center m-2 pt-2"
      >
        <template v-if="!username">
          <nuxt-link to="/users/signin" class="mx-2">
            <span>Accedi</span>
            <v-icon right>mdi-account-key</v-icon>
          </nuxt-link>
          <nuxt-link to="/users/register" class="button-sign-up">
            Registrati
            <v-icon right>mdi-account-plus</v-icon>
          </nuxt-link>
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
    </div>
  </div>
  <!-- <v-navigation-drawer v-model="drawer" temporary right fixed>
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
    </v-navigation-drawer> -->
</template>

<script>
import { mapGetters, mapMutations } from 'vuex'
export default {
  data() {
    return {
      drawer: false,
      group: null,
      toggle_exclusive: undefined,
      isOpen: false,
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
    toggleOpen() {
      this.isOpen = !this.isOpen
    },
  },
}
</script>

<style lang="postcss" scoped>
a {
  @apply inline-block p-2 text-green-300;
  &:hover {
    @apply text-green-100;
  }
  &:focus {
    @apply bg-green-400 rounded-lg text-green-100;
  }
}

.fixed-header {
  @apply fixed z-10 inset-x-0 top-0 left-0 rounded-lg m-4;
}

.brand-title {
  @apply text-xl mr-4;
}

.button-sign-up {
  @apply rounded-lg bg-red-500 text-red-200 font-medium;
  &:hover {
    @apply bg-red-600 text-red-100;
  }
}
</style>