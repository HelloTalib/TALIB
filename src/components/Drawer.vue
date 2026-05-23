<template>
  <v-navigation-drawer
    v-model="drawerOpen"
    :permanent="$vuetify.display.mdAndUp"
    :temporary="$vuetify.display.smAndDown"
    theme="dark"
    id="mainDrawer"
    width="300"
    color="#111"
  >
    <div class="drawer-inner d-flex flex-column align-center fill-height py-8 text-center">
      <!-- Developer name -->
      <h2 class="text-h2 font-weight-black gradient-text mb-1">TALIB</h2>

      <!--  Designation -->
      <span class="text-subtitle-2 font-weight-medium text-medium-emphasis mb-2" style="letter-spacing: 0.4em;">WEBNINJA</span>

      <!-- Accent bar -->
      <div class="accent-bar mb-8"></div>

      <!-- Buttons links -->
      <nav class="d-flex flex-column align-center" style="gap: 6px;">
        <a
          v-for="item in navItems"
          :key="item.title"
          :href="item.link"
          class="nav-link"
        >
          <span class="dot"></span>
          {{ item.title }}
        </a>
      </nav>

      <!-- Social Icons -->
      <div class="mt-auto pt-8">
        <div class="d-flex justify-center" style="gap: 4px;">
          <a
            v-for="social in socialIcons"
            :title="social.name"
            :key="social.name"
            target="_blank"
            :href="social.link"
            class="social-link"
          >
            <v-icon size="22">{{ social.icon }}</v-icon>
          </a>
        </div>
        <div class="text-caption text-medium-emphasis mt-4">© {{ new Date().getFullYear() }} Abu Talib</div>
      </div>
    </div>
  </v-navigation-drawer>
</template>

<script>
export default {
  data() {
    return {
      drawerOpen: true,
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
          link: "https://github.com/hellotalib",
          icon: "mdi-github",
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
a {
  text-decoration: none;
}

.drawer-inner {
  background: linear-gradient(180deg, #0e0e14 0%, #08080c 100%);
  border-right: 1px solid rgba(255,255,255,0.06);
  position: relative;
}
.drawer-inner::before {
  content: "";
  position: absolute;
  inset: 0;
  background:
    radial-gradient(400px 200px at 50% 0%, rgba(255,170,0,0.18), transparent 70%),
    radial-gradient(300px 200px at 50% 100%, rgba(255,94,98,0.12), transparent 70%);
  pointer-events: none;
}

.accent-bar {
  width: 56px;
  height: 3px;
  border-radius: 3px;
  background: linear-gradient(90deg, #ffaa00, #ff5e62);
}

.nav-link {
  position: relative;
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 8px 18px;
  border-radius: 10px;
  color: rgba(255,255,255,0.7);
  font-family: 'Space Grotesk', sans-serif;
  font-weight: 500;
  font-size: 14px;
  letter-spacing: 0.04em;
  transition: color .25s ease, background .25s ease, transform .25s ease;
}
.nav-link .dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: rgba(255,255,255,0.2);
  transition: background .25s ease, box-shadow .25s ease, transform .25s ease;
}
.nav-link:hover {
  color: #fff;
  background: rgba(255,255,255,0.04);
  transform: translateX(4px);
}
.nav-link:hover .dot {
  background: linear-gradient(135deg, #ffaa00, #ff5e62);
  box-shadow: 0 0 12px rgba(255,170,0,0.6);
  transform: scale(1.4);
}

.social-link {
  width: 38px;
  height: 38px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  color: rgba(255,255,255,0.7);
  border: 1px solid rgba(255,255,255,0.08);
  transition: all .25s ease;
}
.social-link:hover {
  color: #ffaa00;
  border-color: rgba(255,170,0,0.5);
  transform: translateY(-2px);
  box-shadow: 0 6px 16px rgba(255,170,0,0.25);
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


