<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
       <q-btn
        v-if="$route.fullPath==='/chat'"
         icon="arrow_back"
         dense
         label="Back"
         flat
         to="/"
       />
        <q-toolbar-title class="absolute-center">
          {{ title }}
        </q-toolbar-title>
      </q-toolbar>
    </q-header>
    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>


import { defineComponent, computed } from 'vue'
import { useRoute } from 'vue-router'

export default defineComponent({
  name: 'MainLayout',

  components: {
  },
 setup () {
   /**
    *  This computed property will return dynamically the layout's title corresponding its route page 
    */
    const title = computed(() => {
      const $route = useRoute() 
      if ($route.fullPath === '/') {
        return 'SmackChat'
      } else if($route.fullPath === '/auth') {
        return 'Login'
      } else if ($route.fullPath === '/chat') {
        return 'Chat'
      }

    })

    return {
      title
    }
  }
})
</script>
