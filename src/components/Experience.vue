<template>
  <section id="experience">
    <v-layout pa-5 wrap>
      <v-flex xs12>
        <h1 class="display-2 font-weight-bold primary--text mb-4">Down the memory lane</h1>
      </v-flex>
      <v-flex xs12 md9 mx-auto>
        <v-timeline :dense="$vuetify.breakpoint.xsOnly" style="z-index:1 !important;">
          <v-timeline-item v-for="(item,index) in places" :key="index" color="primary" large>
            <template v-slot:opposite>
              <span>{{item.year}}</span>
            </template>
            <v-card class="pa-3">
              <h3 class="subheading font-weight-bold">{{item.title}}</h3>
              <span>{{item.desc}}</span>
            </v-card>
          </v-timeline-item>
        </v-timeline>
      </v-flex>
    </v-layout>
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
section {
  position: relative;
}
</style>
