<template>
  <div :class="$style.introductionWrapper">
    <div :class="$style.textWrapper">
      <AtomPageTitle :class="$style.pageTitle" :page-title="pageTitle"></AtomPageTitle>
      <AtomIntroductionText :class="$style.introductionText" :introduction-text="introductionText"></AtomIntroductionText>
    </div>
    <AtomImagine :image-src="imageSrc"></AtomImagine>
  </div>
</template>

<script lang="ts">
import { PropType } from 'vue';

export type Props = {
  pageTitle: string,
  introductionText: string,
  imageSrc: string
}
export default defineComponent ({
  props: {
    pageTitle: {
      type: String as PropType<Props['pageTitle']>,
      required: true
    },
    introductionText: {
      type: String as PropType<Props['introductionText']>,
      required: true
    },
    imageSrc: {
      type: String as PropType<Props['imageSrc']>,
      required: true
    }
  }
})
</script>

<style lang="scss" module>
  .introductionWrapper {
    width: 100%;
    display: flex;
    padding-left: 40px;
    padding-right: 40px;
    padding-bottom: 40px;

    .textWrapper {
      width: 50%;
      padding: 5%;
      display: flex;
      flex-direction: column;
      //align-items: flex-end;
      //justify-content: center;
      row-gap: 60px;
      
    }
  }
</style>