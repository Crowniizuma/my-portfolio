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
        imageSrc: "https://i.pinimg.com/564x/32/cd/b5/32cdb5096400eebc7b5fcf3fb510a320.jpg"
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
      padding-top: 150px;
      }
      padding-top: calc((150 / 1366) * 100vw);
    }
  }

</style>