<template>
  <section id="portfolio">
    <v-img :src="abstract3" cover class="abstract-3"></v-img>

    <div class="pa-5 position-relative">
      <div class="d-flex flex-wrap align-end justify-space-between mb-8" style="gap:16px">
        <div>
          <div class="section-eyebrow mb-2">05 — Portfolio</div>
          <h2 class="text-h2 font-weight-bold mb-0">What I've <span class="gradient-text">done.</span></h2>
        </div>
        <div class="text-body-2 text-medium-emphasis" style="max-width: 420px;">
          A selection of projects spanning frontend, WordPress, and full-stack work.
        </div>
      </div>

      <div class="projects-grid">
        <a
          v-for="(item, index) in items"
          :key="index"
          :href="item.source"
          target="_blank"
          rel="noopener"
          class="project-card hover-lift"
        >
          <div class="project-thumb">
            <img :src="item.img" :alt="item.title" />
            <div class="project-overlay">
              <div class="overlay-inner">
                <div class="overlay-year">{{ item.year }}</div>
                <v-icon size="28" color="white">mdi-arrow-top-right</v-icon>
              </div>
            </div>
          </div>
          <div class="project-body">
            <div class="project-title">{{ item.title }}</div>
            <div class="project-desc">{{ item.desc }}</div>
          </div>
        </a>
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

.abstract-3 {
  position: absolute !important;
  left: 0;
  right: 0;
  z-index: 0 !important;
  opacity: 0.25;
}

a { text-decoration: none; color: inherit; }

.section-eyebrow {
  font-family: 'Space Grotesk', sans-serif;
  font-size: 13px;
  font-weight: 600;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  color: #ffaa00;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
}

.project-card {
  display: block;
  background: rgba(255,255,255,0.03);
  border: 1px solid rgba(255,255,255,0.07);
  border-radius: 18px;
  overflow: hidden;
  color: inherit;
}

.project-thumb {
  position: relative;
  aspect-ratio: 16 / 10;
  overflow: hidden;
  background: #0e0e14;
}
.project-thumb img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform .6s cubic-bezier(.2,.7,.2,1), filter .6s ease;
}
.project-card:hover .project-thumb img {
  transform: scale(1.06);
  filter: saturate(1.1);
}

.project-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(180deg, rgba(11,11,16,0) 30%, rgba(11,11,16,0.85) 100%);
  display: flex;
  align-items: flex-end;
  opacity: 0;
  transition: opacity .3s ease;
}
.project-card:hover .project-overlay { opacity: 1; }
.overlay-inner {
  display: flex;
  width: 100%;
  justify-content: space-between;
  align-items: center;
  padding: 14px 18px;
}
.overlay-year {
  font-family: 'Space Grotesk', sans-serif;
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 0.2em;
  color: #ffaa00;
  background: rgba(255,170,0,0.12);
  padding: 4px 10px;
  border-radius: 999px;
  border: 1px solid rgba(255,170,0,0.4);
}

.project-body {
  padding: 18px 20px 22px;
}
.project-title {
  font-family: 'Space Grotesk', sans-serif;
  font-size: 18px;
  font-weight: 600;
  color: #fff;
  margin-bottom: 6px;
}
.project-desc {
  font-size: 13px;
  color: rgba(255,255,255,0.6);
  line-height: 1.55;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
</style>

