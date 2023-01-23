<template>
  <a :href="link" :class="$style.link" target="_blank">
    <img :src="isSnsFooter? imgSourceFooter : imgSourceHeader" target="_blank"/>
  </a>
</template>
<script lang="ts">
import { PropType } from 'vue';

export type Props = {
  link: string,
  imgSourceHeader: string,
  imgSourceFooter: string,
  isSnsFooter: boolean
}
export default defineComponent({
  props: {
    link: {
      type: String as PropType<Props['link']>,
      required: true 
    },
    imgSourceHeader: {
      type: String as PropType<Props['imgSourceHeader']>,
      required: true 
    },
    imgSourceFooter: {
      type: String as PropType<Props['imgSourceFooter']>,
      required: true 
    },
    isSnsFooter: {
      type: Boolean as PropType<Props['isSnsFooter']>,
      required: false,
      default: false 
    }
  },
  setup(props) {
    
  },
})
</script>

<style lang="scss" module>
@import '@/assets/styles/main.scss';
.link {
  display: block;
  border-radius: 50%;

  img{
    @include pc_standard {
      width: 30px;
      height: auto;
    }
    width: calc((30/1366) * 100vw);
    height: auto;
  }
}
</style>
