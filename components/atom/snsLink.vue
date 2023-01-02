<template>
  <a :href="link" :class="$style.link">
    <img :src="imgSource"/>
  </a>
</template>
<script lang="ts">
import { PropType } from 'vue';

export type Props = {
  link: string,
  imgSource: string
}
export default defineComponent({
  props: {
    link: {
      type: String as PropType<Props['link']>,
      required: true 
    },
    imgSource: {
      type: String as PropType<Props['imgSource']>,
      required: true 
    }
  },
  setup(props) {
    
  },
})
</script>

<style lang="scss" module>
.link {
  display: block;
  border-radius: 50%;

  img{
    width: 40px;
    height: 40px;
  }
}
</style>
