<template>
  <section id="contact">
    <v-row class="pa-5" no-gutters>
      <!-- Header -->
      <v-col cols="12" class="mb-8">
        <div class="section-eyebrow mb-2">06 — Contact</div>
        <h2 class="text-h2 font-weight-bold">Let's <span class="gradient-text">talk.</span></h2>
      </v-col>

      <!-- Form -->
      <v-col cols="12" md="7" class="pr-md-8">
        <div class="glass pa-6 pa-md-8">
        <div class="text-body-2 text-medium-emphasis mb-6">
          Have anything you'd like to say? Fill out the form and I'll get back to you, or use the details on the right.
        </div>
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
                class="btn-gradient"
                size="large"
                type="submit"
                :disabled="!formIsValid"
              >
                Send Message
                <v-icon end>mdi-send</v-icon>
              </v-btn>
            </v-col>
          </v-row>
        </v-form>
        </div>
      </v-col>

      <!-- The contact info block -->
      <v-col cols="12" md="5" class="mt-8 mt-md-0">
        <div class="glass pa-6 pa-md-8 contact-info">
          <h3 class="block-title mb-5">Get in touch</h3>
          <div v-for="(det, i) in contactDetails" :key="i" class="contact-row">
            <div class="contact-icon">
              <v-icon size="20" color="primary">{{ det.icon }}</v-icon>
            </div>
            <div>
              <div class="contact-label">{{ det.title }}</div>
              <div class="contact-value">{{ det.val }}</div>
            </div>
          </div>

          <div class="mt-6 mb-2 text-overline" style="letter-spacing: 0.3em;">FOLLOW</div>
          <div class="d-flex" style="gap: 10px;">
            <a
              v-for="(icon, i) in socialIcons"
              :title="icon.name"
              :key="i"
              target="_blank"
              :href="icon.link"
              class="social-link"
            >
              <v-icon size="20">{{ icon.icon }}</v-icon>
            </a>
          </div>
        </div>
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
      } catch {
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
section { position: relative; }

a { text-decoration: none; }

.section-eyebrow {
  font-family: 'Space Grotesk', sans-serif;
  font-size: 13px;
  font-weight: 600;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  color: #ffaa00;
}

.block-title {
  display: inline-block;
  font-family: 'Space Grotesk', sans-serif;
  font-size: 14px;
  font-weight: 600;
  letter-spacing: 0.25em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.85);
  padding: 6px 14px;
  border-radius: 999px;
  background: rgba(255,170,0,0.08);
  border: 1px solid rgba(255,170,0,0.2);
}

.contact-row {
  display: flex;
  align-items: center;
  gap: 14px;
  padding: 14px 0;
}
.contact-row + .contact-row { border-top: 1px solid rgba(255,255,255,0.06); }
.contact-icon {
  width: 40px;
  height: 40px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  background: rgba(255,170,0,0.1);
  border: 1px solid rgba(255,170,0,0.25);
  border-radius: 12px;
}
.contact-label {
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.5);
}
.contact-value {
  font-size: 14px;
  color: rgba(255,255,255,0.92);
  margin-top: 2px;
}

.social-link {
  width: 40px;
  height: 40px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border-radius: 12px;
  color: rgba(255,255,255,0.75);
  border: 1px solid rgba(255,255,255,0.08);
  background: rgba(255,255,255,0.02);
  transition: all .25s ease;
}
.social-link:hover {
  color: #ffaa00;
  border-color: rgba(255,170,0,0.5);
  transform: translateY(-2px);
  box-shadow: 0 6px 18px rgba(255,170,0,0.25);
}
</style>
