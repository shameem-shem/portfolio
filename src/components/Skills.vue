<template>
  <section class="skills-wrp" id="skills" v-intersect="{
        handler: onIntersect,
        options:{
            threshold:[0, 0.5, 1]
        }
      }">
    <h1 class="headline font-weight-bold">My Skills</h1>
    <v-row>
      <v-col v-for="(skill,i) in skills" :key="i">
        <h6 class="mb-4 title font-weight-bold text-center">{{ skill.technology }}</h6>
        <transition name="svgAnim">
            <svg class="skill-svg"
                :style="isIntersecting ? {strokeDasharray : skill.knowledge * 670 / 100} : {strokeDasharray : 0}"
                version="1.1"
                xmlns="http://www.w3.org/2000/svg"
                xmlns:xlink="http://www.w3.org/1999/xlink"
                x="0px" y="0px"
                viewBox="0 0 271.55 246.96"
                style="enable-background:new 0 0 271.55 246.96;"
                xml:space="preserve" >
                <path d="M198.34,212l45.15-78.19c3.57-6.19,3.57-13.81,0-20l-45.15-78.19c-3.57-6.19-10.18-10-17.32-10l-90.29,0 c-7.15,0-13.75,3.81-17.32,10L28.26,113.8c-3.57,6.19-3.57,13.81,0,20L73.41,212c3.57,6.19,10.18,10,17.32,10l90.29,0 C188.16,222,194.77,218.18,198.34,212z"/>
            </svg>
        </transition>
      </v-col>
    </v-row>
  </section>
</template>

<script>
export default {
  data() {
    return {
      skills: [
        { technology: "HTML", knowledge: "90" },
        { technology: "CSS", knowledge: "90" },
        { technology: "SCSS, LESS", knowledge: "80" },
        { technology: "JavaScript", knowledge: "70" },
        { technology: "jQuery", knowledge: "80" },
        { technology: "VueJs", knowledge: "50" }
      ],
      isIntersecting: false,
    };
  },
  methods:{
      onIntersect(entries){
          this.isIntersecting = entries[0].isIntersecting
      }
  }
};
</script>

<style scoped>
.skill-svg {
  fill: none;
  stroke: #000;
  width: 10rem;
  stroke-width: 1.5rem;
  stroke-dashoffset: 0;
  stroke-dasharray: 670;
  transform: rotate(210deg);
  stroke-linecap: round;
}
.svgAnim-enter{
  stroke-dasharray: 0;
}
.svgAnim-enter-active{
  transition: all 0.5s ease-in-out;
}
</style>