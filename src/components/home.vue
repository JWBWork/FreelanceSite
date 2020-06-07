<template lang="html">

    <section class="Home">
        <!-- <vue-scroll-snap :fullscreen="true"> -->
        <full-page ref="fullpage" :options="fullpageOptions">

            <!-- FIRST SLIDE: greeting and sale pitch -->
            <v-container fill-height fluid class="section" id="scroll-1">
                <v-row class="mt-n12">
                    <v-img :src="require('../assets/banner.jpg')"
                           :contain="false"
                           max-height="320px"
                           min-height="50px"
                           width="100vw"
                           class="header-image"
                           :style="{'height': $vuetify.breakpoint.xs ? '120px': ''}">
                    </v-img>
                    <v-col align="center" justify="end">
                            <h1 class="night-text mt-n12 mb-12 header-text">
                                Hi, I'm Jacob
                            </h1>
                    </v-col>
                </v-row>
                <v-row :class="['mt-n12', slideOneVisible ? 'fade-in' : 'fade-out']"
                        v-observe-visibility="(isVis, entry)=>slideOneVisible=isVis">
                    <v-col cols="12" md="4" align="center" justify="center"
                        :class="[$vuetify.breakpoint.smAndDown ? '': 'ml-10']">
                        <v-img 
                            :src="require('../assets/profilePic.jpg')"
                            class="profile"
                            :style="{'max-width': $vuetify.breakpoint.smAndDown ? '120px' : '225px'}"
                            aspect-ratio="1"/>
                        <!-- <v-img :src="require(`../assets/svg/Project.svg`)" contain class="profile"/> -->
                    </v-col>
                    <v-col cols="12" md="7" class="night-text" align="start">
                        <p :class="[$vuetify.breakpoint.smAndDown ? 'mx-3 px-3': '']">
                            Brooklyn based Design &amp; Develeopment. 
                            <br />
                            <br />
                            Freelance and full stack I can help you source the data your business needs and make the best first impression with a modern responsive landing page.
                            <br/>
                            <br/>
                            Inquire for:
                        </p>
                        <v-carousel height="50"
                                    hide-delimiters
                                    cycle
                                    continuous
                                    interval="2000"
                                    show-arrows
                                    class="mt-2"
                                    vertical
                                    :show-arrows-on-hover="true">
                            <v-carousel-item v-for="(service, i) in services"
                                                :key="i">
                                <v-col justify="center" align="center">
                                    <h2>{{service.name}}</h2>
                                </v-col>
                            </v-carousel-item>
                        </v-carousel>
                    </v-col>
                    <v-col md="1" cols="0"></v-col>
                </v-row>
                <v-row class="mb-10 mt-n5" align="center" justify="center">
                    <v-col cols="12" align="center" justify="center" 
                        :class="['night-text', $vuetify.breakpoint.smAndDown ? '': 'mt-10 pt-10']">
                        <p>services</p>
                        <v-icon @click="$refs.fullpage.api.moveSectionDown()"
                            color="rgb(153, 185, 227)">mdi-chevron-down</v-icon>
                    </v-col>
                </v-row>
            </v-container>

            <!-- SECOND SLIDE: explanation of services -->
            <v-container fill-height fluid class="section" id="scroll-2">
                <v-carousel height="90vh"
                            hide-delimiters
                            show-arrows
                            touchless
                            :class="[$vuetify.breakpoint.smAndDown ? '': '', slideTwoVisible ? 'fade-in' : 'fade-out']"
                            v-observe-visibility="(isVis, entry)=>slideTwoVisible=isVis">
                    <v-carousel-item v-for="service in services" :key="service.name" 
                        :class="[slideTwoVisible ? 'fade-in' : 'fade-out']">
                        <Service :icons="service.icons" :name="service.name" :description="service.description"/>
                    </v-carousel-item>
                </v-carousel>
            </v-container>

            <v-container fluid class="section" id="scroll-3">
                <v-row class="py-5 my-5"></v-row>
                <v-row class="night-text">
                    <v-col justify="start" align="center" 
                        v-observe-visibility="(isVis, entry)=>slideThreeVisible=isVis"
                        :class="[slideThreeVisible ? 'fade-in' : 'fade-out', $vuetify.breakpoint.smAndDown ? 'mt-n12' :'']">
                        <h1 :class="[$vuetify.breakpoint.smAndDown ? 'small-text' :'big-text']">What are you looking for?</h1>
                        <p>
                            Trying to make a great first impression, or source the data you need for your established business? I think I can help.
                        </p>
                    </v-col>
                </v-row>
                <v-row align="center" justify="center"
                    :class="['night-text', $vuetify.breakpoint.smAndDown ? 'mt-n8' :'py-8 my-8', 
                        slideThreeVisible ? 'fade-in' : 'fade-out']">
                    <v-col cols="12" md="8">
                        <Contact/>
                    </v-col>
                </v-row>
                <v-row :class="[$vuetify.breakpoint.smAndDown ? 'mt-n5' : 'pb-0 pt-10 mb-0 mt-10']">
                    <v-col align="center" cols="12" class="pa-0">
                        <transition name="slide">
                            <MyFooter v-show="slideThreeVisible"/>
                        </transition>
                    </v-col>
                </v-row>
                <v-row :class="[$vuetify.breakpoint.smAndDown ? 'mt-12': '']"></v-row>
            </v-container>
        </full-page>
        <!-- </vue-scroll-snap> -->

        <v-btn
        color="rgb(153, 185, 227)"
        dark
        style="position:absolute;top:10px;left:10px;"
        @click.stop="drawer = !drawer"
        v-show="!drawer"
        >
            <v-icon color="black">mdi-menu</v-icon>
        </v-btn>

        <v-navigation-drawer
        v-model="drawer"
        absolute
        temporary
        color="rgb(0, 0, 0, 0.5)"
        width="150px"
        >
            <v-list dense dark>
                <v-list-item link href="#home">
                    <v-list-item-icon>
                        <v-icon color="rgb(153, 185, 227)">mdi-home</v-icon>
                    </v-list-item-icon>

                    <v-list-item-content>
                        <v-list-item-title>Home</v-list-item-title>
                    </v-list-item-content>
                </v-list-item>
                <v-list-item link href="#services">
                    <v-list-item-icon>
                        <v-icon color="rgb(153, 185, 227)">mdi-code-greater-than</v-icon>
                    </v-list-item-icon>

                    <v-list-item-content>
                        <v-list-item-title>Services</v-list-item-title>
                    </v-list-item-content>
                </v-list-item>
                <v-list-item link href="#contact">
                    <v-list-item-icon>
                        <v-icon color="rgb(153, 185, 227)">mdi-send</v-icon>
                    </v-list-item-icon>

                    <v-list-item-content>
                        <v-list-item-title>Contact</v-list-item-title>
                    </v-list-item-content>
                </v-list-item>
            </v-list>
        </v-navigation-drawer>
    </section>

</template>

<script lang="js">
    import VueScrollSnap from "vue-scroll-snap";
    import Service from "./Service";
    import MyFooter from "./MyFooter";
    import Contact from "./Contact";

    export default {
        name: 'Home',
        props: [],
        components: { VueScrollSnap, Service, MyFooter, Contact },
        mounted() {

        },
        data() {
            return {
                services: [
                    {
                        name: "Webscraping",
                        icons: ["data", "spreadsheet"],
                        description: "The data your business needs extracted and structured for analysis.\n\n Price monitoring, market research, realestate, or news and content monitoring - whatever data your business needs sourced via automation."
                    },
                    {
                        name: "ETL Development",
                        icons: ["server", "analytics"],
                        description: "Periodic extraction and delivery of the data your business depends on.\n\n Data extracted and delivered in any format, or to any database, on a regular basis. Today's businesses are data driven, ensure you have the data you need to make the right decisions for your business."
                    },
                    {
                        name: "Landing Pages",
                        icons: ["plane", "landing-page"],
                        description: "Make the best first impression with a custom landing page.\n\n You only have one oppertunity to make a good impression - you need to be found on the web and you need a modern, resonsive landing page."
                    },
                ],
                slideOneVisible: false,
                slideTwoVisible: false,
                slideThreeVisible: false,
                fullpageOptions: {
                    licenseKey: 'BB9932F6-44344862-AAF7B447-A51F2E86',
                    afterLoad: this.afterLoad,
                    scrollBar: false,
                    menu: '#menu',
                    navigation: true,
                    anchors: ['home', 'services', 'contact'],
                    sectionsColor: []
                },
                drawer:null,
            }
        },
        methods: {
        },
        computed: {
            test(){
                console.log(this.slideThreeVisible)
                return this.slideThreeVisible;
            }
        }
    }


</script>

<style lang="scss">
.info-block {
  background-color: rgb(136, 173, 193, 0.4);
  border-radius: 20px;
}

.header-image {
  -webkit-mask-image: -webkit-gradient(
    linear,
    left top,
    left bottom,
    from(rgba(0, 0, 0, 1)),
    to(rgba(0, 0, 0, 0))
  );
  mask-image: linear-gradient(to bottom, rgba(0, 0, 0, 1), rgba(0, 0, 0, 0));
}
.header-text {
  font-size: 7vw;
}

#scroll-1 {
  background: rgb(8, 10, 15, 1);
  background: linear-gradient(
    0deg,
    rgba(0, 0, 0, 1) 30%,
    rgba(8, 10, 15, 1) 100%
  );
}
#scroll-2 {
  background: rgb(0, 0, 0) !important;
}
#scroll-3 {
  background: rgb(0, 0, 0);
  background: linear-gradient(
    0deg,
    rgba(0, 15, 50, 1) 5%,
    rgba(0, 0, 0, 1) 30%
  );
}

.night-text {
  color: rgb(153, 185, 227);
  font-family: Nunito;
  white-space: pre-line;
}

.svg-icon {
  filter: invert(71%) sepia(49%) saturate(228%) hue-rotate(174deg)
    brightness(93%) contrast(92%);
}
.col-svg {
  height: calc(10px + 10vw);
  width: calc(10px + 10vw);
}
.row-svg {
  height: calc(30px + 20vw);
  width: calc(30px + 20vw);
}

.small-text {
  font-size: medium;
}
.big-text {
  font-size: x-large;
}
.profile {
  // max-width: 150px;
  animation: rotating-clip 8s cubic-bezier(1, 0.03, 0.43, 0.96) infinite;
  // clip-path: polygon(100% 13%, 93% 100%, 11% 100%, 0 6%, 83% 0);
}
@keyframes rotating-clip {
  0% {
    clip-path: polygon(89% 0, 100% 86%, 85% 100%, 10% 100%, 0 15%, 15% 0);
  }
  50% {
    clip-path: polygon(15% 0, 89% 0, 100% 86%, 85% 100%, 10% 100%, 0 15%);
  }
  100% {
    clip-path: polygon(0 15%, 15% 0, 89% 0, 100% 86%, 85% 100%, 10% 100%);
  }
}

// fade in/out
.fade-in {
  transition: opacity 1.2s;
}
.fade-out {
  opacity: 0;
  transition: opacity 0.3s;
}
// Slide animation
.slide-leave-active {
  transition: 0.3s;
}
.slide-enter-active {
  transition: 0.5s;
}
.slide-enter {
  transform: translate(0, 100%);
}
.slide-leave-to {
  transform: translate(0, 100%);
}
</style>
