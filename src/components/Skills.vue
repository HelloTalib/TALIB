<template>
  <section id="skills">
    <v-row class="pa-5" justify="space-around" no-gutters>
      <v-img :src="abstract2" height="711" width="778" class="abstract-2"></v-img>
      <v-col cols="12" class="mb-5" style="position:relative">
        <v-row justify="space-between" no-gutters>
          <h2 class="text-h3 font-weight-bold text-primary mb-4">What I Know</h2>
          <blockquote>
            <p class="text-subtitle-1 font-weight-light font-italic">
              Need a more professional describtion of me? Well, here's exactly that:)
            </p>
            <footer class="text-center">
              <v-btn
                color="primary"
                href="https://drive.google.com/file/d/1fv4O3MIylENtRadVWQRKjVlqe0V1uF5z/view?usp=sharing"
              >
                <span>Download CV</span>
              </v-btn>
            </footer>
          </blockquote>
        </v-row>
      </v-col>
      <v-col cols="12" md="3">
        <h3 class="text-h5 font-weight-medium mb-4 text-primary">My Education</h3>
        <v-sheet v-for="(edu,index) in educations" :key="index" class="mb-5 bg-transparent">
          <div class="d-flex">
            <v-sheet class="mr-3" color="primary" height="100" width="1"></v-sheet>
            <div class="flex-grow-1">
              <div class="mb-3">{{edu.name}}</div>
              <div class="text-right">
                <span class="text-h6 text-primary">{{edu.stream}}</span>
                <footer>
                  <div>{{edu.alt}}</div>
                  <div>{{edu.duration}}</div>
                </footer>
              </div>
            </div>
          </div>
        </v-sheet>
      </v-col>
      <v-col cols="12" md="4">
        <h3 class="text-h5 font-weight-medium mb-4 text-primary">My Skills</h3>
        <div class="mb-4" v-for="(skill, index) in skills" :key="index">
          <h4 class="text-uppercase mb-3 text-primary">{{skill.skillName}}</h4>
          <div class="pl-4">
            <v-row
              align="center"
              v-for="(currentSkill, sIndex) in skill.skillSets"
              :key="sIndex"
              class="mb-4"
              no-gutters
            >
              <v-col cols="5">
                <h5 class="text-subtitle-1">{{currentSkill.name}}</h5>
              </v-col>
              <v-col cols="7">
                <v-rating
                  density="compact"
                  readonly
                  active-color="primary"
                  color="#111"
                  :full-icon="fullIcon"
                  :empty-icon="emptyIcon"
                  :model-value="currentSkill.exp"
                ></v-rating>
              </v-col>
            </v-row>
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
      fullIcon: "mdi-star-circle-outline",
      emptyIcon: "mdi-star-circle-outline",
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
section {
  position: relative;
}
  blockquote{
    max-width: 290px;
    text-align: center;
    margin-bottom: 0;
}
    blockquote p{
      margin-bottom: 0;
    }

.abstract-2 {
  position: absolute !important;
  right: 0;
  top: -128px;
  z-index: 0 !important;
}

.abstract-2 ~ * {
  z-index: 1 !important;
}
@media screen and (max-width:600px) {
  blockquote{
    display: none;
  }
}
</style>
