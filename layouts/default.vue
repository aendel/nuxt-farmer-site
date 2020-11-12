<template>
  <v-app >
  
      <custom-header />
  
        <transition>
          <nuxt class="page"/>
        </transition>
      
      <custom-footer />
    
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
.page{
    height: 100%;
    margin: 0px;
    padding: 0px;
    box-sizing: border-box;
}
.bg-gradient{
  background: rgb(104,159,56);
  background: linear-gradient(180deg, rgba(156, 218, 102, 0.8) 0%, rgba(111,166,66,0.7) 40%, rgba(118,173,66,0.7) 60%, rgba(124,179,66,1) 100%);
  min-height: 80vh;
}
</style>