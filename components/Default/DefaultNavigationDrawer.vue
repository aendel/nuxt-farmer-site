<template>
<div>

  <v-navigation-drawer
    :clipped="true"
    permanent
    app
    :mini-variant="false"
    :expand-on-hover="false"
  >
    <timeline />
  </v-navigation-drawer>

  <v-app-bar
    :clipped-left="true"
    app
    hide-on-scroll
  >
    <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
    <v-btn
      icon
      @click.stop="miniVariant = !miniVariant"
    >
      <v-icon>mdi-{{ `chevron-${miniVariant ? 'right' : 'left'}` }}</v-icon>
    </v-btn>
    <v-btn
      icon
      @click.stop="clipped = !clipped"
    >
      <v-icon>mdi-application</v-icon>
    </v-btn>
    <v-btn
      icon
      @click.stop="fixed = !fixed"
    >
      <v-icon>mdi-minus</v-icon>
    </v-btn>
    <v-toolbar-title v-text="title" />
  </v-app-bar>
  </div>
</template>
<script>
import Timeline from '../LayoutComponents/Timeline'

export default {
  components:{
    Timeline
  },
  data(){
    return{
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js',
      target: '#third',
      options: {
        duration: 300,
        offset: 0,
        easing: 'easeInOutCubic',
      }
    }
  }
}
</script>
<style scoped>

</style>