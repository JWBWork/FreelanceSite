<template lang="html">

  <section fluid fill-height class="contact fade">
    <v-row justify="center" align="center">
      <v-col md="8">
        <v-form class="form" ref="contactForm" v-model="validContact">
          <v-text-field v-model="name" :rules="nameRules" label="Name" dense required></v-text-field>
          <v-text-field v-model="email" :rules="emailRules" label="E-mail" dense required></v-text-field>
          <v-textarea v-model="message" :rules="messageRuels" label="How can I help?" dense required no-resize></v-textarea>
          <!-- <v-row justify="space-around" > -->
              <v-btn
                color="rgb(153, 185, 227, 0.5)"
                class="mr-4"
                @click="reset"
              >
                Clear
              </v-btn>
              <v-btn
                :disabled="!validContact"
                color="success"
                class="mr-4"
                @click="validate"
                :loading="sendingEmail"
                style="opacity:0.8;"
              >
                <v-icon v-show="!sendingEmail">mdi-send</v-icon>
              </v-btn>
          <!-- </v-row> -->
        </v-form>
      </v-col>
      <v-col cols="12" md="4" class="my-0 py-0">
        <v-row align="center" justify="center">
          <v-col cols="3" md="12" style="white-space: nowrap;" align="center">
              <span @click="openEmail">
                <v-icon color="rgb(153, 185, 227)">mdi-email</v-icon>
                <span v-if="$vuetify.breakpoint.mdAndUp"> - {{$store.state.contactEmail}}</span>
              </span>
          </v-col>
          <!-- <v-row :class="[$vuetify.breakpoint.smAndDown ? '' : 'py-4 my-4']"></v-row> -->
          <v-col cols="3" md="12" style="white-space: nowrap;" align="center">
              <span @click="openLinkedIn">
                <v-icon color="rgb(153, 185, 227)">mdi-linkedin</v-icon>
                <span v-if="$vuetify.breakpoint.mdAndUp"> - linkedin.com/in/jacobwbrooks/</span>
              </span> 
          </v-col>
        </v-row>
      </v-col>
    </v-row>

    <div class="text-center ma-2">
      <v-snackbar
        v-model="snackbar"
      >
        {{ snackbarMessage }}
        <v-btn
          color="rgb(153, 185, 227)"
          text
          @click="snackbar = false"
        >
          Close
        </v-btn>
      </v-snackbar>
    </div>
  </section>

</template>

<script lang="js">
  import axios from 'axios';

  export default  {
    name: 'contact',
    props: [],
    mounted () {
      
    },
    data () {
      return {
        name: '',
        nameRules: [
          v => !!v || 'Name is Required!',
          v => (v && v.length <= 20 || 'Name must be < 20 char.')
        ],
        email: '',
        emailRules: [
          v => !!v || 'Email is Required!',
          v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
        ],
        message: '',
        messageRuels: [
          v => !!v || 'Message is Required!'
        ],
        validContact: true,
        snackbar: false,
        snackbarMessage: '',
        sendingEmail: false,
      }
    },
    methods: {
      validate () {
        this.sendingEmail = true;
        let valid = this.$refs.contactForm.validate()
        if (valid) {
          let data = {
            "email":this.email,
            "name":this.name,
            "message": this.message
          }
          axios.post( 
            // 'https://18.205.29.246:5000/dev-inquery',
            'https://api.jacobbrooks.dev/dev-inquery', 
            // 'http://127.0.0.1:5000/dev-inquery', 
            // 'http://127.0.0.1:5000/dev-inquery', 
            data,
            {
              // headers: {
                // 'Authorization': 'Bearer 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',
                // 'Content-Type': 'application/json',
                // 'Content-Type': 'application/x-www-form-urlencoded',
                // 'Access-Control-Allow-Origin': '*',
              // }
            }
          ).then(
            (response)=>{
                if (response.status == 200) {
                  this.snackbarMessage = "You'll hear from me soon!";
                  this.snackbar = true;
                  this.sendingEmail = false;
                  this.reset();
                }
            }
          ).catch(
            (error) => {
              console.log("error", error);
              this.snackbarMessage = "There has been an error! Please try again later...";
              this.snackbar = true;
              this.sendingEmail = false;
            }
          );
        }
      },
      reset () {
        this.$refs.contactForm.reset()
      },
      openEmail(){
        let email = "JacobBrooksWork@gmail.com";
        let subject = "Freelance%20Inquiry"
        let emailHref = `mailto:${email}?subject=${subject}`
        this.openNewTab(emailHref);
      },
      openLinkedIn(){
        this.openNewTab("https://www.linkedin.com/in/jacobwbrooks/");
      },
      openNewTab(url) {
        window.open(url);
      }
    },
    computed: {

    }
}


</script>

<style scoped lang="scss">
.contact {
}

.form{
  background-color: rgb(153, 185, 227);
  padding: 15px;
  border-radius: 20px;
  // opacity: 0.9;
  // -webkit-mask-image: -webkit-gradient(linear, left top, left bottom, from(rgba(0,0,0,1)), to(rgba(0,0,0,0)));
  // mask-image: linear-gradient(to bottom, rgba(0,0,0,1), rgba(0,0,0,0));
  background: linear-gradient(to bottom, rgb(153, 185, 227, 1), rgb(153, 185, 227, 0));
}
</style>
