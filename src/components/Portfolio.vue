<template>
  <section id="portfolio">
    <v-row class="pa-5" no-gutters>
      <v-img
        :src="abstract3"
        height="100%"
        width="100%"
        class="abstract-3"
      ></v-img>
      <h2 class="text-h3 font-weight-bold text-primary mb-4">
        What I've Done
      </h2>
      <v-carousel class="elevation-0" height="600" :show-arrows="false" cycle hide-delimiter-background>
        <v-carousel-item v-for="(item, index) in items" :key="index">
          <v-sheet class="bg-transparent pa-5" height="100%">
            <div class="text-center mb-5">
              <h2 class="text-primary text-h6 font-weight-light mb-1">
                Modern  looking html Template
              </h2>
              <span class="text-subtitle-1">Created for Practice😁</span>
            </div>
            <v-row no-gutters>
              <v-col cols="auto">
                <div class="mb-3" style="max-width: 500px">
                  <h2 class="text-primary text-h6 font-weight-light mb-3">
                    Project Details
                  </h2>
                  <div class="text-subtitle-1 mb-5">{{ item.desc }}</div>
                  <h2 class="text-primary text-h6 font-weight-light">
                    Project Info
                  </h2>
                  <v-list class="bg-transparent" density="compact">
                    <v-list-item>
                      <template v-slot:prepend>
                        <v-icon color="primary">mdi-code-tags</v-icon>
                      </template>
                      <v-list-item-title class="mr-2">{{ item.title }}</v-list-item-title>
                    </v-list-item>
                    <v-list-item>
                      <template v-slot:prepend>
                        <v-icon color="primary">mdi-access-point</v-icon>
                      </template>
                      <v-list-item-title class="mr-2">
                        <a
                          :href="item.source"
                          target="_blank"
                          class="text-white"
                        >
                          Live Demo
                          <v-icon>mdi-link-variant</v-icon>
                        </a>
                      </v-list-item-title>
                    </v-list-item>
                    <v-list-item>
                      <template v-slot:prepend>
                        <v-icon color="primary">mdi-calendar</v-icon>
                      </template>
                      <v-list-item-title class="mr-2">{{ item.year }}</v-list-item-title>
                    </v-list-item>
                  </v-list>
                </div>
              </v-col>
              <v-col class="d-none d-md-flex">
                <a :href="item.source">
                  <v-img
                    height="350"
                    width="500"
                    contain
                    :src="item.img"
                    class="mx-auto"
                  ></v-img>
                </a>
              </v-col>
            </v-row>
          </v-sheet>
        </v-carousel-item>
      </v-carousel>
    </v-row>
  </section>
</template>

<script>
import abstract3 from "@/assets/abstract-3.png";
import demoFlorence from "@/assets/portfolio/demo-florence.png";
import demoBrooklyn from "@/assets/portfolio/demo-brooklyn.png";
import demoPeakShop from "@/assets/portfolio/demo-peak-shop.png";
import demoOxpitan from "@/assets/portfolio/demo-oxpitan.png";
import personalPortfolio from "@/assets/portfolio/personal-portfolio.png";
import demoBalou from "@/assets/portfolio/demo-balou.png";
import demoYard from "@/assets/portfolio/demo-yard.png";
import demoCraft from "@/assets/portfolio/demo-craft.png";
import demoCreativeHub from "@/assets/portfolio/demo-creative-hub.png";
import demoDesignBites from "@/assets/portfolio/demo-design-bites.png";

export default {
  data() {
    return {
      abstract3,
      items: [
        {
          desc: "This is a Beauty Parlour Website. Uses html, CSS, SASS &; UIKIT Framework to Design this static website. This website is really outstanding to look😍.",
          title: "Parlour Website",
          source: "https://floreence.netlify.app/",
          year: "2019",
          img: demoFlorence,
        },
        {
          desc: "This is an Agency Website. Uses html, CSS, SASS &; UIKIT Framework to Design this static website. This was just a project and was coded by me in 7th Grade.",
          title: "Agency Website",
          source: "https://brooklynn.netlify.app/",
          year: "2019",
          img: demoBrooklyn,
        },
        {
          desc: "This is an Online Store Project. Uses html, CSS, SASS &; UIKIT Framework to Design this static website",
          title: "Online Store",
          source: "https://peak-shop.netlify.app/",
          year: "2019",
          img: demoPeakShop,
        },
        {
          desc: "This is a Non-Profit Organization Website. I use html, CSS, SASS &; UIKIT Framework to Design this static website",
          title: "Non-Profit Website",
          source: "https://oxpitan.netlify.app/",
          year: "2019",
          img: demoOxpitan,
        },
        {
          desc: "This is My Personal Portfolio Website. I used html, CSS, SASS VueJs, VuetifyJs ect. to develop this awesome looking protfolio website;",
          title: "Portfolio Website",
          source: "https://talib.netlify.app/",
          year: "2019",
          img: personalPortfolio,
        },
        {
          desc: "This is kids wears and accesories Website. I used html, CSS, SASS to develop this website;",
          title: "Kids Website",
          source: "https://babiees.netlify.app/",
          year: "2019",
          img: demoBalou,
        },
        {
          desc: "This is an interior design Website. I used html, CSS, SASS to develop this awesome looking interior website;",
          title: "Interior Website",
          source: "https://yaard.netlify.app/",
          year: "2019",
          img: demoYard,
        },
        {
          desc: "This is a Handcraft design Website. I used html, CSS, SASS to develop this awesome looking handcraft website;",
          title: "Craft Website",
          source: "https://crafti.netlify.app/",
          year: "2019",
          img: demoCraft,
        },
        {
          desc: "This is a Creative minimal looking Website. I used html, CSS, SASS to develop this awesome looking handcraft website;",
          title: "Creative Website",
          source: "https://creativehub.netlify.app/",
          year: "2019",
          img: demoCreativeHub,
        },
        {
          desc: "This is a Blog Website. I used html, CSS, SASS to develop this awesome looking blog resources website;",
          title: "Blog Website",
          source: "https://designbites.netlify.app/",
          year: "2019",
          img: demoDesignBites,
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

