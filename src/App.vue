<template>
  <v-app>
    <Drawer/>
    <v-main class="hide-overflow" id="mainContent">
      <Hero/>
      <v-container fluid class="py-5 px-0">
        <About/>
        <Experience/>
        <Skills/>
        <Portfolio/>
        <Contact/>
      </v-container>
    </v-main>
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
</style>