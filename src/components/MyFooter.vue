<template lang="html">
  <v-footer color="rgb(8, 10, 15, 1)" class="footer" padless fixed>
    <v-row class="night-text">
      <v-col>
        <v-row justify="center">
          <v-col
            cols="12"
            md="4"
            align="[$vuetify.breakpoint.smAndDown ? 'end' : 'center']"
            style="white-space: nowrap;"
            class="ma-0 pa-0"
          >
            Powered by
          </v-col>
          <v-col
            cols="12"
            md="2"
            align="[$vuetify.breakpoint.smAndDown ? 'start' : 'center']"
            :class="[$vuetify.breakpoint.smAndDown ? 'ma-0 pa-0' : 'ma-0 pa-0']"
            style="white-space: nowrap;"
          >
            <span><v-icon color="green">mdi-vuejs</v-icon></span>
            <!-- , -->
            <span><v-icon color="blue">mdi-vuetify</v-icon></span>
            <!-- &#x26; -->
            <span><v-icon color="yellow">mdi-language-python</v-icon></span>
          </v-col>
        </v-row>
      </v-col>
      <v-col>
        <v-row justify="center">
          <v-col cols="12" style="white-space: nowrap;" class="ma-0 pa-0">
            Art by
            <a
              href="https://www.flaticon.com/authors/freepik"
              title="Freepik"
              class="ml-2"
              >Freepik</a
            >
          </v-col>
        </v-row>
      </v-col>
      <v-col>
        <v-row justify="center">
          <v-col
            cols="12"
            md="3"
            align="[$vuetify.breakpoint.smAndDown ? 'end' : 'center']"
            class="ma-0 pa-0"
          >
            Hosted by
          </v-col>
          <v-col
            cols="12"
            md="1"
            align="[$vuetify.breakpoint.smAndDown ? 'start' : 'center']"
            class="ma-0 pa-0"
          >
            <span><v-icon color="yellow">mdi-aws</v-icon></span>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-footer>
</template>

<script lang="js">

  export default  {
    name: 'myfooter',
    props: [],
    mounted () {

    },
    data () {
      return {

      }
    },
    methods: {

    },
    computed: {

    }
}
</script>

<style scoped lang="scss">
.footer {
}
</style>
