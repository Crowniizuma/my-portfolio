<template>
  <div :class="$style.scrollDownWrapper">
    <span></span>
    <span></span>
    <span></span>
  </div>
</template>

<script lang="ts">

export default defineComponent({
  setup() {
    
  },
})
</script>

<style lang="scss" module>
@import '@/assets/styles/main.scss';
  .scrollDownWrapper {
    span {
      display: block;
      width: 20px;
      aspect-ratio: 1/1;
      border-bottom: 2px solid $color1;
      border-right: 2px solid $color1;
      transform: rotate(45deg);
      margin: -10px;
      animation: animate 2s infinite;

      &:nth-child(2) {
        animation-delay: -0.2s;
      }

      &:nth-child(3) {
        animation-delay: -0.4s;
      }
    }

    @keyframes animate{
      0%{
        opacity: 0;
        transform: rotate(45deg) translate(-20px, -20px);
      }
      50%{
        opacity: 1;
      }
      100%{
        opacity: 0;
        transform: rotate(45deg) translate(20px, 20px);
      }
    }
  }
</style>