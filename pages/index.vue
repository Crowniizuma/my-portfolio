<template>
  <div :class="$style.home">
    <div :class="$style.homeWrapper">
      <OrganismKanban></OrganismKanban>
    </div>
  </div>
</template>
<script lang= "ts">
import kanban from "~~/components/organism/kanban.vue";


export default defineComponent({
  components: { kanban },
  setup() {
    
  },
})
</script>

<style lang="scss" module>
@import "@/assets/styles/main.scss";
.home {
  position: absolute;
  width: 100vw;
  top: 68px;
  .homeWrapper {
    max-width: 1280px;
    padding-left: 40px;
    padding-right: 40px;
    margin: auto;
    
  }
}
</style>
