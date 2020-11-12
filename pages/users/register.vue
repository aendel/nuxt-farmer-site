<template>
  <v-container fluid class="d-flex align-center justify-center">
    <v-row align="center" justify="center">
      <v-col cols="6">
        <v-card>
          <v-card-text>
            <v-form lazy-validation>
              <p>Registrati</p>
              <v-text-field v-model="username" label="Name" required outlined clearable></v-text-field>

              <v-text-field v-model="email" label="E-mail" required outlined clearable type="email"></v-text-field>

              <v-text-field
                v-model="password"
                label="Password"
                required
                outlined
                clearable
                type="password"
              ></v-text-field>
            </v-form>
          </v-card-text>
          <v-divider class="mt-8"></v-divider>
          <v-card-actions>
            <v-btn
              color="success"
              text
              :disabled="isLoading"
              @click.stop.prevent="handleSubmit"
            >Registrati</v-btn>
          </v-card-actions>
        </v-card>
        <v-card class="mt-4">
          <v-card-text>
            Hai già un account?
            <nuxt-link :to="{ name: 'users-signin'}">Accedi</nuxt-link>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { mapMutations } from 'vuex'
import strapi from '~/utils/Strapi'

export default {
  data() {
    return {
      username: '',
      password: '',
      email: '',
    }
  },
  computed: {
    isLoading() {
      return this.$nuxt.$loading?.loading
    },
  },
  mounted() {
    this.$nextTick(() => {
      this.$nuxt.$loading.start()
      setTimeout(() => this.$nuxt.$loading.finish(), 2000)
    })
  },
  methods: {
    ...mapMutations({
      setUser: 'auth/setUser',
    }),
    async handleSubmit() {
      try {
        this.$nuxt.$loading.start()
        const response = await strapi.register(
          this.username,
          this.email,
          this.password
        )
        this.$nuxt.$loading.finish()
        // Call your setUser mutation from your auth.js store file
        this.setUser(response.user)
        this.$router.go(-1)
      } catch (err) {
        this.$nuxt.$loading.finish()
        alert(err.message || 'An error occurred.')
      }
    },
  },
}
</script>

<style>
</style>