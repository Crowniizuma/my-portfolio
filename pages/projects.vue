<template>
  <div :class="$style.projects">
    <div :class="$style.projectsWrapper">
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
        pageTitle: "<projects/>",
        introductionText: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
        imageSrc: "/image/projects/project-1.jpeg"
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
  .projects {
    width: 100vw;
    .projectsWrapper {
      width: 100%;
      margin: auto;
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