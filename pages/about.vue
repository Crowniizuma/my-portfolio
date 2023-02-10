<template>
  <div :class="$style.about">
    <div :class="$style.aboutWrapper">
      <MoleculeIntroduction v-bind="introduction" :key="introduction.pageTitle"></MoleculeIntroduction>
    </div>
  </div>
</template>

<script lang="ts">
import { Props as introductionProps } from "@/components/molecule/introduction.vue"

export default defineComponent({
  setup() {
    const introduction = ref<introductionProps>(
      {
        pageTitle: "about",
        introductionText: "I have 2.5 years experiences working in IT industry as front-end web developer, system engineer and Bridge SE. I love solving problems and creating simple yet beautiful UI.",
        //imageSrc: "https://i.pinimg.com/564x/8d/85/6d/8d856d73c15c6281d004b33f291412bf.jpg"
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
    //background-image: url("https://i.pinimg.com/564x/e5/45/40/e5454032198880571c878d0069de745c.jpg");
    //background-size: cover;
    .aboutWrapper {
      width: 100%;
      padding-left: 40px;
      padding-right: 40px;
      margin: auto;
      @include pc_standard {
      padding-top: 100px;
      }
      padding-top: calc((100 / 1366) * 100vw);
    }
  }

</style>