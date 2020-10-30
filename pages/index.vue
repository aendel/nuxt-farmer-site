<template>
  <v-container fluid class="pa-0 ma-0">
      <VideoHero :video="heroVideo"/>
      <div :style="`height:${windowHeightSize}px`"></div>
      <v-row>
        <v-col>
          <carousel :height="windowHeightSize" :gallery="carouselGallery" />
        </v-col>
      </v-row>

      <v-container>
        <timeline :histories="histories" />
      </v-container>
  </v-container>
</template>
<script>
import Timeline from '~/components/LayoutComponents/Timeline'
import Carousel from '~/components/LayoutComponents/Carousel'
import Hero from '~/components/LayoutComponents/Hero'
import VideoHero from '~/components/LayoutComponents/VideoHero'
import historiesQuery from '~/apollo/queries/histories/histories.gql'
import carouselQuery from '~/apollo/queries/carousel/carouselGallery.gql'
import heroVideoQuery from '~/apollo/queries/heroVideo/heroVideo.gql'
import Tractor from '~/components/Tractor'

export default {
  asyncData() {
    return new Promise((resolve) => {
      setTimeout(function () {
        resolve({ name: 'world' })
      }, 1000)
    })
  },
  components: {
    Timeline,
    Carousel,
    Hero,
    VideoHero,
    Tractor,
  },
  data() {
    return {
      items: this.generatePost(1),
      histories: [],
      carouselGallery: {},
      heroVideo: {}
    }
  },
  apollo: {
    histories: {
      prefetch: true,
      query: historiesQuery,
    },
    heroVideo:{
      prefetch: true,
      query: heroVideoQuery,
    },
    carouselGallery: {
      prefetch: true,
      query: carouselQuery,
    },
  },
  computed: {
    windowHeightSize() {
      if (!process.client) return 0
      return window.innerHeight
    },
    windowWidthSize() {
      if (!process.client) return 0
      return window.innerWidth
    },
  },
  methods: {
    generatePost(n) {
      return [...Array(n + 1).keys()].slice(1)
    },
    windowHeightSizeMethod(offset = 0) {
      if (!process.client) return 0
      return window.innerHeight - offset
    },
    windowWidthSizeMethod(offset = 0) {
      if (!process.client) return 0
      return window.innerWidth - offset
    },
  },
}
</script>
<style scoped>
.bg-img {
  background: rgba(76, 175, 80, 0.3);
}
</style>