<template>
  <v-navigation-drawer fixed dark app id="mainDrawer">
    <v-layout align-center fill-height py-5 justify-center column>
      <!-- The name typed logo -->
      <!-- Developer name -->
      <h2 class="display-3 font-weight-black primary--text mb-2">TALIB</h2>

      <!--  Designation -->
      <span class="title font-weight-light mb-5">WEBNINJA</span>

      <!-- Buttons links -->
      <div v-for="item in navItems" :key="item.title">
        <v-btn
          class="mb-3 text-capitalize subheading font-weight-medium"
          flat
          dark
          :href="item.link"
          >{{ item.title }}</v-btn
        >
      </div>

      <!-- Social Icons -->
      <div class="mt-auto">
        <!-- Now for each item, we create a new icon -->
        <div class="my-4">
          <a
            class="mx-1"
            v-for="social in socialIcons"
            :title="social.name"
            :key="social.name"
            target="_blank"
            :href="social.link"
          >
            <v-btn icon>
              <v-icon>{{ social.icon }}</v-icon>
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
        { title: "Education & Skills", link: "#skills" },
        { title: "Portfolio", link: "#portfolio" },
        { title: "Contact", link: "#contact" },
      ],

      socialIcons: [
        {
          name: "WordPress",
          link: "https://profiles.wordpress.org/abutalib/",
          icon: "mdi-wordpress",
        },
        {
          name: "Github",
          link: "https://github.com/abutalib4599",
          icon: "mdi-github-circle",
        },
        {
          name: "Upwork",
          link: "https://www.upwork.com/workwith/abutalib4599/",
          icon: "icon-upwork",
        },
      ],
    };
  },
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

@font-face {
  font-family: "icomoon";
  src: url("../assets/fonts/icomoon.eot?ezeop7");
  src: url("../assets/fonts/icomoon.eot?ezeop7#iefix")
      format("embedded-opentype"),
    url("../assets/fonts/icomoon.ttf?ezeop7") format("truetype"),
    url("../assets/fonts/icomoon.woff?ezeop7") format("woff"),
    url("../assets/fonts/icomoon.svg?ezeop7#icomoon") format("svg");
  font-weight: normal;
  font-style: normal;
  font-display: block;
}

[class^="icon-"],
[class*=" icon-"] {
  /* use !important to prevent issues with browser extensions that change fonts */
  font-family: "icomoon" !important;
  speak: never;
  font-style: normal;
  font-weight: normal;
  font-variant: normal;
  text-transform: none;
  line-height: 1;
  font-size: 16px;
  /* border: 1px solid rgba(255, 255, 255, 0.75); */
  border-radius: 50%;
  padding: 3px;
  background: #fff;

  /* Better Font Rendering =========== */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.icon-upwork:before {
  content: "\e900";
  color: #333;
}
</style>


