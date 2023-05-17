<template>
  <div :class="$style.blog">
    <div :class="$style.blogWrapper">
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
        pageTitle: "<blog/>",
        introductionText: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
        imageSrc: "/image/blog/blog-1.jpeg"
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
  .blog {
    width: 100vw;

    .blogWrapper {
      max-width: 1280px;
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