<template lang="html">
  <v-container fluid fill-height class="service">
    <v-row>
        <v-col cols="0" md="1"></v-col>
        <v-col cols="12" md="4" align="center">
            <v-row justify="center" :class="[$vuetify.breakpoint.smAndDown ? 'my-n10': '']">
                <v-col cols="5" md="6" v-for="icon in icons" :key=icon>
                    <v-img :src="require(`../assets/svg/${icon}.svg`)"
                        :class="['svg-icon', 
                            $vuetify.breakpoint.smAndDown ? 'row-svg': 'col-svg']"
                        contain />
                        <!-- style="transform: rotate(75deg);" -->
                </v-col>
            </v-row>
            <p class="night-text pt-6 mt-10" style="font-size:xx-large">
                {{name}}
            </p>
        </v-col>
        <v-col cols="12" md="6" class="night-text" align="start">
            <p :class="['night-text', $vuetify.breakpoint.smAndDown ? 'small-text': 'big-text']">
                {{description}}
            </p>
        </v-col>
        <v-col cols="0" md="1"></v-col>
    </v-row>
</v-container>

</template>

<script lang="js">

  export default  {
    name: 'service',
    props: [
      'icons',
      'name',
      'description'
    ],
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
    .service {

    }
</style>
