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
          title: "Year 2021 and forward",
          desc:
            "I got a job as a Software Engineer ‍at BdThemes. Here, My Primary work is Contribute to Develop WordPress Plugins/Elementor Addons",
          year: "2021",
        },
        {
          title: "Year 2020 and forward",
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
