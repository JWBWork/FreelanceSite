<template>
    <v-app>
        <!--<v-app-bar
          app
          color="primary"
          dark
        >
        </v-app-bar>-->
        <v-content>
            <Home/>
        </v-content>
    </v-app>
</template>
<script>
    import HelloWorld from './components/HelloWorld';
    import Home from './components/home';

    export default {
        name: 'App',

        components: {
            HelloWorld,
            Home,
        },

        data: () => ({
            //
        }),
    };
</script>