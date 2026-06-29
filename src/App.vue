<template>
  <v-app>
    <div class="grain-overlay" aria-hidden="true"></div>
    <!-- Custom cursor (outer = JS position, inner = visual + hover transition) -->
    <div class="cursor-dot" ref="cursorDot" aria-hidden="true">
      <div class="cursor-dot-inner"></div>
    </div>
    <div class="cursor-ring" ref="cursorRing" aria-hidden="true">
      <div class="cursor-ring-inner"></div>
    </div>
    <!-- Scroll progress bar -->
    <div class="scroll-progress" :style="{ width: scrollPct + '%' }" aria-hidden="true"></div>
    <Drawer />
    <v-main id="mainContent">
      <Hero />
      <About />
      <Experience />
      <Skills />
      <Portfolio />
      <Contact />
      <footer class="site-footer">
        <div class="footer-inner">
          <span>Abu Talib &nbsp;·&nbsp; {{ year }} &nbsp;·&nbsp; Built with Vue.js</span>
        </div>
      </footer>
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
  components: { Hero, Drawer, About, Experience, Skills, Portfolio, Contact },
  data() {
    return {
      year: new Date().getFullYear(),
      scrollPct: 0,
      cursorMX: -200, cursorMY: -200,
      ringX: -200, ringY: -200,
      rafId: null,
    };
  },
  mounted() {
    this.$nextTick(() => {
      // Fade-up observer
      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              entry.target.classList.add("is-visible");
              observer.unobserve(entry.target);
            }
          });
        },
        { threshold: 0.12 }
      );
      document.querySelectorAll(".fade-up").forEach((el) => observer.observe(el));

      // Scroll progress
      window.addEventListener("scroll", this.onScrollHandler, { passive: true });

      // Custom cursor (desktop only)
      if (window.matchMedia("(pointer: fine)").matches) {
        this.initCursor();
      }
    });
  },
  beforeUnmount() {
    window.removeEventListener("scroll", this.onScrollHandler);
    if (this.mouseMoveBound) window.removeEventListener("mousemove", this.mouseMoveBound);
    if (this.mouseOverBound) document.removeEventListener("mouseover", this.mouseOverBound);
    cancelAnimationFrame(this.rafId);
    document.documentElement.classList.remove("custom-cursor");
  },
  methods: {
    onScrollHandler() {
      const el = document.documentElement;
      const pct = (el.scrollTop / (el.scrollHeight - el.clientHeight)) * 100;
      this.scrollPct = Math.min(pct, 100);
    },
    initCursor() {
      document.documentElement.classList.add("custom-cursor");
      const dot  = this.$refs.cursorDot;
      const ring = this.$refs.cursorRing;
      if (!dot || !ring) return;

      // Instant dot follow
      this.mouseMoveBound = (e) => {
        this.cursorMX = e.clientX;
        this.cursorMY = e.clientY;
        dot.style.transform = `translate(${e.clientX}px, ${e.clientY}px)`;
      };
      window.addEventListener("mousemove", this.mouseMoveBound, { passive: true });

      // Hover state (inner element handles visual transition)
      this.mouseOverBound = (e) => {
        const over = e.target.closest("a, button, input, textarea, select, [role='button'], [tabindex='0']");
        dot.classList.toggle("is-hover", !!over);
        ring.classList.toggle("is-hover", !!over);
      };
      document.addEventListener("mouseover", this.mouseOverBound, { passive: true });

      // Lagged ring follow
      const animateRing = () => {
        this.ringX += (this.cursorMX - this.ringX) * 0.11;
        this.ringY += (this.cursorMY - this.ringY) * 0.11;
        ring.style.transform = `translate(${this.ringX}px, ${this.ringY}px)`;
        this.rafId = requestAnimationFrame(animateRing);
      };
      animateRing();
    }
  }
};
</script>

<style>
/* ── Custom Cursor ── */
/* Outer wrapper: JS controls transform for position only */
.cursor-dot,
.cursor-ring {
  position: fixed;
  top: 0; left: 0;
  pointer-events: none;
  z-index: 10000;
  will-change: transform;
}
.cursor-ring { z-index: 9999; }

/* Inner visual element: CSS transitions only for appearance */
.cursor-dot-inner {
  width: 7px;
  height: 7px;
  background: var(--color-accent);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  transition: width 0.18s ease, height 0.18s ease, background 0.18s ease;
}
.cursor-ring-inner {
  width: 32px;
  height: 32px;
  border: 1.5px solid rgba(110, 231, 183, 0.55);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  transition: width 0.28s ease, height 0.28s ease, border-color 0.28s ease;
}

/* Hover states act on inner elements */
.cursor-dot.is-hover  .cursor-dot-inner  { width: 14px; height: 14px; background: #fff; }
.cursor-ring.is-hover .cursor-ring-inner { width: 50px;  height: 50px;  border-color: rgba(110,231,183,0.2); }

.custom-cursor,
.custom-cursor * { cursor: none !important; }
/* Ensure Vuetify form inputs also hide cursor */
.custom-cursor .v-field *,
.custom-cursor .v-input * { cursor: none !important; }

/* ── Scroll Progress Bar ── */
.scroll-progress {
  position: fixed;
  top: 0; left: 0;
  height: 2px;
  background: var(--color-accent);
  z-index: 10001;
  transition: width 0.1s linear;
  box-shadow: 0 0 8px rgba(110,231,183,0.6);
  pointer-events: none;
}

.grain-overlay {
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 9000;
  opacity: 0.045;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
  background-size: 200px 200px;
}

.site-footer {
  border-top: 1px solid var(--color-border);
  padding: 28px 48px;
}
.footer-inner {
  max-width: 1200px;
  margin: 0 auto;
  font-family: var(--font-mono);
  font-size: 12px;
  letter-spacing: 0.06em;
  color: var(--color-muted);
  text-align: center;
}

@media (max-width: 640px) {
  .site-footer { padding: 24px 16px; }
}
</style>