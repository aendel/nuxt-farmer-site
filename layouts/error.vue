<template>
  <v-app dark>
    <v-content>
      <v-container fluid>
        <v-layout>
          <v-flex>
            <v-row align="center" justify="center">
              <v-col class="text-center">
                <h1 v-if="error.statusCode === 404">{{ pageNotFound }}</h1>
                <h1 v-else>{{ otherError }}</h1>
                <NuxtLink to="/">Home page</NuxtLink>
              </v-col>
            </v-row>
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
export default {
  layout: 'empty',
  props: {
    error: {
      type: Object,
      default: null,
    },
  },
  data() {
    return {
      pageNotFound: '404 Not Found',
      otherError: 'An error occurred',
    }
  },
  head() {
    const title =
      this.error.statusCode === 404 ? this.pageNotFound : this.otherError
    return {
      title,
    }
  },
}
</script>

<style scoped>
h1 {
  font-size: 20px;
}
</style>
