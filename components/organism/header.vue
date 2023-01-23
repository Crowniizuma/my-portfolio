<template>
  <div :class="$style.header">
    <div :class="$style.headerWrapper">
      <MoleculeNav></MoleculeNav>
      <a-select v-model:value="$i18n.locale" :options="localeOptions">
      </a-select>
    </div>
  </div>
</template>

<script lang="ts">
import { SelectProps } from 'ant-design-vue/es/select';
export default defineComponent({
  setup() {
    const localeOptions = ref<SelectProps['options']>([
      {
        value: 'en',
        label: 'English',
        bordered: false 
      },
      {
        value: 'ja',
        label: '日本語',
        bordered: false 
      }
    ])
    return {
      localeOptions
    }
  },
})
</script>

<style lang="scss" module>
@import '@/assets/styles/main.scss';
.header {
  width: 100vw;
  position: fixed;
  background-color: rgba(255, 255, 255, 0.5);
  z-index: 100;
  .headerWrapper {
    max-width: 1280px;
    margin: auto;
    width: 100%;
    display: flex;
    @include pc_standard {
      column-gap: 50px;
    }
    padding: 15px 40px;  
    column-gap: calc((50/1366)*100vw);
    justify-content: right;
    align-items: center;

  }
}
</style>
