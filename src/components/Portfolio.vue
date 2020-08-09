<template>
  <section id="portfolio">
    <v-layout pa-5 wrap>
      <v-img
        :src="require('@/assets/abstract-3.png')"
        height="100%"
        width="100%"
        class="abstract-3"
      ></v-img>
      <h2 class="display-2 font-weight-bold primary--text mb-4">What I've Done</h2>
      <v-carousel class="elevation-0" height="600" hide-controls :cycle="true">
        <v-carousel-item v-for="(item,index) in items" :key="index">
          <v-sheet class="transparent pa-5" height="100%">
            <div class="text-xs-center mb-5">
              <h2 class="primary--text title font-weight-light mb-1">Advanced Library Management</h2>
              <span class="subheading">Created for fun</span>
            </div>
            <v-layout wrap>
              <v-flex shrink>
                <div class="mb-3" style="max-width:500px;">
                  <h2 class="primary--text title font-weight-light mb-3">Project Details</h2>
                  <div class="subheading mb-5">{{item.desc}}</div>
                  <h2 class="primary--text title font-weight-light">Project Info</h2>
                  <v-list class="transparent">
                    <v-list-tile>
                      <v-list-tile-action>
                        <v-icon class="primary">mdi-code-tags</v-icon>
                      </v-list-tile-action>
                      <v-list-tile-title class="mr-2">{{item.title}}</v-list-tile-title>
                    </v-list-tile>
                  </v-list>
                  <v-list class="transparent">
                    <v-list-tile>
                      <v-list-tile-action>
                        <v-icon class="primary">mdi-access-point</v-icon>
                      </v-list-tile-action>
                      <v-list-tile-title class="mr-2">
                        <a :href="item.source" target="_blank" class="white--text">
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
                      <v-list-tile-title class="mr-2">{{item.year}}</v-list-tile-title>
                    </v-list-tile>
                  </v-list>
                </div>
              </v-flex>
              <v-flex hidden-sm-and-down>
                <v-img height="350" width="500" contain :src="item.img" class="mx-auto"></v-img>
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
          desc:
            "This is an Online Store Project. Uses WordPress with premium WoodMart Theme. All the product uploaded manually. This was just a project and was coded by me in 7th Grade.",
          title: "Online Store",
          source: "https://shopup.bdwebninja.com/",
          year: "2019",
          img: require("@/assets/portfolio/shopup.png")
        },
        {
          title: "Dashboard",
          desc:
            "A Online Course Learning management system written in Vuejs. Uses Firebase for the database management. All the data is encrypted using BCrypt. This was my first big project and was coded by me in 7th Grade.",
          source: "https://todo-vuejs.netlify.com/",
          year: "2019",
          img: require("@/assets/portfolio/dashboard.png")
        },
{
          title: "SubReddit",
          desc:
            "A subreddit web application. Uses axios for the database management. All the data is encrypted using axios. This was also learning based project with Brad Traversy",
          source: "https://subreddit.netlify.com/",
          year: "2018",
          img: require("@/assets/portfolio/subreddit.png")
        },
        {
          title: "Countries",
          desc:
            "A Project management system written in VueJs. Uses Firebase for the database and Authentication management. All the data is encrypted using Firebase Authentication.",
          source: "https://countries-1.netlify.com/",
          year: "2018",
          img: require("@/assets/portfolio/login.png")
        },

        {
          title: "Smoothies",
          desc:
            "A todo list management system written in Vuejs. Uses firebase for the database management and Authentication. All the data is encrypted using Firebase Authentication. This was a learning based project with net ninja",
          source: "https://smoothies.netlify.com/",

          year: "2017",
          img: require("@/assets/portfolio/3.jpg")
        },
      ]
    };
  }
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

