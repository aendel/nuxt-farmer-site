<template>
  <v-container>
    <v-row align="center" justify="center">
      <v-col cols="6">
        <v-card>
          <v-card-text>
            <v-form lazy-validation>
              <p>Accedi</p>

              <v-text-field v-model="email" label="E-mail" required outlined clearable type="email"></v-text-field>

              <v-text-field v-model="password" label="Password" required outlined clearable type="password"></v-text-field>
            </v-form>
          </v-card-text>
          <v-divider class="mt-8"></v-divider>
          <v-card-actions>
            <v-btn color="success" text :disabled="isLoading" @click.stop.prevent="handleSubmit">Accedi</v-btn>
          </v-card-actions>
        </v-card>
        <v-card class="mt-4">
          <v-card-text>
            Non hai un account? <nuxt-link :to="{ name: 'users-register'}">Registrati</nuxt-link>
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
      email: '',
      password: '',
      loading: false
    }
  },
  computed:{
    isLoading(){
      return this.$nuxt.$loading?.loading
    }
  },
  methods: {
    async handleSubmit() {
      try {
        this.$nuxt.$loading.start()
        const response = await strapi.login(
          this.email,
          this.password
        )
        this.$nuxt.$loading.finish()
        this.setUser(response.user)
        this.$router.go(-1)
      } catch (err) {
        this.$nuxt.$loading.finish()
        alert(err.message || 'An error occurred.')
      }
    },
    ...mapMutations({
      setUser: 'auth/setUser'
    })
  }
}
</script>