<template>
  <v-app dark>
    <Drawer/>
    <v-content class="hide-overflow" style="padding-left:300px" id="mainContent">
      <div>
        <Hero/>
        <div class="container py-5 px-0 fluid">
          <About/>
          <Experience/>
          <Skills/>
          <Portfolio/>
          <Contact/>
        </div>
      </div>
    </v-content>
  </v-app>
</template>

<script>
import Drawer from "@/components/Drawer.vue";
import Hero from "@/components/Hero.vue";
import About from "@/components/About.vue";
import Experience from "@/components/Experience.vue";
import Skills from "@/components/Skills.vue";
import Portfolio from "@/components/Portfolio.vue";
import Contact from "@/components/Contact.vue";
export default {
  components: {
    Hero,
    Drawer,
    About,
    Experience,
    Skills,
    Portfolio,
    Contact
  }
};
</script>


<style>
@media screen and (max-width: 960px) {
  #mainContent {
    padding-left: 0 !important;
  }

  #mainDrawer {
    display: none;
  }
}
</style>