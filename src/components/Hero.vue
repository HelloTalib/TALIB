<template>
  <section class="hero">
    <v-img :src="heroImage" cover class="hero-img"></v-img>
    <div class="hero-overlay"></div>

    <div class="hero-content">
      <div class="pa-8 pa-md-12 reveal">
        <div class="text-overline mb-3" style="letter-spacing: 0.4em;">HELLO, I AM</div>
        <h1 class="hero-name">
          <span class="d-block">ABU</span>
          <span class="d-block gradient-text">TALIB</span>
        </h1>
        <div class="hero-tag mt-4">
          <span class="line"></span>
          <span class="text-uppercase">Software Engineer · WebNinja</span>
        </div>

        <div class="d-flex flex-wrap mt-8" style="gap: 14px;">
          <v-btn href="#portfolio" size="large" class="btn-gradient">
            View My Work
            <v-icon end>mdi-arrow-down</v-icon>
          </v-btn>
          <v-btn href="#contact" size="large" variant="outlined" color="white">
            Get In Touch
          </v-btn>
        </div>
      </div>
    </div>

    <a href="#about" class="scroll-cue">
      <span>scroll</span>
      <v-icon size="20">mdi-chevron-double-down</v-icon>
    </a>
  </section>
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

<style scoped>
.hero {
  position: relative;
  height: 100vh;
  min-height: 600px;
  overflow: hidden;
  padding: 0;
}
.hero-img {
  position: absolute !important;
  inset: 0;
  height: 100%;
  width: 100%;
}
.hero-overlay {
  position: absolute;
  inset: 0;
  background:
    linear-gradient(120deg, rgba(11,11,16,0.92) 0%, rgba(11,11,16,0.4) 55%, rgba(11,11,16,0.2) 100%),
    radial-gradient(800px 400px at 0% 100%, rgba(255,170,0,0.18), transparent 70%);
}
.hero-content {
  position: relative;
  z-index: 1;
  height: 100%;
  display: flex;
  align-items: center;
  max-width: 880px;
}
.hero-name {
  font-family: 'Space Grotesk', sans-serif;
  font-weight: 700;
  font-size: clamp(56px, 11vw, 168px);
  line-height: 0.92;
  letter-spacing: -0.04em;
  margin: 0;
}
.hero-tag {
  display: inline-flex;
  align-items: center;
  gap: 14px;
  color: rgba(255,255,255,0.7);
  font-weight: 500;
  letter-spacing: 0.16em;
  font-size: 13px;
}
.hero-tag .line {
  display: inline-block;
  width: 48px;
  height: 2px;
  background: linear-gradient(90deg, #ffaa00, #ff5e62);
}

.scroll-cue {
  position: absolute;
  bottom: 28px;
  left: 50%;
  transform: translateX(-50%);
  display: inline-flex;
  flex-direction: column;
  align-items: center;
  gap: 6px;
  color: rgba(255,255,255,0.6);
  font-size: 11px;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  text-decoration: none;
  animation: float 2.2s ease-in-out infinite;
}
.scroll-cue:hover { color: #ffaa00; }
@keyframes float {
  0%, 100% { transform: translate(-50%, 0); }
  50%      { transform: translate(-50%, 6px); }
}
</style>
