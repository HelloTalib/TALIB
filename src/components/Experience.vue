<template>
  <section id="experience">
    <div class="section-wrap">
      <div class="fade-up">
        <div class="section-eyebrow">03 — Journey</div>
        <h2 class="section-heading">Down the <span class="gradient-text">memory lane.</span></h2>
      </div>

      <div class="timeline">
        <div
          v-for="(item, index) in places"
          :key="index"
          class="timeline-entry fade-up"
          :class="'delay-' + Math.min(index + 1, 5)"
        >
          <!-- Accent dot + vertical line handled by CSS -->
          <div class="timeline-marker" aria-hidden="true">
            <span class="marker-dot"></span>
          </div>

          <div class="timeline-body">
            <div class="timeline-year">{{ item.year }}</div>
            <div class="timeline-card hover-lift">
              <h3 class="entry-title">{{ item.title }}</h3>
              <p class="entry-desc">{{ item.desc }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      places: [
        {
          title: "Year 2023 and forward!",
          desc:
            "As a Software Engineer of BDTHEMES, I'm contribute to Develop bdthemes all products such as ElementPack, PrimeSlider, Ultimate Post kit, Ultimate Store Kit, Live Copy Paste plugins and trying to switch new technology..",
          year: "2023",
        },
        {
          title: "Year 2022",
          desc:
            "As a Software Engineer of BDTHEMES, I'm contribute to Develop bdthemes all products. especially ElementPack. I have added more stunning features for example Mega Menu, Live Copy Paste, Context Menu, Dynamic Grid/Carousel, Horizontal Scroller, tile scroll, animated background, cursor effects, reveal effects and so on..😊",
          year: "2022",
        },
        {
          title: "Year 2021",
          desc:
            "I got a job as a Software Engineer ‍of BdThemes. Here my primary task is Contribute to Develop WordPress Plugins/Elementor Addons",
          year: "2021",
        },
        {
          title: "Mastering WordPress and Practice...",
          desc:
            "Entered mainstream development and I almost write code daily till date. Some of my works are used by thousands of people on a daily basis. Check my GitHub repo.",
          year: "2020",
        },
        {
          title: "Elementor Addons Development",
          desc:
            "Created 20+ elementor widget just for practice purpose. have not services this category any marketplace yet.",
          year: "2019",
        },
        {
          title: "WordPress Theme Development",
          desc:
            "I Developed 30+ WordPress theme for my clients on the online marketplace such as fiverr, upwork, etc.",
          year: "2019",
        },
        {
          title: "WordPress Theme Customization",
          desc:
            "Created Agency Website for my first Client on upwork marketplace. I was using WordPress and Elementor with some awesome WP Plugins for completed these project.",
          year: "2018",
        },
        {
          title: "Created own API",
          desc:
            "Created my first REST API for my own BLOG website. for Front End, I used html5, css3, Vuejs with Vuetify Library. and for Back-End, I used Node Api with MongoDB",
          year: "2017",
        },
        {
          title: "Front-End Development",
          desc:
            "My first Job At Fiverr, I created modern website for my client using html, css, scss, VueJs and VuetifyJs. yeah! Client was fully satisfied.",
          year: "2017",
        },
      ],
    };
  },
};
</script>

<style scoped>
section { position: relative; }

.section-heading {
  font-size: clamp(32px, 4vw, 52px);
  font-weight: 700;
  line-height: 1.1;
  margin-bottom: 64px;
}

/* ── Timeline shell ── */
.timeline {
  position: relative;
  padding-left: 32px;
  max-width: 760px;
}
.timeline::before {
  content: '';
  position: absolute;
  left: 6px;
  top: 8px;
  bottom: 0;
  width: 1px;
  background: linear-gradient(
    to bottom,
    var(--color-accent-border) 0%,
    transparent 100%
  );
}

/* ── Entry ── */
.timeline-entry {
  position: relative;
  display: flex;
  gap: 24px;
  padding-bottom: 36px;
}
.timeline-entry:last-child { padding-bottom: 0; }

/* ── Marker ── */
.timeline-marker {
  position: absolute;
  left: -32px;
  top: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 14px;
  height: 14px;
}
.marker-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: var(--color-accent);
  box-shadow: 0 0 0 3px rgba(110, 231, 183, 0.18), 0 0 12px rgba(110, 231, 183, 0.35);
  flex-shrink: 0;
}

/* ── Body ── */
.timeline-body {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 10px;
}
.timeline-year {
  display: inline-block;
  font-family: var(--font-mono);
  font-size: 11px;
  font-weight: 500;
  letter-spacing: 0.18em;
  color: var(--color-accent);
  background: var(--color-accent-dim);
  border: 1px solid var(--color-accent-border);
  padding: 4px 12px;
  border-radius: 999px;
  width: fit-content;
}

/* ── Card ── */
.timeline-card {
  padding: 20px 24px;
  background: rgba(255, 255, 255, 0.025);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-md);
}
.entry-title {
  font-family: var(--font-display);
  font-size: 17px;
  font-weight: 600;
  margin-bottom: 10px;
  color: var(--color-text);
}
.entry-desc {
  font-size: 14px;
  line-height: 1.7;
  color: var(--color-muted);
  margin: 0;
}

/* ── Responsive ── */
@media (max-width: 640px) {
  .timeline { padding-left: 24px; }
  .timeline-marker { left: -24px; }
  .section-heading { margin-bottom: 40px; }
}
</style>
