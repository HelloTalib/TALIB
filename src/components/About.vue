<template>
  <section id="about">
    <!-- Background decorative image, absolutely positioned -->
    <v-img :src="abstract1" width="613" height="528" class="abstract-1"></v-img>
    <v-row class="pa-5 position-relative" id="about-me" no-gutters>
      <!-- The basic info page -->
      <v-col cols="12" md="7">
        <!-- Section 1, Who I am -->
        <section>
          <div class="section-eyebrow mb-2">01 — Introduction</div>
          <h2 class="text-h2 font-weight-bold mb-6">Who <span class="gradient-text">I am.</span></h2>
          <v-row justify="space-between">
            <!-- Info and signature -->
            <v-col cols="12" md="7">
              <div class="text-subtitle-1 mb-5">
                <p>{{ aboutMe }}</p>

                <!--  The Image -->
                <v-img :src="signature" width="150" class="ml-auto"></v-img>
              </div>
            </v-col>

            <!-- Contact details -->
            <v-col cols="12" md="5" class="mb-5">
              <div class="info-card glass pa-5">
                <div class="info-row">
                  <v-icon color="primary" size="20">mdi-map-marker-outline</v-icon>
                  <div>
                    <div class="info-label">Location</div>
                    <div class="info-value">Banani, Bogura, Bangladesh</div>
                  </div>
                </div>
                <div class="info-row">
                  <v-icon color="primary" size="20">mdi-email-outline</v-icon>
                  <div>
                    <div class="info-label">Email</div>
                    <div class="info-value">talib@bdthemes.com</div>
                  </div>
                </div>
                <div class="info-row">
                  <v-icon color="primary" size="20">mdi-phone-outline</v-icon>
                  <div>
                    <div class="info-label">Phone</div>
                    <div class="info-value">+8801795142054</div>
                  </div>
                </div>
              </div>
            </v-col>
          </v-row>
        </section>

        <!-- Section 2, What I can do for you -->
        <section>
          <div class="section-eyebrow mt-12 mb-2">02 — Services</div>
          <h2 class="text-h2 font-weight-bold mb-6">What I <span class="gradient-text">can do.</span></h2>

          <div>
            <v-expansion-panels variant="accordion" class="glass-panels">
              <v-expansion-panel
                v-for="(item, i) in aboutItems"
                :key="i"
                bg-color="transparent"
              >
                <v-expansion-panel-title>
                  <div class="d-flex align-center" style="gap:14px">
                    <span class="panel-number">0{{ i + 1 }}</span>
                    <div class="text-h6 font-weight-medium">{{ item.title }}</div>
                  </div>
                </v-expansion-panel-title>
                <v-expansion-panel-text>
                  <div class="text-body-2 text-medium-emphasis">{{ item.description }}</div>
                </v-expansion-panel-text>
              </v-expansion-panel>
            </v-expansion-panels>
          </div>
        </section>
      </v-col>

      <!-- Right column: stats + portrait -->
      <v-col md="5" class="d-none d-md-flex flex-column pl-md-8">
        <div class="stats-grid mb-6">
          <div class="stat-card glass">
            <div class="stat-num gradient-text">5+</div>
            <div class="stat-label">Years experience</div>
          </div>
          <div class="stat-card glass">
            <div class="stat-num gradient-text">100+</div>
            <div class="stat-label">Projects shipped</div>
          </div>
          <div class="stat-card glass">
            <div class="stat-num gradient-text">30+</div>
            <div class="stat-label">WordPress themes</div>
          </div>
          <div class="stat-card glass">
            <div class="stat-num gradient-text">∞</div>
            <div class="stat-label">Cups of coffee</div>
          </div>
        </div>
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
  opacity: 0.35;
}

.section-eyebrow {
  font-family: 'Space Grotesk', sans-serif;
  font-size: 13px;
  font-weight: 600;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  color: #ffaa00;
}

.stats-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 14px;
}
.stat-card {
  padding: 22px 18px;
  text-align: center;
}
.stat-num {
  font-family: 'Space Grotesk', sans-serif;
  font-size: 40px;
  font-weight: 700;
  line-height: 1;
  margin-bottom: 6px;
}
.stat-label {
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.6);
}

.info-row {
  display: flex;
  align-items: flex-start;
  gap: 14px;
  padding: 10px 0;
}
.info-row + .info-row { border-top: 1px solid rgba(255,255,255,0.06); }
.info-label {
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.5);
  margin-bottom: 2px;
}
.info-value {
  font-size: 14px;
  color: rgba(255,255,255,0.9);
}

.panel-number {
  font-family: 'Space Grotesk', sans-serif;
  font-size: 12px;
  font-weight: 700;
  color: #ffaa00;
  letter-spacing: 0.15em;
}

.glass-panels :deep(.v-expansion-panel) {
  border: 1px solid rgba(255,255,255,0.06);
  border-radius: 14px !important;
  margin-bottom: 10px;
  background: rgba(255,255,255,0.02) !important;
  transition: border-color .25s ease, background .25s ease;
}
.glass-panels :deep(.v-expansion-panel:hover) {
  border-color: rgba(255,170,0,0.35);
  background: rgba(255,255,255,0.04) !important;
}
.glass-panels :deep(.v-expansion-panel--active) {
  border-color: rgba(255,170,0,0.5);
}
.glass-panels :deep(.v-expansion-panel__shadow) { display: none; }
.glass-panels :deep(.v-expansion-panel-title) { padding: 16px 20px; }
.glass-panels :deep(.v-expansion-panel-text__wrapper) { padding: 4px 20px 20px 20px; }
</style>
