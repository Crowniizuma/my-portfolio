<template>
  <div>
    <p :class="$style.pageTitle">{{ $t(pageTitle) }}</p>
  </div>
</template>

<script lang="ts">
import { PropType } from 'vue';

export type Props = {
  pageTitle: string
}

export default defineComponent({
  props: {
    pageTitle: {
      type: String as PropType<Props['pageTitle']>,
      required: true
    }
  },
  setup() {
    
  },
})
</script>

<style lang="scss" module>
@import '@/assets/styles/main.scss';

.pageTitle {
  @include pc_standard {
    font-size: 40px;
  }
  font-size: calc((40 / 1366) * 100vw);
  font-weight: bold;
}
</style>