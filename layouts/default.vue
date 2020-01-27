<template>
  <v-app :dark="setTheme">
    <v-navigation-drawer v-model="drawer" :mini-variant="miniVariant" :clipped="clipped" permanent fixed app>
      <v-list>
        <v-list-item v-for="(item, i) in items" :key="i" :to="item.to" router>
          <v-list-item-action>
            <v-icon v-html="item.icon" color="blue darken-2"/>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title"/>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar :clipped-left="clipped" fixed app>
      <v-btn @click.stop="miniVariant = !miniVariant" icon>
        <v-icon v-html="miniVariant ? 'chevron_right' : 'chevron_left'" />
      </v-btn>
      <v-toolbar-title v-html="title"/>
      <v-spacer></v-spacer>
      <v-toolbar-items
      class="mt-8">
        <v-switch
          label="Dark Mode"
          v-model="goDark"
        ></v-switch>
      </v-toolbar-items>
    </v-app-bar>
    <v-content>
      <v-container fluid>
        <v-progress-circular
          v-if="loading"
          :size="200"
          :width="20"
          color="red"
          indeterminate
        >
          Loading 7MB models.
          <br>
          Please be patient...
        </v-progress-circular>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer :fixed="fixed" app>
      <v-flex class="text-xs-right">
        <a href="http://kodtemplar.com/">
          <span>KodTemplar - &copy; 2020</span>
        </a>
        &nbsp;
      </v-flex>
    </v-footer>
  </v-app>
</template>

<script>

export default {
  data () {
    return {
      goDark: false,
      clipped: false,
      drawer: true,
      fixed: false,
      items: [
        { icon: 'home', title: 'Welcome', to: '/' },
        { icon: 'people', title: 'Users', to: '/users' },
        { icon: 'wallpaper', title: 'Train', to: '/train' },
        { icon: 'camera', title: 'Recognize', to: '/recognize' }
      ],
      miniVariant: true,
      right: true,
      rightDrawer: false,
      title: 'Realtime Face Recognition &reg'
    }
  },
  computed: {
    setTheme() {
            if (this.goDark == true) {
                return (this.$vuetify.theme.dark = true);
            } else {
                return (this.$vuetify.theme.dark = false);
            }
        },
    loading () {
      return this.$store.state.face.loading
    }
  },
  // created () {
  //   this.$vuetify.theme.dark = true
  // },
  async mounted () {
    if(localStorage.getItem('goDark')) this.goDark =
    JSON.parse(localStorage.getItem('goDark'));
    const self = this
    await self.$store.dispatch('face/load')
  },
  watch: {
    goDark: {
      handler() {
        console.log('goDark Changed');
        localStorage.setItem('goDark', JSON.stringify(this.goDark));
      },
      deep: true,
    },
  }
}
</script>
