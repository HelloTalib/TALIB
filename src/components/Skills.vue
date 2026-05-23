<template>
  <section id="skills">
    <v-img :src="abstract2" height="711" width="778" class="abstract-2"></v-img>
    <v-row class="pa-5 position-relative" no-gutters>
      <v-col cols="12" class="mb-10">
        <div class="d-flex flex-wrap align-end justify-space-between" style="gap:24px">
          <div>
            <div class="section-eyebrow mb-2">04 — Expertise</div>
            <h2 class="text-h2 font-weight-bold">What <span class="gradient-text">I know.</span></h2>
          </div>
          <div class="cv-cta glass pa-5">
            <p class="text-body-2 text-medium-emphasis mb-3 font-italic">
              Need a more professional description of me? Well, here's exactly that 😊
            </p>
            <v-btn
              class="btn-gradient"
              href="https://drive.google.com/file/d/1fv4O3MIylENtRadVWQRKjVlqe0V1uF5z/view?usp=sharing"
              target="_blank"
            >
              <v-icon start>mdi-download</v-icon>
              Download CV
            </v-btn>
          </div>
        </div>
      </v-col>

      <!-- Education -->
      <v-col cols="12" md="5" class="pr-md-6">
        <h3 class="block-title mb-5">
          <v-icon size="20" color="primary" class="mr-2">mdi-school-outline</v-icon>
          My Education
        </h3>
        <div class="edu-track">
          <div v-for="(edu,index) in educations" :key="index" class="edu-card hover-lift">
            <span class="edu-duration">{{ edu.duration }}</span>
            <div class="edu-stream gradient-text">{{ edu.stream }}</div>
            <div class="edu-name">{{ edu.name }}</div>
            <div class="edu-alt">{{ edu.alt }}</div>
          </div>
        </div>
      </v-col>

      <!-- Skills -->
      <v-col cols="12" md="7" class="pl-md-6 mt-8 mt-md-0">
        <h3 class="block-title mb-5">
          <v-icon size="20" color="primary" class="mr-2">mdi-code-tags</v-icon>
          My Skills
        </h3>
        <div class="mb-8" v-for="(skill, index) in skills" :key="index">
          <h4 class="skill-group-title mb-4">{{ skill.skillName }}</h4>
          <div class="skills-grid">
            <div
              v-for="(currentSkill, sIndex) in skill.skillSets"
              :key="sIndex"
              class="skill-row"
            >
              <div class="d-flex align-center justify-space-between mb-1">
                <span class="skill-name">{{ currentSkill.name }}</span>
                <span class="skill-pct">{{ currentSkill.exp * 20 }}%</span>
              </div>
              <div class="bar">
                <div class="bar-fill" :style="{ width: (currentSkill.exp * 20) + '%' }"></div>
              </div>
            </div>
          </div>
        </div>
      </v-col>
    </v-row>
  </section>
</template>

<script>
import abstract2 from "@/assets/abstract-2.png";

export default {
  data() {
    return {
      abstract2,
      educations: [
               {  name: "Asian University of Bangladesh",
          alt: "CSE",
          stream: "Computer Science and Engineering",
          duration: "2017-2021"
        },
        {
          name: "BitDegree",
          alt: "Full-Stack Web Developer",
          stream: "Certification of Full-Stack Web Development",
          duration: "2019-2020"
        },
        {
          name: "Learn With Hasin Hayder",
          alt: "WordPress Expert",
          stream: "Mastering WordPress",
          duration: "2019-2020"
        },
        {
          name: "Eduonix Learning Solutions",
          alt: "Back End Development",
          stream: "Mastering PHP & MySQL",
          duration: "2018-2019"
        },
        {
          name: "Udemy",
          alt: "Front End Development",
          stream: "Front End Development",
          duration: "2017-2018"
        },
        // {
        //   name: "National University of Bangladesh",
        //   alt: "Political Science",
        //   stream: "Bachelor of Social Science",
        //   duration: "2017-Present"
        // },


        {
          name: "Zirabo Dewan Idris College",
          alt: "General Subject",
          stream: "Higher Secondary",
          duration: "2015-2017"
        },
        {
          name: "Jumarbari High School",
          alt: "General Subject",
          stream: "Senior Secondary",
          duration: "2013-2015"
        },
        {
          name: "Kamalerpara High School",
          alt: "General Subject",
          stream: "Junior Secondary",
          duration: "2009-2012"
        },
        {
          name: "Folia Digar Govt. Primary School",
          alt: "General Subject",
          stream: "Primary Education",
          duration: "2004-2008"
        }
      ],
      skills: [
        {
          skillName: "Web Design",
          skillSets: [
            { name: "HTML", exp: 5 },
            { name: "CSS", exp: 4 },
            { name: "BootsTrap", exp: 5 },
            { name: "UIkit", exp: 5 },
            { name: "MeterilizeCSS", exp: 4 },
            { name: "SASS", exp: 5 },
            { name: "JavaScript", exp: 4 },
            { name: "jQuery", exp: 5 },
            { name: "AJAX", exp: 4 },
            { name: "VueJs", exp: 5 },
            { name: "VuetifyJs", exp: 4 },
            { name: "ReactJs", exp: 3 },
          ]
        },
        {
          skillName: "Web Development & Others",
          skillSets: [
            { name: "PHP", exp: 4 },
            { name: "MYSQL", exp: 3 },
            { name: "WordPress", exp: 4 },
            { name: "Elementor", exp: 5 },
            { name: "WooCommerce", exp: 5 },
            { name: "Gutenburg", exp: 3 },
            { name: "ExpressJs", exp: 3 },
            { name: "MongoDB", exp: 3 },
            { name: "NodeJs", exp: 3 },
            { name: "Firebase", exp: 4 },
            { name: "Github", exp: 5 },
          ]
        }
      ]
    };
  }
};
</script>


<style scoped>
section { position: relative; }

.abstract-2 {
  position: absolute !important;
  right: 0;
  top: -128px;
  z-index: 0 !important;
  opacity: 0.3;
}

.section-eyebrow {
  font-family: 'Space Grotesk', sans-serif;
  font-size: 13px;
  font-weight: 600;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  color: #ffaa00;
}

.cv-cta {
  max-width: 360px;
  text-align: center;
}

.block-title {
  display: inline-flex;
  align-items: center;
  font-family: 'Space Grotesk', sans-serif;
  font-size: 14px;
  font-weight: 600;
  letter-spacing: 0.25em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.85);
  padding: 6px 14px;
  border-radius: 999px;
  background: rgba(255,170,0,0.08);
  border: 1px solid rgba(255,170,0,0.2);
}

/* Education */
.edu-track {
  position: relative;
  padding-left: 18px;
  border-left: 2px solid rgba(255,170,0,0.25);
}
.edu-card {
  position: relative;
  padding: 16px 18px;
  margin-bottom: 14px;
  background: rgba(255,255,255,0.03);
  border: 1px solid rgba(255,255,255,0.06);
  border-radius: 14px;
}
.edu-card::before {
  content: "";
  position: absolute;
  left: -27px;
  top: 22px;
  width: 14px;
  height: 14px;
  border-radius: 50%;
  background: linear-gradient(135deg, #ffaa00, #ff5e62);
  border: 3px solid var(--bg-base, #0b0b10);
  box-shadow: 0 0 0 2px rgba(255,170,0,0.4);
}
.edu-duration {
  display: inline-block;
  font-family: 'Space Grotesk', sans-serif;
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 0.18em;
  color: #ffaa00;
  background: rgba(255,170,0,0.08);
  padding: 3px 10px;
  border-radius: 999px;
  margin-bottom: 8px;
}
.edu-stream {
  font-family: 'Space Grotesk', sans-serif;
  font-size: 16px;
  font-weight: 600;
  line-height: 1.3;
}
.edu-name {
  font-size: 14px;
  color: rgba(255,255,255,0.9);
  margin-top: 4px;
}
.edu-alt {
  font-size: 12px;
  color: rgba(255,255,255,0.55);
  margin-top: 2px;
}

/* Skills */
.skill-group-title {
  font-family: 'Space Grotesk', sans-serif;
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.55);
}
.skills-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0,1fr));
  gap: 18px 28px;
}
@media (max-width: 600px) {
  .skills-grid { grid-template-columns: 1fr; }
}
.skill-name {
  font-family: 'Space Grotesk', sans-serif;
  font-size: 14px;
  font-weight: 500;
  color: rgba(255,255,255,0.92);
}
.skill-pct {
  font-family: 'Space Grotesk', sans-serif;
  font-size: 12px;
  font-weight: 600;
  color: rgba(255,170,0,0.9);
}
.bar {
  height: 6px;
  border-radius: 999px;
  background: rgba(255,255,255,0.06);
  overflow: hidden;
}
.bar-fill {
  height: 100%;
  background: linear-gradient(90deg, #ffaa00, #ff5e62);
  border-radius: 999px;
  transition: width .8s cubic-bezier(.2,.7,.2,1);
}
</style>
