<template>
  <v-img :src="heroImage" cover style="height:100vh">
    <div class="d-flex fill-height justify-end align-end pa-5 text-right">
      <div>
        <div class="text-uppercase text-h3">ABU TALIB</div>
        <h1 class="text-primary text-uppercase text-h5">Software Engineer</h1>
      </div>
    </div>
  </v-img>
</template>

<script>
import heroImage from "@/assets/hero.jpg";

export default {
  data() {
    return {
      heroImage
    };
  }
};
</script>

<style>
</style>
