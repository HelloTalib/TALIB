<template>
  <section id="experience">
    <v-row class="pa-5" no-gutters>
      <v-col cols="12" class="mb-8">
        <div class="section-eyebrow mb-2">03 — Journey</div>
        <h2 class="text-h2 font-weight-bold">Down the <span class="gradient-text">memory lane.</span></h2>
      </v-col>
      <v-col cols="12" md="10" class="mx-auto">
        <v-timeline
          :side="$vuetify.display.smAndDown ? 'end' : undefined"
          :density="$vuetify.display.smAndDown ? 'compact' : 'default'"
          line-color="rgba(255,170,0,0.25)"
        >
          <v-timeline-item
            v-for="(item,index) in places"
            :key="index"
            dot-color="primary"
            size="small"
            fill-dot
          >
            <template v-slot:opposite>
              <div class="year-badge">{{ item.year }}</div>
            </template>
            <div class="timeline-card hover-lift">
              <h3 class="text-h6 font-weight-semibold mb-2">{{ item.title }}</h3>
              <p class="text-body-2 text-medium-emphasis mb-0">{{ item.desc }}</p>
            </div>
          </v-timeline-item>
        </v-timeline>
      </v-col>
    </v-row>
  </section>
</template>

<script>
export default {
  data() {
    return {
      places: [
        {
          title: "Year 2023 and forward!",
          desc:
            "As a Software Engineer of BDTHEMES, I'm contribute to Develop bdthemes all products such as ElementPack, PrimeSlider, Ultimate Post kit, Ultimate Store Kit, Live Copy Paste plugins and trying to switch new technology..",
          year: "2023",
        },
        {
          title: "Year 2022",
          desc:
            "As a Software Engineer of BDTHEMES, I'm contribute to Develop bdthemes all products. especially ElementPack. I have added more stunning features for example Mega Menu, Live Copy Paste, Context Menu, Dynamic Grid/Carousel, Horizontal Scroller, tile scroll, animated background, cursor effects, reveal effects and so on..😊",
          year: "2022",
        },
        {
          title: "Year 2021",
          desc:
            "I got a job as a Software Engineer ‍of BdThemes. Here my primary task is Contribute to Develop WordPress Plugins/Elementor Addons",
          year: "2021",
        },
        {
          title: "Mastering WordPress and Practice...",
          desc:
            "Entered mainstream development and I almost write code daily till date. Some of my works are used by thousands of people on a daily basis. Check my GitHub repo.",
          year: "2020",
        },
        {
          title: "Elementor Addons Development",
          desc:
            "Created 20+ elementor widget just for practice purpose. have not services this category any marketplace yet.",
          year: "2019",
        },
        {
          title: "WordPress Theme Development",
          desc:
            "I Developed 30+ WordPress theme for my clients on the online marketplace such as fiverr, upwork, etc.",
          year: "2019",
        },
        {
          title: "WordPress Theme Customization",
          desc:
            "Created Agency Website for my first Client on upwork marketplace. I was using WordPress and Elementor with some awesome WP Plugins for completed these project.",
          year: "2018",
        },
        {
          title: "Created own API",
          desc:
            "Created my first REST API for my own BLOG website. for Front End, I used html5, css3, Vuejs with Vuetify Library. and for Back-End, I used Node Api with MongoDB",
          year: "2017",
        },
        {
          title: "Front-End Development",
          desc:
            "My first Job At Fiverr, I created modern website for my client using html, css, scss, VueJs and VuetifyJs. yeah! Client was fully satisfied.",
          year: "2017",
        },
      ],
    };
  },
};
</script>

<style scoped>
section { position: relative; }

.section-eyebrow {
  font-family: 'Space Grotesk', sans-serif;
  font-size: 13px;
  font-weight: 600;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  color: #ffaa00;
}

.year-badge {
  display: inline-block;
  padding: 6px 14px;
  border-radius: 999px;
  font-family: 'Space Grotesk', sans-serif;
  font-weight: 600;
  font-size: 13px;
  color: #ffaa00;
  background: rgba(255,170,0,0.08);
  border: 1px solid rgba(255,170,0,0.25);
}

.timeline-card {
  padding: 18px 20px;
  background: rgba(255,255,255,0.03);
  border: 1px solid rgba(255,255,255,0.06);
  border-radius: 14px;
  backdrop-filter: blur(8px);
}
</style>
