<template>
  <div>
    <p :class="$style.introduction">{{ $t(introductionText) }}</p>
  </div>
</template>

<script lang="ts">
import { PropType } from 'vue';

export type Props = {
  introductionText: string
}

export default defineComponent({
  props: {
    introductionText: {
      type: String as PropType<Props['introductionText']>,
      required: true
    }
  },
  setup() {
    
  },
})
</script>

<style lang="scss" module>
@import '@/assets/styles/main.scss';

.introduction {
  @include pc_standard {
    font-size: 25px;
  }
  font-size: calc((25 / 1366) * 100vw);
  line-height: 1.5em;
}
</style>