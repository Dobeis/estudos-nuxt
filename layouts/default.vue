<template>
  <v-app>
    <sidebar
      :show="showSidebar"
      @sidebarStatusChanged="setSidebarStatus"
    />
    <navbar
      title="Sistema Life"
      @toggleSidebar="toggleSidebar"
    />
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
  import Navbar from './../components/Navbar'
  import Sidebar from './../components/Sidebar'

  export default {
    middleware: 'auth',
    components: {
      navbar: Navbar,
      sidebar: Sidebar
    },
    head () {
      return {
        title: 'Sistema Life'
      }
    },
    data: () => ({
      showSidebar: false
    }),
    methods: {
      toggleSidebar () {
        this.showSidebar = !this.showSidebar
      },
      setSidebarStatus (event) {
        this.showSidebar = event
      }
    }
  }
</script>
