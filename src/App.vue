<template>
  <v-app>
    <v-dialog :fullscreen="$vuetify.breakpoint.mobile">
      ...
    </v-dialog>
    <v-app-bar app color="primary" dark>
      <v-toolbar-title>
        Vuetify Dashboard
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn text rounded>Login</v-btn>
      <v-btn text rounded>Home</v-btn>
    </v-app-bar>
    <v-main>
      <v-card width="400" class="mx-auto mt-5">
      <v-card-title>
        <h1 class="display-1"> Login</h1>
      </v-card-title>
      <v-card-text>
        <v-form>
          <v-text-field
            label="Username"
            prepend-icon="mdi-account-circle"
          >
          </v-text-field>
          <v-text-field
            label="Password"
            :type="showPassword ? 'text' : 'password'"
            prepend-icon="mdi-lock"
            :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
            @click:append="showPassword = !showPassword"
          >
          </v-text-field>
        </v-form>
      </v-card-text>
      <v-card-actions>
        <v-btn color="success">Register</v-btn>
        <v-spacer></v-spacer>
        <v-btn color="info">Login</v-btn>
      </v-card-actions>
      </v-card>
    </v-main>
    <v-footer
      color="primary lighten-1"
      padless
    >
      <v-row
        justify="center"
        no-gutters
      >
        <v-btn
          v-for="link in links"
          :key="link"
          color="white"
          text
          rounded
          class="my-2"
        >
          {{ link }}
        </v-btn>
        <v-col
          class="primary lighten-2 py-4 text-center white--text"
          cols="12"
        >
          {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
        </v-col>
      </v-row>
    </v-footer>
  </v-app>
</template>

<script>
// import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    // HelloWorld,
  },

  data: () => ({
    showPassword: false,
    links: [
        'Home',
        'About Us',
        'Team',
        'Services',
        'Blog',
        'Contact Us',
      ],
    isMobile: false,

    beforeDestroy() {
      if(typeof window === 'undefined' ) return;

      window.removeEventListner('resize', this.onResize, {passive: true})
    },

    mounted () {
      this.onResize()
      console.log("ddfdfd")
      console.log(this.$vuetify.breakpoint.width)
      window.addEventListener('resize', this.onResize, { passive: true })
    },

    methods: {
      onResize () {
        this.isMobile =  window.innerWidth < 600
      }
    }
  }),
};
</script>
