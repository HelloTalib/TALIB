<template>
  <section id="about">
    <v-row class="pa-5" id="about-me" no-gutters>
      <!-- Background Image -->
      <v-img :src="abstract1" width="613" height="528" class="abstract-1"></v-img>

      <!-- The basic info page -->
      <v-col cols="12" md="7">
        <!-- Section 1, Who I am -->
        <section>
          <h2 class="text-h3 font-weight-bold text-primary mb-4">Who I am.</h2>
          <v-row justify="space-between">
            <!-- Info and signature -->
            <v-col cols="12" md="7">
              <div class="text-subtitle-1 mb-5">
                <p>{{ aboutMe }}</p>

                <!--  The Image -->
                <v-img :src="signature" width="150" class="ml-auto"></v-img>
              </div>
            </v-col>

            <!-- Second flex, contact details -->
            <v-col cols="12" md="4" class="mb-5">
              <v-row align="center" no-gutters>
                <!-- Flex 1 as headings -->
                <v-col cols="6" class="text-uppercase text-primary font-weight-medium">
                  <div class="mb-3">Location</div>
                  <div class="mb-3">Email</div>
                  <div class="mb-3">Phone</div>
                </v-col>

                <!-- Flex 2 as info -->
                <v-col cols="6" class="text-subtitle-1">
                  <div class="mb-3">Banani, Bogura, Bangladesh</div>
                  <div class="mb-3">talib@bdthemes.com</div>
                  <div class="mb-3">+8801795142054</div>
                </v-col>
              </v-row>
            </v-col>
          </v-row>
        </section>

        <!-- Section 2, What I can do for you -->
        <section>
          <h2 class="text-h3 text-primary font-weight-bold mb-4">What I can do for you.</h2>

          <div>
            <v-expansion-panels variant="popout">
              <v-expansion-panel
                v-for="(item, i) in aboutItems"
                :key="i"
                class="bg-transparent"
              >
                <v-expansion-panel-title>
                  <div class="text-h6 font-weight-light">{{ item.title }}</div>
                </v-expansion-panel-title>
                <v-expansion-panel-text>
                  <v-card>
                    <v-card-text>
                      <div>{{ item.description }}</div>
                    </v-card-text>
                  </v-card>
                </v-expansion-panel-text>
              </v-expansion-panel>
            </v-expansion-panels>
          </div>
        </section>
      </v-col>

      <!-- Second flex that covers the rest of the webpage with image -->
      <v-col md="5" class="d-none d-md-flex flex-column text-right text-uppercase">
        <div class="text-h3">Software Engineer</div>
        <span class="text-primary font-italic text-h6">Talib</span>

        <!-- That image -->
        <v-img
          :aspect-ratio="undefined"
          contain
          src="https://material-portfolio-dark.vuetifyjs.com/img/john.d70ed315.png"
          style="height: 100%; margin-right: -48px;"
        ></v-img>
      </v-col>
    </v-row>
  </section>
</template>


<script>
import abstract1 from "@/assets/abstract-1.png";
import signature from "@/assets/signature.png";

export default {
  data() {
    return {
      abstract1,
      signature,
      aboutMe:
        "Hi there! I'm Abu Talib. But everyone also known me as TALIB. I am a Software Engineer at BdThemes. I have over 5+ years of web developing experience in various languages. For me, sky's the limit.",
      aboutItems: [
        {
          title: "Front End Development",
          description:
            "I will create your website from scratch using HTML, CSS, SCSS, VueJs,VeutifyJs OR Meterial Design with Awesome jQuery features & cool animations:) I just needed PSD or anykind of website layout from you",
        },
        {
          title: "WordPress Theme Development",
          description:
            "I will convert your static website to Dynamic Website; That means you can change everyting in your website for example text, content, image, video, audio, etc. [without any coding knowledge]:-)",
        },
        {
          title: "Elementor Addons/Widget Develop From Scratch",
          description:
            "As a WordPress Developer or Elementor Expert you know that sometimes Elementor Or Elementor Pro default Widget is not enough to create your website. that's why you need a more customizable, Modern, and advanced Elementor Widget. @Hey! don't worry, I  will develop Elementor Addons or Wedget from scratch. I just want to make your life easier and put a smile on your face:)",
        },

        {
          title: "Online Store or e-Commerce Website",
          description:
            "I know, this is not something to boast of but yeah I have pretty decent knowledge of WooCommerce Website Development; In the world wide, I’ve dozens of active online store & e-commerce Website that I designed, customized and developed.",
        },
        {
          title: "REST APIs",
          description:
            "You are very well known what an API is, right? Well I know how to build one. yes, I can makes Node API and Restful Express API etc.",
        },
        {
          title: "CRUD Application",
          description:
            "I  will create your web application using firebase authentication that you can CREATE/READ/UPDATE/DELETE(post) without any kind of coding knowledge.",
        },
        {
          title: "Full Stack Web Development",
          description:
            'Count me, if you need to help any kind of Web Development. Be it frontend or backend. Just keep me away from Fornt-End Developer.I despise that, I have enough knowledge of backend too and alos "MERN, MEAN stack". that means build a website using MongoDB,"Expressjs, ReactJs or Vuejs & Nodejs.',
        },
      ],
    };
  },
};
</script>


<style scoped>
section {
  position: relative;
}

.abstract-1 {
  position: absolute !important;
  left: -48px;
  top: -48px;
  z-index: 0 !important;
}

.v-expansion-panel > li {
  border-top: 1px solid hsla(0, 0%, 100%, 0.12) !important;
}

.v-expansion-panel > li:nth-child(1) {
  border-top: none !important;
}
</style>
