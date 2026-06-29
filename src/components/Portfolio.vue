<template>
  <section id="portfolio">
    <div class="section-wrap">
      <!-- Header -->
      <div class="portfolio-header fade-up">
        <div>
          <div class="section-eyebrow">05 — Portfolio</div>
          <h2 class="section-heading">What I've <span class="gradient-text">done.</span></h2>
        </div>
        <p class="portfolio-sub">A selection of projects spanning frontend, WordPress, and full-stack work.</p>
      </div>

      <!-- Asymmetric grid: first item featured (full width) -->
      <div class="projects-layout">
        <!-- Featured project (index 0) -->
        <a
          v-if="items.length > 0"
          :href="items[0].source"
          target="_blank"
          rel="noopener noreferrer"
          class="project-card project-featured fade-up delay-1"
          :aria-label="'View project: ' + items[0].title"
          @mousemove="onCardTilt($event)"
          @mouseleave="onCardLeave($event)"
        >
          <div class="card-shine" aria-hidden="true"></div>
          <div class="project-thumb">
            <img :src="items[0].img" :alt="items[0].title" loading="lazy" />
            <div class="project-overlay">
              <span class="overlay-year">{{ items[0].year }}</span>
              <span class="overlay-arrow" aria-hidden="true">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M7 17L17 7M17 7H7M17 7v10"/></svg>
              </span>
            </div>
          </div>
          <div class="project-body">
            <span class="project-badge">Featured</span>
            <h3 class="project-title">{{ items[0].title }}</h3>
            <p class="project-desc">{{ items[0].desc }}</p>
          </div>
        </a>

        <!-- Remaining projects (2-col grid) -->
        <div class="projects-grid">
          <a
            v-for="(item, index) in items.slice(1)"
            :key="index"
            :href="item.source"
            target="_blank"
            rel="noopener noreferrer"
            class="project-card fade-up"
            :class="'delay-' + Math.min(index + 2, 5)"
            @mousemove="onCardTilt($event)"
            @mouseleave="onCardLeave($event)"
          >
            <div class="card-shine" aria-hidden="true"></div>
            <div class="project-thumb">
              <img :src="item.img" :alt="item.title" loading="lazy" />
              <div class="project-overlay">
                <span class="overlay-year">{{ item.year }}</span>
                <span class="overlay-arrow" aria-hidden="true">
                  <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M7 17L17 7M17 7H7M17 7v10"/></svg>
                </span>
              </div>
            </div>
            <div class="project-body">
              <h3 class="project-title">{{ item.title }}</h3>
              <p class="project-desc">{{ item.desc }}</p>
            </div>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import abstract3 from "@/assets/abstract-3.png";
import demoFlorence from "@/assets/portfolio/demo-florence.png";
import demoBrooklyn from "@/assets/portfolio/demo-brooklyn.png";
import demoPeakShop from "@/assets/portfolio/demo-peak-shop.png";
import demoOxpitan from "@/assets/portfolio/demo-oxpitan.png";
import personalPortfolio from "@/assets/portfolio/personal-portfolio.png";
import demoBalou from "@/assets/portfolio/demo-balou.png";
import demoYard from "@/assets/portfolio/demo-yard.png";
import demoCraft from "@/assets/portfolio/demo-craft.png";
import demoCreativeHub from "@/assets/portfolio/demo-creative-hub.png";
import demoDesignBites from "@/assets/portfolio/demo-design-bites.png";

export default {
  methods: {
    onCardTilt(e) {
      const card = e.currentTarget;
      const rect = card.getBoundingClientRect();
      const x = (e.clientX - rect.left) / rect.width  - 0.5;
      const y = (e.clientY - rect.top)  / rect.height - 0.5;
      card.style.transform = `perspective(700px) rotateX(${y * -10}deg) rotateY(${x * 10}deg) translateY(-4px) scale(1.01)`;
      const shine = card.querySelector(".card-shine");
      if (shine) shine.style.background = `radial-gradient(circle at ${(x + 0.5) * 100}% ${(y + 0.5) * 100}%, rgba(110,231,183,0.13) 0%, transparent 55%)`;
    },
    onCardLeave(e) {
      const card = e.currentTarget;
      card.style.transform = "";
      card.style.transition = "transform 0.5s cubic-bezier(0.2,0.7,0.2,1)";
      const shine = card.querySelector(".card-shine");
      if (shine) shine.style.background = "";
      setTimeout(() => { card.style.transition = ""; }, 500);
    },
  },
  data() {
    return {
      abstract3,
      items: [
        {
          desc: "This is a Beauty Parlour Website. Uses html, CSS, SASS &; UIKIT Framework to Design this static website. This website is really outstanding to look😍.",
          title: "Parlour Website",
          source: "https://floreence.netlify.app/",
          year: "2019",
          img: demoFlorence,
        },
        {
          desc: "This is an Agency Website. Uses html, CSS, SASS &; UIKIT Framework to Design this static website. This was just a project and was coded by me in 7th Grade.",
          title: "Agency Website",
          source: "https://brooklynn.netlify.app/",
          year: "2019",
          img: demoBrooklyn,
        },
        {
          desc: "This is an Online Store Project. Uses html, CSS, SASS &; UIKIT Framework to Design this static website",
          title: "Online Store",
          source: "https://peak-shop.netlify.app/",
          year: "2019",
          img: demoPeakShop,
        },
        {
          desc: "This is a Non-Profit Organization Website. I use html, CSS, SASS &; UIKIT Framework to Design this static website",
          title: "Non-Profit Website",
          source: "https://oxpitan.netlify.app/",
          year: "2019",
          img: demoOxpitan,
        },
        {
          desc: "This is My Personal Portfolio Website. I used html, CSS, SASS VueJs, VuetifyJs ect. to develop this awesome looking protfolio website;",
          title: "Portfolio Website",
          source: "https://talib.netlify.app/",
          year: "2019",
          img: personalPortfolio,
        },
        {
          desc: "This is kids wears and accesories Website. I used html, CSS, SASS to develop this website;",
          title: "Kids Website",
          source: "https://babiees.netlify.app/",
          year: "2019",
          img: demoBalou,
        },
        {
          desc: "This is an interior design Website. I used html, CSS, SASS to develop this awesome looking interior website;",
          title: "Interior Website",
          source: "https://yaard.netlify.app/",
          year: "2019",
          img: demoYard,
        },
        {
          desc: "This is a Handcraft design Website. I used html, CSS, SASS to develop this awesome looking handcraft website;",
          title: "Craft Website",
          source: "https://crafti.netlify.app/",
          year: "2019",
          img: demoCraft,
        },
        {
          desc: "This is a Creative minimal looking Website. I used html, CSS, SASS to develop this awesome looking handcraft website;",
          title: "Creative Website",
          source: "https://creativehub.netlify.app/",
          year: "2019",
          img: demoCreativeHub,
        },
        {
          desc: "This is a Blog Website. I used html, CSS, SASS to develop this awesome looking blog resources website;",
          title: "Blog Website",
          source: "https://designbites.netlify.app/",
          year: "2019",
          img: demoDesignBites,
        },
        // {
        //   title: "Dashboard",
        //   desc:
        //     "A Online Course Learning management system written in Vuejs. Uses Firebase for the database management. All the data is encrypted using BCrypt. This was my first big project and was coded by me in 7th Grade.",
        //   source: "https://tgerodo-vuejs.netlify.app",
        //   year: "2019",
        //   img: require("@/assets/portfolio/dashboard.png")
        // },
        // {
        //   title: "SubReddit",
        //   desc: "A subreddit web application. Uses axios for the database management. All the data is encrypted using axios. This was also learning based project with Brad Traversy",
        //   source: "https://subreddit.netlify.app",
        //   year: "2018",
        //   img: require("@/assets/portfolio/subreddit.png"),
        // },
        // {
        //   title: "Countries",
        //   desc: "A Project management system written in VueJs. Uses Firebase for the database and Authentication management. All the data is encrypted using Firebase Authentication.",
        //   source: "https://countries-1.netlify.app/",
        //   year: "2018",
        //   img: require("@/assets/portfolio/login.png"),
        // },

        // {
        //   title: "Smoothies",
        //   desc: "A todo list management system written in Vuejs. Uses firebase for the database management and Authentication. All the data is encrypted using Firebase Authentication. This was a learning based project with net ninja",
        //   source: "https://smoothies.netlify.com/",

        //   year: "2017",
        //   img: require("@/assets/portfolio/3.jpg"),
        // },
      ],
    };
  },
};
</script>

<style scoped>
section { position: relative; }
a { text-decoration: none; color: inherit; }

/* ── Header ── */
.portfolio-header {
  display: flex;
  flex-wrap: wrap;
  align-items: flex-end;
  justify-content: space-between;
  gap: 24px;
  margin-bottom: 56px;
}
.section-heading {
  font-size: clamp(32px, 4vw, 52px);
  font-weight: 700;
  line-height: 1.1;
  margin-bottom: 0;
}
.portfolio-sub {
  font-size: 14px;
  color: var(--color-muted);
  max-width: 380px;
  line-height: 1.7;
  margin: 0;
}

/* ── Layout ── */
.projects-layout {
  display: flex;
  flex-direction: column;
  gap: 20px;
}
.projects-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

/* ── Card base ── */
.project-card {
  display: block;
  position: relative;
  background: rgba(255, 255, 255, 0.025);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  overflow: hidden;
  will-change: transform;
  transform-style: preserve-3d;
  transition: box-shadow 0.3s ease, border-color 0.3s ease;
}
.project-card:hover {
  box-shadow: var(--shadow-soft);
  border-color: var(--color-accent-border);
}

/* ── Shine layer ── */
.card-shine {
  position: absolute;
  inset: 0;
  z-index: 2;
  pointer-events: none;
  border-radius: inherit;
  transition: background 0.15s ease;
}

/* ── Thumbnail ── */
.project-thumb {
  position: relative;
  aspect-ratio: 16 / 10;
  overflow: hidden;
  background: var(--color-surface);
}
.project-featured .project-thumb { aspect-ratio: 16 / 7; }

.project-thumb img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.6s cubic-bezier(0.2,0.7,0.2,1);
}
.project-card:hover .project-thumb img { transform: scale(1.04); }

/* ── Overlay ── */
.project-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(180deg, transparent 35%, rgba(10,10,15,0.88) 100%);
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  padding: 16px 20px;
  opacity: 0;
  transition: opacity 0.3s ease;
}
.project-card:hover .project-overlay { opacity: 1; }

.overlay-year {
  font-family: var(--font-mono);
  font-size: 11px;
  font-weight: 500;
  letter-spacing: 0.16em;
  color: var(--color-accent);
  background: var(--color-accent-dim);
  border: 1px solid var(--color-accent-border);
  padding: 4px 10px;
  border-radius: 999px;
}
.overlay-arrow {
  width: 36px;
  height: 36px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  background: var(--color-accent);
  color: #0A0A0F;
  border-radius: 50%;
}

/* ── Body ── */
.project-body {
  padding: 20px 24px 24px;
}
.project-badge {
  display: inline-block;
  font-family: var(--font-mono);
  font-size: 10px;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--color-accent);
  background: var(--color-accent-dim);
  border: 1px solid var(--color-accent-border);
  padding: 3px 10px;
  border-radius: 999px;
  margin-bottom: 10px;
}
.project-title {
  font-family: var(--font-display);
  font-size: 18px;
  font-weight: 600;
  color: var(--color-text);
  margin-bottom: 8px;
}
.project-featured .project-title { font-size: 22px; }
.project-desc {
  font-size: 13px;
  color: var(--color-muted);
  line-height: 1.6;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
  margin: 0;
}

/* ── Responsive ── */
@media (max-width: 1024px) {
  .projects-grid { grid-template-columns: repeat(2, 1fr); }
}
@media (max-width: 640px) {
  .projects-grid { grid-template-columns: 1fr; }
  .project-featured .project-thumb { aspect-ratio: 16 / 9; }
}
</style>
