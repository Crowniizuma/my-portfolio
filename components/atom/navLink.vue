<template>
  <NuxtLink :to="link" :class="[isClicked? $style.clicked : $style.normal, $style.link ]">{{ $t(title) }}</NuxtLink>
</template>
<script lang="ts">
import { PropType } from 'vue';

export type Props = {
  link: string,
  title: string,
  isClicked?: boolean,
}
export default defineComponent({
  props: {
    link: {
      type: String as PropType<Props['link']>,
      required: true 
    },
    title: {
      type: String as PropType<Props['title']>,
      required: true 
    },
    isClicked: {
      type: Boolean as PropType<Props['isClicked']>,
      required: false,
      default: false 
    },
  },
  setup(props) {
    
  },
})
</script>

<style lang="scss" module>
.link {

  size: calc((20/1366)*100vw);
  &.normal {
    color: #68b04e;
  }
  
  &.clicked {
    color: #a9aaa9;
  }
}
</style>
