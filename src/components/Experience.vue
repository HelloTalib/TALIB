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
          title: "Senior Software Engineer — BdThemes",
          desc: "Leading Gutenberg product development: shipped ZoloBlocks (5.0 ★, 1,000+ installs) — a full page-builder toolkit, and Instant AI Image Generator (1,000+ installs). Driving architecture decisions across the BdThemes plugin ecosystem.",
          year: "2024–Now",
        },
        {
          title: "Plugin Developer — BdThemes",
          desc: "Developed Live Copy Paste for Elementor — a cross-domain copy-paste & page duplicator now used by 7,000+ WordPress sites (4.3 ★). Added major features to Element Pack: Mega Menu, Context Menu, Dynamic Grid, Horizontal Scroller, cursor effects, and animated backgrounds.",
          year: "2022–2023",
        },
        {
          title: "Software Engineer — BdThemes",
          desc: "Joined BdThemes to build and maintain WordPress plugins. Contributed to Element Pack Lite, Prime Slider, Ultimate Post Kit, and Ultimate Store Kit — collectively installed on hundreds of thousands of WordPress sites worldwide.",
          year: "2021",
        },
        {
          title: "WordPress & Full-Stack Development",
          desc: "Went deep into WordPress core, PHP, and REST APIs. Delivered 30+ themes and custom plugin solutions for clients on Fiverr and Upwork. Work began reaching thousands of daily users on production sites.",
          year: "2019–2020",
        },
        {
          title: "Elementor Addon & Theme Development",
          desc: "Built 20+ custom Elementor widgets and WordPress themes for global clients. Developed WooCommerce stores and delivered full agency websites using Elementor, custom PHP, and advanced CSS animations.",
          year: "2018–2019",
        },
        {
          title: "Front-End & Freelance Beginnings",
          desc: "Started freelancing on Fiverr building pixel-perfect websites with HTML, CSS, SCSS, Vue.js, and Vuetify. Built my first REST API (Node.js + MongoDB + Vue.js) and began learning the full web development stack.",
          year: "2017–2018",
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
