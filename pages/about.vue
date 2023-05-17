<template>
  <div :class="$style.about">
    <div :class="$style.aboutWrapper">
      <MoleculeIntroduction v-bind="introduction" :key="introduction.pageTitle"></MoleculeIntroduction>
    </div>
    <MoleculeSkillChart :class="$style.chart"></MoleculeSkillChart>
  </div>
</template>

<script lang="ts">
import { Props as introductionProps } from "@/components/molecule/introduction.vue"

export default defineComponent({
  setup() {
    const introduction = ref<introductionProps>(
      {
        pageTitle: "<about/>",
        introductionText: "I have 2.5 years experiences working in IT industry as front-end web developer, system engineer and Bridge SE. I love solving problems and creating simple yet beautiful UI.",
        imageSrc: "/image/about/about-1.jpeg"
      }
    )
    return {
      introduction
    }
  },
})
</script>

<style lang="scss" module>
  @import "@/assets/styles/main.scss";
  .about {
    width: 100vw;
    .aboutWrapper {
      max-width: 1280px;
      margin: auto;
      height: 100vh;
      @include pc {
        padding-left: 40px;
        padding-right: 40px;
      }
      @include pc_standard {
        padding-top: 150px;
      }
      padding-top: calc((150 / 1366) * 100vw);
      padding-left: calc((40 / 1366) * 100vw);
      padding-right: calc((40 / 1366) * 100vw);
      
    }

  }

</style>