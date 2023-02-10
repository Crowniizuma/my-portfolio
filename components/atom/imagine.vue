<template>
  <div :class="$style.imageWrapper">
    <img :src="imageSrc" :class="$style.image"/>
  </div>
</template>

<script lang="ts">
import { PropType } from 'vue';
export type Props = {
  imageSrc: string
} 
export default defineComponent({
  props: {
    imageSrc: {
      type: String as PropType<Props['imageSrc']>,
      required: true
    }
  },
  setup() {
    
  },
})
</script>

<style lang="scss" module>
@import '@/assets/styles/main.scss';
.imageWrapper {
  width: 50%;
  .image {
    width: 100%;
  }
}
</style>