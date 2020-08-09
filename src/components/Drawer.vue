<template>
  <v-navigation-drawer fixed dark app id="mainDrawer">
    <v-layout align-center fill-height py-5 justify-center column>
      <!-- The name typed logo -->
      <!-- Developer name -->
      <h2 class="display-3 font-weight-black primary--text mb-2">TALIB</h2>

      <!--  Designation -->
      <span class="title font-weight-light mb-5">BD WEBNINJA</span>

      <!-- Buttons links -->
      <div v-for="item in navItems" :key="item.title">
        <v-btn
          class="mb-3 text-capitalize subheading font-weight-medium"
          flat
          dark
          :href="item.link"
        >{{ item.title }}</v-btn>
      </div>

      <!-- Social Icons -->
      <div class="mt-auto">
        <!-- Now for each item, we create a new icon -->
        <div class="my-4">
          <a
            class="mx-2"
            v-for="social in socialIcons"
            :title="social.name"
            :key="social.name"
            target="_blank"
            :href="social.link"
          >
            <v-btn icon>
              <v-icon>{{social.icon}}</v-icon>
            </v-btn>
          </a>
        </div>
      </div>
    </v-layout>
  </v-navigation-drawer>
</template>

<script>
export default {
  data() {
    return {
      navItems: [
        { title: "@Hey", link: "#" },
        { title: "About Me", link: "#about" },
        { title: "Experience", link: "#experience" },
        { title: "Skills & Education", link: "#skills" },
        { title: "Portfolio", link: "#portfolio" },
        { title: "Contact", link: "#contact" }
      ],

      socialIcons: [
        {
          name: "Facebook",
          link: "https://www.facebook.com/abutalib4599",
          icon: "mdi-facebook"
        },
        {
          name: "Twitter",
          link: "https://twitter.com/abutalib4599",
          icon: "mdi-twitter"
        },
        {
          name: "Github",
          link: "https://github.com/abutalib4599",
          icon: "mdi-github-circle"
        }
      ]
    };
  }
};
</script>

<style scoped>
#mainDrawer {
  height: 100%;
  margin-top: 0px;
  max-height: calc(100% - 0px);
  transform: translateX(0px) !important;
  width: 300px;
  background-color: #111;
}

a {
  text-decoration: none;
}
</style>


