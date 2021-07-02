<template>
  <section id="portfolio">
    <v-layout pa-5 wrap>
      <v-img
        :src="require('@/assets/abstract-3.png')"
        height="100%"
        width="100%"
        class="abstract-3"
      ></v-img>
      <h2 class="display-2 font-weight-bold primary--text mb-4">
        What I've Done
      </h2>
      <v-carousel class="elevation-0" height="600" hide-controls :cycle="true">
        <v-carousel-item v-for="(item, index) in items" :key="index">
          <v-sheet class="transparent pa-5" height="100%">
            <div class="text-xs-center mb-5">
              <h2 class="primary--text title font-weight-light mb-1">
                Modern  looking html Template
              </h2>
              <span class="subheading">Created for Practice😁</span>
            </div>
            <v-layout wrap>
              <v-flex shrink>
                <div class="mb-3" style="max-width: 500px">
                  <h2 class="primary--text title font-weight-light mb-3">
                    Project Details
                  </h2>
                  <div class="subheading mb-5">{{ item.desc }}</div>
                  <h2 class="primary--text title font-weight-light">
                    Project Info
                  </h2>
                  <v-list class="transparent">
                    <v-list-tile>
                      <v-list-tile-action>
                        <v-icon class="primary">mdi-code-tags</v-icon>
                      </v-list-tile-action>
                      <v-list-tile-title class="mr-2">{{
                        item.title
                      }}</v-list-tile-title>
                    </v-list-tile>
                  </v-list>
                  <v-list class="transparent">
                    <v-list-tile>
                      <v-list-tile-action>
                        <v-icon class="primary">mdi-access-point</v-icon>
                      </v-list-tile-action>
                      <v-list-tile-title class="mr-2">
                        <a
                          :href="item.source"
                          target="_blank"
                          class="white--text"
                        >
                          Live Demo
                          <v-icon>mdi-link-variant</v-icon>
                        </a>
                      </v-list-tile-title>
                    </v-list-tile>
                  </v-list>
                  <v-list class="transparent">
                    <v-list-tile>
                      <v-list-tile-action>
                        <v-icon class="primary">mdi-calendar</v-icon>
                      </v-list-tile-action>
                      <v-list-tile-title class="mr-2">{{
                        item.year
                      }}</v-list-tile-title>
                    </v-list-tile>
                  </v-list>
                </div>
              </v-flex>
              <v-flex hidden-sm-and-down>
                <a :href="item.source">
                  <v-img
                    height="350"
                    width="500"
                    contain
                    :src="item.img"
                    class="mx-auto"
                  ></v-img>
                </a>
              </v-flex>
            </v-layout>
          </v-sheet>
        </v-carousel-item>
      </v-carousel>
    </v-layout>
  </section>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          desc: "This is a Beauty Parlour Website. Uses html, CSS, SASS &; UIKIT Framework to Design this static website. This website is really outstanding to look😍.",
          title: "Parlour Website",
          source: "https://floreence.netlify.app/",
          year: "2019",
          img: require("@/assets/portfolio/demo-florence.png"),
        },
        {
          desc: "This is an Agency Website. Uses html, CSS, SASS &; UIKIT Framework to Design this static website. This was just a project and was coded by me in 7th Grade.",
          title: "Agency Website",
          source: "https://brooklynn.netlify.app/",
          year: "2019",
          img: require("@/assets/portfolio/demo-brooklyn.png"),
        },
        {
          desc: "This is an Online Store Project. Uses html, CSS, SASS &; UIKIT Framework to Design this static website",
          title: "Online Store",
          source: "https://peak-shop.netlify.app/",
          year: "2019",
          img: require("@/assets/portfolio/demo-peak-shop.png"),
        },
        {
          desc: "This is a Non-Profit Organization Website. I use html, CSS, SASS &; UIKIT Framework to Design this static website",
          title: "Non-Profit Website",
          source: "https://oxpitan.netlify.app/",
          year: "2019",
          img: require("@/assets/portfolio/demo-oxpitan.png"),
        },
        {
          desc: "This is My Personal Portfolio Website. I used html, CSS, SASS VueJs, VuetifyJs ect. to develop this awesome looking protfolio website;",
          title: "Portfolio Website",
          source: "https://talib.netlify.app/",
          year: "2019",
          img: require("@/assets/portfolio/personal-portfolio.png"),
        },
        {
          desc: "This is kids wears and accesories Website. I used html, CSS, SASS to develop this website;",
          title: "Kids Website",
          source: "https://babiees.netlify.app/",
          year: "2019",
          img: require("@/assets/portfolio/demo-balou.png"),
        },
        {
          desc: "This is an interior design Website. I used html, CSS, SASS to develop this awesome looking interior website;",
          title: "Interior Website",
          source: "https://yaard.netlify.app/",
          year: "2019",
          img: require("@/assets/portfolio/demo-yard.png"),
        },
        {
          desc: "This is a Handcraft design Website. I used html, CSS, SASS to develop this awesome looking handcraft website;",
          title: "Craft Website",
          source: "https://crafti.netlify.app/",
          year: "2019",
          img: require("@/assets/portfolio/demo-craft.png"),
        },
        {
          desc: "This is a Creative minimal looking Website. I used html, CSS, SASS to develop this awesome looking handcraft website;",
          title: "Creative Website",
          source: "https://creativehub.netlify.app/",
          year: "2019",
          img: require("@/assets/portfolio/demo-creative-hub.png"),
        },
        {
          desc: "This is a Blog Website. I used html, CSS, SASS to develop this awesome looking blog resources website;",
          title: "Blog Website",
          source: "https://designbites.netlify.app/",
          year: "2019",
          img: require("@/assets/portfolio/demo-design-bites.png"),
        },
        // {
        //   title: "Dashboard",
        //   desc:
        //     "A Online Course Learning management system written in Vuejs. Uses Firebase for the database management. All the data is encrypted using BCrypt. This was my first big project and was coded by me in 7th Grade.",
        //   source: "https://tgerodo-vuejs.netlify.app",
        //   year: "2019",
        //   img: require("@/assets/portfolio/dashboard.png")
        // },
        // {
        //   title: "SubReddit",
        //   desc: "A subreddit web application. Uses axios for the database management. All the data is encrypted using axios. This was also learning based project with Brad Traversy",
        //   source: "https://subreddit.netlify.app",
        //   year: "2018",
        //   img: require("@/assets/portfolio/subreddit.png"),
        // },
        // {
        //   title: "Countries",
        //   desc: "A Project management system written in VueJs. Uses Firebase for the database and Authentication management. All the data is encrypted using Firebase Authentication.",
        //   source: "https://countries-1.netlify.app/",
        //   year: "2018",
        //   img: require("@/assets/portfolio/login.png"),
        // },

        // {
        //   title: "Smoothies",
        //   desc: "A todo list management system written in Vuejs. Uses firebase for the database management and Authentication. All the data is encrypted using Firebase Authentication. This was a learning based project with net ninja",
        //   source: "https://smoothies.netlify.com/",

        //   year: "2017",
        //   img: require("@/assets/portfolio/3.jpg"),
        // },
      ],
    };
  },
};
</script>


<style scoped>
section {
  position: relative;
}

.abstract-3 {
  position: absolute !important;
  left: 0;
  right: 0;
  z-index: 0 !important;
}

.abstract-3 ~ * {
  z-index: 1 !important;
}

a {
  text-decoration: none;
}
</style>

