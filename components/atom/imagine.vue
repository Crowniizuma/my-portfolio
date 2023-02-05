<template>
  <div>
    <img :src="imageSrc" :class="$style.imageSrc"/>
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
.imageSrc {
  width: 100%;
  position: relative;
  &::after {
    content: '';
    width: 300px;
    height: 350px;
    left: -10px;
    top: -10px;
    border: 5px solid $color1;
  }
}
</style>