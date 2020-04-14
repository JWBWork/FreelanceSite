<template lang="html">

    <section class="Home">
        <vue-scroll-snap :fullscreen="true">

            <!-- FIRST SLIDE: greeting and sale pitch -->
            <v-container fill-height fluid class="item" id="scroll-1">
                <v-row class="mt-n12" justify="center">
                    <v-img :src="require('../assets/banner.jpg')"
                           :contain="false"
                           max-height="320px"
                           min-height="50px"
                           width="100vw"
                           class="header-image" />
                </v-row>
                <v-row class="mt-n8">
                    <v-col cols="12" md="4" align="center" justify="center">
                        <h1 :class="['night-text', $vuetify.breakpoint.smAndDown ? 'mt-n12 mb-3': '']"
                            style="font-size:xx-large">
                            Jacob Brooks Work
                        </h1>
                        <v-img :src="require('../assets/profilePic.jpg')"
                               :class="[$vuetify.breakpoint.smAndDown ? 'small-profile mt-n5': 'big-profile']"
                               aspect-ratio="1"
                               style="border-radius:50%;" />
                    </v-col>
                    <v-col cols="12" md="7" class="night-text" justify="center" align="center">
                        <p :class="['px-4', 'night-text', $vuetify.breakpoint.smAndDown ? 'small-text': 'big-text']">
                            Hey how are you im jacob here's my sales pitch yada yada yada, and you're totally convinced to give me all your money
                            <br />
                            ... anyways - um you're here because you need:
                        </p>
                        <v-carousel height="50"
                                    hide-delimiters
                                    cycle
                                    class="mt-2">
                            <v-carousel-item v-for="(service, i) in services"
                                                :key="i">
                                <v-col justify="center" align="center">
                                    <h2>{{service}}</h2>
                                </v-col>
                            </v-carousel-item>
                        </v-carousel>
                    </v-col>
                    <v-col md="1" cols="0"></v-col>
                </v-row>
                <v-row class="mt-n8">
                    <v-col cols="12" align="center" justify="end" class="mt-10 pt-10 night-text">
                        <p align="end">something something something</p>
                    </v-col>
                </v-row>
    
            </v-container>

            <!-- SECOND SLIDE: explanation of services -->
            <v-container fill-height fluid class="item" id="scroll-2">
                <v-carousel height="90vh"
                            hide-delimiters>
                    <v-carousel-item>
                        <!-- SCRAPING CAROUSEL -->
                        <v-container fluid fill-height>
                            <v-row>
                                <v-col cols="12" md="5" align="center" justify="center">
                                    <v-img :src="require('../assets/scraping.svg')"
                                           :class="['svg-icon', $vuetify.breakpoint.smAndDown ? 'small-icon': 'big-icon']"
                                            contain />
                                    <p class="night-text pt-6 mt-8" style="font-size:xx-large">
                                        Scraping
                                    </p>
                                </v-col>
                                <v-col cols="12" md="6" class="night-text pa-10" align="center">
                                    <p :class="['night-text', $vuetify.breakpoint.smAndDown ? 'small-text': 'big-text']">
                                        Non irure do veniam ex commodo voluptate consequat ea. Deserunt consequat incididunt quis eu dolor cillum. Nisi dolor labore et nostrud quis. 
                                        <br />
                                        <br />
                                        Eu ipsum ipsum ipsum et laboris aliqua commodo cupidatat cillum consectetur dolor do. Consequat ipsum commodo laborum ipsum sunt sunt quis consectetur mollit aliquip cillum mollit. Do eu qui officia cupidatat.
                                    </p>
                                </v-col>
                                <v-col cols="0" md="1"></v-col>
                            </v-row>
                        </v-container>
                    </v-carousel-item>
                    <v-carousel-item>
                        <!-- Landing page CAROUSEL -->
                        <v-container fluid fill-height>
                            <v-row>
                                <v-col cols="12" md="5" align="center" justify="center">
                                    <v-img :src="require('../assets/landing-page.svg')"
                                           :class="['svg-icon', $vuetify.breakpoint.smAndDown ? 'small-icon': 'big-icon']"
                                           contain />
                                    <p class="night-text pt-6 mt-6" style="font-size:xx-large">
                                        Landing Page
                                    </p>
                                </v-col>
                                <v-col cols="12" md="6" class="night-text pa-10" align="center">
                                    
                                    <p :class="['night-text', $vuetify.breakpoint.smAndDown ? 'small-text': 'big-text']">
                                        asdfhk lasjdfhkaj sdl;fkjal ;skdjf;alskjd f;alskdjfl ;askdjfl;a ksjdf;alskdjf a
                                        asdl;kfj asl;dkfj a;lsdjfal;skdjf ;alskdjf ;alskdjfl;aksjdf;l aksjdfl;k ajsd;lfjkasd
                                        <br />
                                        <br />
                                        dkjfhaksdhf askdjfh aksjdfhkl ajsdhfkljash dfkljha sidufhqwuiefb iasdbfvuoayshdfkahsd
                                        asb dcjlasbhdkfjh aslcbas dbuwbeicbuh wieucbiwcbu eiawu ciawec iawcbiawbc
                                        cn iaweubcashbdckjasdbc abhscdasbuyd
                                    </p>
                                </v-col>
                                <v-col cols="0" md="1"></v-col>
                            </v-row>
                        </v-container>
                    </v-carousel-item>
                </v-carousel>
            </v-container>

            <v-container fill-height fluid class="item night-text" id="scroll-3">
                <v-row class="py-5 my-5"></v-row>
                <v-row>
                    <v-col justify="start" align="center">
                        <h1>GIVE ME YOUR MONEY</h1>
                    </v-col>
                </v-row>
                <v-row :class="[$vuetify.breakpoint.smAndDown ? 'py-8 my-8': 'py-12 my-12']"></v-row>
                <v-row>
                    <v-col align="center">
                        email stuff
                    </v-col>
                    <v-col align="center">
                        phone stuff
                    </v-col>
                </v-row>
                <v-row class="py-12 my-12"></v-row>
                <v-row class="pb-0 pt-12 mb-0 mt-12">
                    <v-col align="center">
                        <v-footer color="rgb(8, 10, 15, 1)" padless>
                            <v-row class="night-text">
                                <v-col>
                                    <div>Powered by Vue</div>
                                </v-col>
                                <v-col>
                                    Icons made by <a href="https://www.flaticon.com/authors/freepik" title="Freepik">Freepik</a>
                                </v-col>
                            </v-row>
                        </v-footer>
                    </v-col>
                </v-row>
            </v-container>
        </vue-scroll-snap>
    </section>

</template>

<script lang="js">
    import VueScrollSnap from "vue-scroll-snap";

    export default {
        name: 'Home',
        props: [],
        components: { VueScrollSnap, },
        mounted() {

        },
        data() {
            return {
                services: [
                    "Webscraping",
                    "Recurrent Scrape Delivery",
                    "Landing Pages"
                ]
            }
        },
        methods: {

        },
        computed: {

        }
    }


</script>

<style scoped lang="scss">
    .Home {
        /*overflow: hidden;*/
    }

    .item{
        /*height: 100vh;*/
        /*width:100vw;*/
    }

    .info-block {
        background-color: rgb(136, 173, 193, 0.4);
        border-radius: 20px;
    }

    .header-image {
        -webkit-mask-image: -webkit-gradient(linear, left top, left bottom, from(rgba(0,0,0,1)), to(rgba(0,0,0,0)));
        mask-image: linear-gradient(to bottom, rgba(0,0,0,1), rgba(0,0,0,0));
    }

    #scroll-1 {
        background: rgb(8, 10, 15, 1);
        background: linear-gradient(0deg, rgba(0, 0, 0, 1) 30%, rgba(8, 10, 15, 1) 100%);
    }

    #scroll-2 {
        background: rgb(0, 0, 0);
    }

    #scroll-3 {
        background: rgb(0, 0, 0);
        background: linear-gradient(0deg, rgba(0, 15, 75, 1) 1%, rgba(0, 0, 0, 1) 100%);
    }

    .night-text {
        color: rgb(153, 185, 227);
    }

    .svg-icon {
        filter: invert(71%) sepia(49%) saturate(228%) hue-rotate(174deg) brightness(93%) contrast(92%);
    }
    .small-icon {
        height:150px;
    }
    .big-icon {
        height:275px;
    }
    .small-text{
        font-size:large;
    }
    .big-text{
        font-size:x-large;
    }
    .big-profile {
        height: 300px;
        width: 300px;
    }
    .small-profile {
        height:150px;
        width:150px;
    }
</style>
