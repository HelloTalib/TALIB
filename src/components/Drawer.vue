<template>
  <header :class="['site-nav', { 'nav-scrolled': isScrolled }]" role="banner">
    <!-- Logo -->
    <a href="#" class="nav-logo" aria-label="Abu Talib – Home">
      <span class="logo-name">TALIB</span>
      <span class="logo-dot" aria-hidden="true"></span>
    </a>

    <!-- Desktop nav links -->
    <nav class="nav-links" aria-label="Primary navigation">
      <a
        v-for="item in navItems.slice(1)"
        :key="item.title"
        :href="item.link"
        class="nav-link"
        :class="{ 'nav-link--active': activeSection === item.link.replace('#','') }"
      >{{ item.title }}</a>
    </nav>

    <!-- Desktop social links -->
    <div class="nav-socials" aria-label="Social links">
      <a
        v-for="social in socialIcons"
        :key="social.name"
        :href="social.link"
        :title="social.name"
        target="_blank"
        rel="noopener noreferrer"
        class="nav-social-link"
      >
        <svg v-if="social.name === 'Github'" width="18" height="18" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
          <path d="M12 0C5.374 0 0 5.373 0 12c0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23A11.509 11.509 0 0112 5.803c1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576C20.566 21.797 24 17.3 24 12c0-6.627-5.373-12-12-12z"/>
        </svg>
        <svg v-else-if="social.name === 'WordPress'" width="18" height="18" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
          <path d="M12 0C5.371 0 0 5.371 0 12s5.371 12 12 12 12-5.371 12-12S18.629 0 12 0zM1.421 12c0-1.973.47-3.837 1.3-5.491L7.63 21.01A10.595 10.595 0 011.421 12zm10.579 10.58a10.6 10.6 0 01-3.02-.44l3.208-9.317 3.286 9.001a.894.894 0 00.069.13 10.607 10.607 0 01-3.543.626zm1.455-15.629c.635-.033 1.207-.1 1.207-.1.569-.067.502-.903-.067-.869 0 0-1.707.134-2.81.134-1.037 0-2.778-.134-2.778-.134-.569-.034-.636.835-.066.869 0 0 .538.067 1.107.1l1.644 4.505-2.311 6.928-3.843-11.433c.635-.033 1.207-.1 1.207-.1.568-.067.502-.903-.067-.869 0 0-1.706.134-2.81.134a10.594 10.594 0 017.386-3.033c1.932 0 3.735.522 5.277 1.43-.034 0-.067-.006-.1-.006-1.038 0-1.774.904-1.774 1.874 0 .87.502 1.607 1.038 2.477.402.703.87 1.607.87 2.912 0 .904-.347 1.953-.803 3.426l-1.05 3.509-3.812-11.344zm4.9 14.404l3.263-9.431c.609-1.523.811-2.744.811-3.831 0-.393-.027-.759-.075-1.106A10.564 10.564 0 0122.578 12c0 4.093-2.207 7.678-5.223 9.455z"/>
        </svg>
        <span v-else class="social-text">{{ social.name }}</span>
      </a>
    </div>

    <!-- Hamburger button (mobile) -->
    <button
      class="hamburger"
      :class="{ 'is-open': drawerOpen }"
      @click="drawerOpen = !drawerOpen"
      :aria-expanded="drawerOpen"
      aria-label="Toggle navigation menu"
    >
      <span></span>
      <span></span>
      <span></span>
    </button>

    <!-- Mobile fullscreen overlay -->
    <div class="mobile-overlay" :class="{ 'is-open': drawerOpen }" aria-hidden="!drawerOpen">
      <nav class="mobile-nav" aria-label="Mobile navigation">
        <a
          v-for="(item, i) in navItems"
          :key="item.title"
          :href="item.link"
          class="mobile-nav-link"
          :class="{ 'mobile-link--active': activeSection === item.link.replace('#','') }"
          :style="{ transitionDelay: drawerOpen ? (i * 0.07 + 0.1) + 's' : '0s' }"
          @click="drawerOpen = false"
        >{{ item.title }}</a>
      </nav>
      <div class="mobile-footer">
        <a
          v-for="social in socialIcons"
          :key="social.name"
          :href="social.link"
          :title="social.name"
          target="_blank"
          rel="noopener noreferrer"
          class="mobile-social"
          @click="drawerOpen = false"
        >{{ social.name }}</a>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      drawerOpen: false,
      isScrolled: false,
      activeSection: '',
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
  mounted() {
    window.addEventListener("scroll", this.handleScroll, { passive: true });
    this.$nextTick(() => this.initSectionObserver());
  },
  beforeUnmount() {
    window.removeEventListener("scroll", this.handleScroll);
    if (this.sectionObserver) this.sectionObserver.disconnect();
  },
  methods: {
    handleScroll() {
      this.isScrolled = window.scrollY > 24;
    },
    initSectionObserver() {
      const sections = document.querySelectorAll('section[id]');
      if (!sections.length) return;
      this.sectionObserver = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) this.activeSection = entry.target.id;
          });
        },
        { rootMargin: '-40% 0px -55% 0px' }
      );
      sections.forEach(s => this.sectionObserver.observe(s));
    },
  },
};
</script>

<style scoped>
a { text-decoration: none; }

/* ── Nav Shell ── */
.site-nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  height: var(--nav-height);
  display: flex;
  align-items: center;
  padding: 0 48px;
  gap: 40px;
  transition: background 0.35s ease, backdrop-filter 0.35s ease, border-color 0.35s ease;
  border-bottom: 1px solid transparent;
}
.site-nav.nav-scrolled {
  background: rgba(10, 10, 15, 0.82);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border-bottom-color: var(--color-border);
}

/* ── Logo ── */
.nav-logo {
  display: flex;
  align-items: center;
  gap: 6px;
  margin-right: auto;
}
.logo-name {
  font-family: var(--font-display);
  font-weight: 800;
  font-size: 20px;
  letter-spacing: 0.08em;
  color: var(--color-text);
  transition: color var(--transition-base);
}
.nav-logo:hover .logo-name { color: var(--color-accent); }
.logo-dot {
  width: 7px;
  height: 7px;
  border-radius: 50%;
  background: var(--color-accent);
  box-shadow: 0 0 10px var(--color-accent);
}

/* ── Desktop Nav Links ── */
.nav-links {
  display: flex;
  align-items: center;
  gap: 8px;
}
.nav-link {
  position: relative;
  padding: 6px 12px;
  font-size: 14px;
  font-weight: 500;
  color: var(--color-muted);
  letter-spacing: 0.01em;
  transition: color var(--transition-base);
}
.nav-link::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 12px;
  width: 0;
  height: 1px;
  background: var(--color-accent);
  transition: width 0.25s ease;
}
.nav-link:hover,
.nav-link--active {
  color: var(--color-text);
}
.nav-link:hover::after,
.nav-link--active::after { width: calc(100% - 24px); }
.nav-link--active { color: var(--color-accent) !important; }

/* ── Desktop Social Links ── */
.nav-socials {
  display: flex;
  align-items: center;
  gap: 4px;
}
.nav-social-link {
  width: 36px;
  height: 36px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  color: var(--color-muted);
  border: 1px solid var(--color-border);
  transition: color var(--transition-base), border-color var(--transition-base), transform var(--transition-base);
}
.nav-social-link:hover {
  color: var(--color-accent);
  border-color: var(--color-accent-border);
  transform: translateY(-2px);
}
.social-text {
  font-size: 10px;
  font-weight: 600;
  letter-spacing: 0.05em;
}

/* ── Hamburger ── */
.hamburger {
  display: none;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 5px;
  width: 40px;
  height: 40px;
  background: none;
  border: 1px solid var(--color-border);
  border-radius: var(--radius-sm);
  cursor: pointer;
  padding: 8px;
  transition: border-color var(--transition-base);
}
.hamburger:hover { border-color: var(--color-accent-border); }
.hamburger span {
  display: block;
  width: 20px;
  height: 1.5px;
  background: var(--color-text);
  border-radius: 2px;
  transition: transform 0.3s ease, opacity 0.3s ease;
  transform-origin: center;
}
.hamburger.is-open span:nth-child(1) { transform: translateY(6.5px) rotate(45deg); }
.hamburger.is-open span:nth-child(2) { opacity: 0; transform: scaleX(0); }
.hamburger.is-open span:nth-child(3) { transform: translateY(-6.5px) rotate(-45deg); }

/* ── Mobile Overlay ── */
.mobile-overlay {
  position: fixed;
  inset: 0;
  background: var(--color-bg);
  z-index: 999;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 48px 32px;
  pointer-events: none;
  opacity: 0;
  transition: opacity 0.35s ease;
}
.mobile-overlay.is-open {
  pointer-events: all;
  opacity: 1;
}

.mobile-nav {
  display: flex;
  flex-direction: column;
  gap: 8px;
}
.mobile-nav-link {
  font-family: var(--font-display);
  font-size: clamp(32px, 8vw, 56px);
  font-weight: 700;
  letter-spacing: -0.03em;
  color: rgba(255, 255, 255, 0.2);
  line-height: 1.15;
  opacity: 0;
  transform: translateY(16px);
  transition: color 0.25s ease, opacity 0.4s ease, transform 0.4s ease;
}
.mobile-overlay.is-open .mobile-nav-link {
  opacity: 1;
  transform: translateY(0);
}
.mobile-nav-link:hover,
.mobile-link--active { color: var(--color-accent); }

.mobile-footer {
  margin-top: 48px;
  display: flex;
  gap: 24px;
  flex-wrap: wrap;
}
.mobile-social {
  font-family: var(--font-mono);
  font-size: 12px;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--color-muted);
  transition: color var(--transition-base);
}
.mobile-social:hover { color: var(--color-accent); }

/* ── Responsive ── */
@media (max-width: 1024px) {
  .site-nav { padding: 0 32px; gap: 24px; }
  .nav-socials { display: none; }
}
@media (max-width: 768px) {
  .site-nav { padding: 0 20px; }
  .nav-links { display: none; }
  .hamburger { display: flex; }
}
@media (max-width: 640px) {
  .site-nav { padding: 0 16px; }
}
</style>
