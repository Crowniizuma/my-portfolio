<template>
  <div :class="$style.skillChartWrapper">
    <div :class="$style.titleWrapper">
      <p :class="$style.title">My skills</p>
    </div>
    <AtomChart :class="$style.chart"></AtomChart>
  </div>
</template>

<script lang="ts">

export default defineComponent({
  setup() {
    
  },
})
</script>

<style lang="scss" module>
@import "@/assets/styles/main.scss";
.skillChartWrapper {
  width: 100%;
  display: flex;
  column-gap: 10%;

  .titleWrapper {
    width: 40%;
    background-color: $color1;
    display: flex;
    justify-content: center;
    align-items: center;

    .title {
      @include pc_standard {
        font-size: 40px;
      }
      font-size: calc((40 / 1366) * 100vw);
      color: $color2;
    }
  }
}
</style>