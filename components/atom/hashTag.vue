<template>
  <div :class="$style.hashtagWrapper">
    <a :class="$style.hashtagLink">{{ $t(hashtagContent) }}</a>
  </div>
</template>

<script lang="ts">
import { PropType } from 'vue';
export type Props = {
  hashtagContent: string
}
export default defineComponent ({
  props: {
    hashtagContent: {
      type: String as PropType<Props['hashtagContent']>,
      required: true
    }
  },
 setup() {

 }
})
</script>

<style lang="scss" module>
@import "@/assets/styles/main.scss";
.hashtagWrapper {
  width: 100%;

  .hashtagLink {
    color: #fff;
    font-weight: bold;
    @include pc_standard {
      font-size: 12px;
    }
    font-size: calc((12 / 1366) * 100vw);
    padding: 5px;
    background-image: linear-gradient(180deg, $color4 0%,  $color5 100%);
    border-radius: 5px;
  }
}
</style>