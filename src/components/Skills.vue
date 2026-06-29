<template>
  <section id="skills">
    <div class="section-wrap">
      <!-- Header row -->
      <div class="skills-header fade-up">
        <div>
          <div class="section-eyebrow">04 — Expertise</div>
          <h2 class="section-heading">What <span class="gradient-text">I know.</span></h2>
        </div>
        <div class="cv-cta glass">
          <p class="cv-caption">Need a full professional profile? Here it is 😊</p>
          <a
            href="https://drive.google.com/file/d/1fv4O3MIylENtRadVWQRKjVlqe0V1uF5z/view?usp=sharing"
            target="_blank"
            rel="noopener noreferrer"
            class="btn-cv"
          >
            <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M21 15v4a2 2 0 01-2 2H5a2 2 0 01-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
            Download CV
          </a>
        </div>
      </div>

      <!-- Two-column: Education + Skills -->
      <div class="skills-grid-layout">
        <!-- Education -->
        <div class="fade-up delay-1">
          <h3 class="block-label">
            <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><path d="M22 10v6M2 10l10-5 10 5-10 5z"/><path d="M6 12v5c3 3 9 3 12 0v-5"/></svg>
            Education
          </h3>
          <div class="edu-track">
            <div
              v-for="(edu, index) in educations"
              :key="index"
              class="edu-card hover-lift"
            >
              <span class="edu-duration">{{ edu.duration }}</span>
              <div class="edu-stream gradient-text">{{ edu.stream }}</div>
              <div class="edu-name">{{ edu.name }}</div>
              <div class="edu-alt">{{ edu.alt }}</div>
            </div>
          </div>
        </div>

        <!-- Skills -->
        <div class="fade-up delay-2">
          <h3 class="block-label">
            <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><polyline points="16 18 22 12 16 6"/><polyline points="8 6 2 12 8 18"/></svg>
            Skills
          </h3>
          <div
            v-for="(skill, index) in skills"
            :key="index"
            class="skill-group"
          >
            <h4 class="skill-group-title">{{ skill.skillName }}</h4>
            <div class="skill-tags">
              <span
                v-for="(s, si) in skill.skillSets"
                :key="si"
                class="skill-tag"
                :data-level="s.exp"
              >{{ s.name }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import abstract2 from "@/assets/abstract-2.png";

export default {
  data() {
    return {
      abstract2,
      educations: [
        {
          name: "Asian University of Bangladesh",
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

/* ── Header ── */
.skills-header {
  display: flex;
  flex-wrap: wrap;
  align-items: flex-end;
  justify-content: space-between;
  gap: 32px;
  margin-bottom: 72px;
}
.section-heading {
  font-size: clamp(32px, 4vw, 52px);
  font-weight: 700;
  line-height: 1.1;
  margin-bottom: 0;
}

/* ── CV CTA ── */
.cv-cta {
  padding: 20px 24px;
  text-align: center;
  max-width: 320px;
}
.cv-caption {
  font-size: 13px;
  color: var(--color-muted);
  font-style: italic;
  margin: 0 0 14px 0;
}
.btn-cv {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 10px 22px;
  background: var(--color-accent);
  color: #0A0A0F;
  font-weight: 600;
  font-size: 13px;
  border-radius: var(--radius-md);
  text-decoration: none;
  transition: filter var(--transition-base), transform var(--transition-base);
  will-change: transform;
}
.btn-cv:hover { filter: brightness(1.06); transform: translateY(-1px); }

/* ── Two-col layout ── */
.skills-grid-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 64px;
  align-items: start;
}

/* ── Block labels ── */
.block-label {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  font-family: var(--font-mono);
  font-size: 11px;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--color-text);
  background: var(--color-accent-dim);
  border: 1px solid var(--color-accent-border);
  padding: 6px 14px;
  border-radius: 999px;
  margin-bottom: 24px;
  color: var(--color-accent);
}

/* ── Education ── */
.edu-track {
  position: relative;
  padding-left: 20px;
  border-left: 1px solid var(--color-accent-border);
}
.edu-card {
  position: relative;
  padding: 14px 18px;
  margin-bottom: 12px;
  background: rgba(255, 255, 255, 0.025);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-md);
}
.edu-card::before {
  content: "";
  position: absolute;
  left: -27px;
  top: 18px;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: var(--color-accent);
  border: 2px solid var(--color-bg);
  box-shadow: 0 0 0 2px var(--color-accent-border);
}
.edu-duration {
  display: inline-block;
  font-family: var(--font-mono);
  font-size: 10px;
  font-weight: 500;
  letter-spacing: 0.14em;
  color: var(--color-accent);
  background: var(--color-accent-dim);
  padding: 3px 9px;
  border-radius: 999px;
  margin-bottom: 6px;
}
.edu-stream {
  font-family: var(--font-display);
  font-size: 14px;
  font-weight: 600;
  line-height: 1.3;
}
.edu-name {
  font-size: 13px;
  color: rgba(226, 232, 240, 0.85);
  margin-top: 3px;
}
.edu-alt {
  font-size: 11px;
  color: var(--color-muted);
  margin-top: 2px;
}

/* ── Skills as Tags ── */
.skill-group { margin-bottom: 32px; }
.skill-group-title {
  font-family: var(--font-mono);
  font-size: 11px;
  font-weight: 500;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--color-muted);
  margin-bottom: 14px;
}
.skill-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}
.skill-tag {
  display: inline-block;
  padding: 5px 14px;
  border: 1px solid var(--color-accent-border);
  border-radius: 999px;
  font-size: 13px;
  font-weight: 500;
  color: var(--color-text);
  background: var(--color-accent-dim);
  transition: background var(--transition-base), color var(--transition-base), border-color var(--transition-base);
  cursor: default;
}
.skill-tag:hover,
.skill-tag[data-level="5"] {
  background: rgba(110, 231, 183, 0.18);
  border-color: var(--color-accent);
  color: var(--color-accent);
}

/* ── Responsive ── */
@media (max-width: 1024px) {
  .skills-grid-layout { gap: 40px; }
}
@media (max-width: 768px) {
  .skills-grid-layout { grid-template-columns: 1fr; gap: 48px; }
  .skills-header { flex-direction: column; align-items: flex-start; }
  .cv-cta { max-width: 100%; }
}
</style>
