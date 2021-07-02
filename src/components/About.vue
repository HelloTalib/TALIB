<template>
  <section id="about">
    <v-layout class="pa-5 wrap" id="about-me">
      <!-- Background Image -->
      <v-img :src="require('@/assets/abstract-1.png')" width="613" height="528" class="abstract-1"></v-img>

      <!-- The basic info page -->
      <v-flex xs12 md7>
        <!-- Section 1, Who I am -->
        <section>
          <h2 class="display-2 font-weight-bold primary--text mb-4">Who I am.</h2>
          <v-layout justify-space-between wrap>
            <!-- Info and signature -->
            <v-flex xs12 md7>
              <div class="subheading mb-5 mb-0">
                <p>{{ aboutMe }}</p>

                <!--  The Image -->
                <v-img :src="require('@/assets/signature.png')" width="150" class="ml-auto"></v-img>
              </div>
            </v-flex>

            <!-- Second flex, contact details -->
            <v-flex xs12 md4 mb-5>
              <v-layout align-center>
                <!-- Flex 1 as headings -->
                <v-flex xs6 text-uppercase primary--text font-weight-medium>
                  <div class="mb-3">Location</div>
                  <div class="mb-3">Email</div>
                  <div class="mb-3">Phone</div>
                </v-flex>

                <!-- Flex 2 as info -->
                <v-flex xs6 no-wrap subheading>
                  <div class="mb-3">Banani, Bogura, Bangladesh</div>
                  <div class="mb-3">abutalib4599@gmail.com</div>
                  <div class="mb-3">+8801795142054</div>
                </v-flex>
              </v-layout>
            </v-flex>
          </v-layout>
        </section>

        <!-- Section 2, What I can do for you -->
        <section>
          <!-- Heading -->
          <h2 class="display-2 primary--text font-weight-bold mb-4">What I can do for you.</h2>

          <div>
            <!-- Vueetify expansion panel -->
            <v-expansion-panel popout>
              <v-expansion-panel-content
                v-for="(item, i) in aboutItems"
                :key="i"
                class="transparent"
              >
                <template v-slot:header>
                  <div class="title font-weight-light">
                    <div>{{ item.title }}</div>
                  </div>
                </template>

                <div>
                  <v-card>
                    <v-card-text>
                      <div>{{ item.description }}</div>
                    </v-card-text>
                  </v-card>
                </div>
              </v-expansion-panel-content>
            </v-expansion-panel>
          </div>
        </section>
      </v-flex>

      <!-- Second flex that covers the rest of the webpage with image -->
      <v-flex hidden-sm-and-down md5 text-xs-right text-uppercase>
        <div class="display-1">Software Engineer</div>
        <span class="primary--text headline font-weight-light">Talib</span>

        <!-- That image -->
        <v-img
          contain
          src="https://material-portfolio-dark.vuetifyjs.com/img/john.d70ed315.png"
          style="height: 100%; margin-right: -48px;"
        ></v-img>
      </v-flex>
    </v-layout>
  </section>
</template>


<script>
export default {
  data() {
    return {
      aboutMe:
        "Hello there! I'm Abu Talib. Everyone also known me as TALIB. I am a Software Engineer at . I have over 3+ years of web developing experience in various languages. For me, sky's the limit.",
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
