<template>
    <v-carousel
      id="carousel"
      :height="height"
      continuous
      cycle
      hide-delimiter-background
      hide-delimiters
      :show-arrows="false"
      dark
      
    >
      <v-carousel-item v-for="(image,i) in gallery.images" :key="i">
        <!-- <span
        class="black--text"
        >{{history.id}} {{history.title}} {{history.description}} {{history.img}}</span> -->
        <v-img
          :src="`http://localhost:1337${image.formats.large.url}`"
          :lazy-src="`http://localhost:1337${image.formats.large.url}`"
        >
        <!-- <span>{{image.formats.large.url}}</span> -->
        </v-img>
      </v-carousel-item>
    </v-carousel>
</template>

<script>
export default {
  props: {
    height: {
      type: Number,
      default: 400,
    },
    histories: {
      type: Array,
      default: () => [],
    },
    gallery: {
      type: Object,
      default: () => {},
    },
  },
}
</script>

<style>
</style>