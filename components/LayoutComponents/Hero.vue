<template>
  <v-card class="pa-4" shaped :elevation="20" color="light-green accent-1">
    <v-card-title>
      <h1 class="display-4 font-weight-thin">Farmer Site</h1>
    </v-card-title>
    <v-card-subtitle>
      <h2 class="font-weight-light">Grown your application today!</h2>
    </v-card-subtitle>
    <v-card-actions class="mt-4">
      <v-fab-transition>
        <v-btn
          color="success"
          fab
          dark
          small
          bottom
          absolute
          right
          @click="$vuetify.goTo('#carousel')"
        >
          <v-icon>mdi-chevron-down</v-icon>
        </v-btn>
      </v-fab-transition>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {}
</script>