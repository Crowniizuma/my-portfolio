<template>
  <NuxtLink :to="link" :class="[isVisiting? $style.visiting : $style.header, isFooter? $style.footer : $style.header, $style.link ]">{{ $t(title) }}</NuxtLink>
</template>
<script lang="ts">
import { PropType } from 'vue';

export type Props = {
  link: string,
  title: string,
  isVisiting?: boolean,
  isFooter?: boolean
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
    isVisiting: {
      type: Boolean as PropType<Props['isVisiting']>,
      required: false,
      default: false 
    },
    isFooter: {
      type: Boolean as PropType<Props['isFooter']>,
      required: false,
      default: false 
    },
  },
  setup(props) {
    
  },
})
</script>

<style lang="scss" module>
@import '@/assets/styles/main.scss';
.link {

  @include pc_standard {
    font-size: 16px;
  }
  font-size: calc((16 / 1366)*100vw);
  font-weight: bold;
  &.header {
    color: $color1;
    display: inline-block;
    position: relative;

    &::after {
      content: '';
      position: absolute;
      width: 100%;
      transform: scaleX(0);
      height: 2px;
      bottom: -5px;
      left: 0;
      background-color: $color1;
      transform-origin: bottom right;
      transition: transform 0.25s ease-out;
    }

    &:hover::after {
      transform: scaleX(1);
      transform-origin: bottom left;
    }
    &.visiting {
      &::after {
        content: '';
        transform: none;
      }
    }
  }

  &.footer {
    color: $color2;
  }
}
</style>
