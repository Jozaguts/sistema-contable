<template>
  <v-app id="inspire">
    <Header v-model="expandOnHover"></Header>

    <v-main>
      <v-container fluid class="page-wrapper">
        <router-view />
        <v-btn
          bottom
          color="success"
          dark
          fab
          fixed
          right
          @click.stop="setCustomizerDrawer(!Customizer_drawer)"
        >
          <v-icon>mdi-cog</v-icon>
        </v-btn>
      </v-container>
    </v-main>
    <Sidebar :expand-on-hover.sync="expandOnHover"></Sidebar>

    <Customizer v-model="expandOnHover"></Customizer>

    <Footer></Footer>
  </v-app>
</template>

<script>
import Header from '../components/header/Header'
import Sidebar from '../components/sidebar/Sidebar'
import Footer from '../components/footer/Footer'
import Customizer from '../components/customizer/Customizer'
import { mapState, mapMutations } from 'vuex'
export default {
  name: 'dashboard',

  components: {
    Header,
    Sidebar,
    Footer,
    Customizer
  },

  props: {
    source: String
  },
  data: () => ({
    expandOnHover: false
  }),
  computed: {
    ...mapState(['Customizer_drawer'])
  },

  methods: {
    ...mapMutations({
      setCustomizerDrawer: 'SET_CUSTOMIZER_DRAWER'
    })
  }
}
</script>

<style>
</style>