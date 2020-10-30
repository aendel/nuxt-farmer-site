<template>
  <v-app >
    <v-content class="m-0 p-0">
      <custom-header />
      <v-content class="bg-gradient py-0">
        <transition>
          <nuxt />
        </transition>
      </v-content>
      <custom-footer />
    </v-content>
  </v-app>
</template>

<script>
import CustomHeader from '~/components/DefaultLayout/CustomHeader.vue'
import CustomFooter from '~/components/DefaultLayout/CustomFooter.vue'
export default {
  components: {
    CustomHeader,
    CustomFooter
  },
  data() {
    return {}
  }
}
</script>
<style scoped>
.bg-gradient{
  background: rgb(104,159,56);
  background: linear-gradient(180deg, rgba(156, 218, 102, 0.8) 0%, rgba(111,166,66,0.7) 40%, rgba(118,173,66,0.7) 60%, rgba(124,179,66,1) 100%);
  min-height: 80vh;
}
</style>