<template>
  <section id="contact">
    <v-row class="pa-5" no-gutters>
      <!-- Header -->
      <v-col cols="12">
        <h2 class="text-h3 font-weight-bold text-primary mb-4">Let's talk</h2>
      </v-col>

      <!-- Sub desc -->
      <v-col cols="12" md="5" class="mb-4 pr-md-5">
        <h2 class="text-primary text-h6 font-weight-light text-uppercase mb-2">What can I do for you?</h2>
        <div class="text-subtitle-1 mb-5">
          Have anything that you would like to say to me? Well you are more than welcome to do so. Please fill out the form below and hit that send button or else get in touch using the details given along with the form.
        </div>
        <h2 class="text-primary text-h6 font-weight-light text-uppercase mb-3">Send me a message</h2>
        <v-form
          ref="form"
          v-model="formIsValid"
          autocomplete="off"
          @submit.prevent="sendEmail"
        >
          <v-row no-gutters>
            <v-col cols="12">
              <v-text-field
                label="Name"
                variant="solo-filled"
                flat
                v-model="name"
                :rules="nonEmptyRule"
                required
              ></v-text-field>
            </v-col>

            <v-col cols="12">
              <v-text-field
                label="Email"
                variant="solo-filled"
                flat
                v-model="email"
                :rules="emailRules"
                required
              ></v-text-field>
            </v-col>

            <v-col cols="12">
              <v-text-field
                label="Subject"
                v-model="subject"
                :rules="nonEmptyRule"
                variant="solo-filled"
                flat
                required
              ></v-text-field>
            </v-col>

            <v-col cols="12">
              <v-textarea
                variant="solo-filled"
                flat
                :rules="nonEmptyRule"
                v-model="message"
                label="Message"
                required
              ></v-textarea>
            </v-col>

            <v-col cols="12" v-if="successAlert" class="mb-2">
              <v-alert type="success">Message Sent.</v-alert>
            </v-col>

            <v-col cols="12" v-if="infoAlert" class="mb-2">
              <v-alert type="info">Sending....</v-alert>
            </v-col>

            <v-col cols="12" v-if="errorAlert" class="mb-2">
              <v-alert type="error">Unable to send the message. Please try another method to contact me</v-alert>
            </v-col>

            <v-col cols="12" class="text-right">
              <v-btn
                color="primary"
                type="submit"
                :disabled="!formIsValid"
              >
                Send
                <v-icon class="ml-2">mdi-send</v-icon>
              </v-btn>
            </v-col>
          </v-row>
        </v-form>
      </v-col>

      <!-- The contact info block -->
      <v-col cols="12" md="3" class="text-left">
        <h2 class="text-primary text-h6 font-weight-light text-uppercase">Social Contacts</h2>

        <!-- Social Links -->
        <div class="my-4">
          <a
            class="mx-2"
            v-for="(icon, i) in socialIcons"
            :title="icon.name"
            :key="i"
            target="_blank"
            :href="icon.link"
          >
            <v-btn icon variant="text">
              <v-icon>{{ icon.icon }}</v-icon>
            </v-btn>
          </a>
        </div>

        <!-- The list with details -->
        <v-list class="bg-transparent" lines="three">
          <v-list-item v-for="(det, i) in contactDetails" :key="i">
            <template v-slot:prepend>
              <v-icon color="primary" class="mr-5" style="font-size: 48px;">{{ det.icon }}</v-icon>
            </template>
            <v-list-item-title class="mr-2 text-primary">{{ det.title }}</v-list-item-title>
            <v-list-item-subtitle>{{ det.val }}</v-list-item-subtitle>
          </v-list-item>
        </v-list>
      </v-col>

      <!-- The image block -->
      <v-col cols="12" md="4">
        <v-img
          contain
          style="top: 95px;"
          src="https://material-portfolio-dark.vuetifyjs.com/img/john-alt.7fef353c.png"
        ></v-img>
      </v-col>
    </v-row>
  </section>
</template>


<script>
export default {
  data() {
    return {
      // Form model directives
      formIsValid: true,
      name: "",
      email: "",
      subject: "",
      message: "",

      // Alert visibility directives
      successAlert: false,
      infoAlert: false,
      errorAlert: false,

      nonEmptyRule: [v => !!v || "This field can't be empty"],

      emailRules: [
        v => !!v || "E-mail is required",
        v => /.+@.+/.test(v) || "E-mail must be valid"
      ],

      contactDetails: [
        {
          title: "Address",
          val: "Banani, Bogura, Bangladesh",
          icon: "mdi-map-marker"
        },
        { title: "Phone", val: "+8801795142054", icon: "mdi-phone" },
        { title: "Email", val: "talib@bdthemes.com", icon: "mdi-email" }
      ],

      socialIcons: [
        {
          name: "Telegram",
          link: "https://t.me/hellotalib",
          icon: "mdi-telegram"
        },
        {
          name: "Twitter",
          link: "https://twitter.com/hellotalib",
          icon: "mdi-twitter"
        },
        {
          name: "Linkedin",
          link: "https://linkedin.com/in/hellotalib",
          icon: "mdi-linkedin"
        },
      ]
    };
  },

  methods: {
    async sendEmail() {
      // Validate the form, if errors, exit right away
      const { valid } = await this.$refs.form.validate();
      if (!valid) return;

      const body = new URLSearchParams({
        name: this.name,
        email: this.email,
        subject: this.subject,
        message: this.message
      });

      this.infoAlert = true;
      this.formIsValid = false;

      try {
        const res = await fetch("https://talib.netlify.app/mail.php", {
          method: "POST",
          headers: { "Content-Type": "application/x-www-form-urlencoded" },
          body
        });
        const text = await res.text();
        this.infoAlert = false;
        if (text.trim() === "Success") {
          this.successAlert = true;
        } else {
          this.errorAlert = true;
        }
      } catch (e) {
        this.infoAlert = false;
        this.errorAlert = true;
      } finally {
        setTimeout(() => {
          this.successAlert = false;
          this.errorAlert = false;
          this.$refs.form?.reset();
          this.formIsValid = true;
        }, 3000);
      }
    }
  }
};
</script>

<style scoped>
section {
  position: relative;
}

a {
  text-decoration: none;
}
</style>
