<template>
  <div :class="$style.footer">
    <div :class="$style.footerWrapper">
      <div :class="$style.copyright">©️2023 nguyen anh</div>
      <MoleculeNav :is-footer-nav="true"></MoleculeNav>
    </div>
  </div>
</template>

<style lang="scss" module>
@import '@/assets/styles/main.scss';
.footer {
  width: 100vw;
  background: linear-gradient(45deg,$color3, $color1);
  z-index: 100;

  .footerWrapper {
    max-width: 1280px;
    margin: auto;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 15px 40px;  
    .copyright {
      color: $color2;
      @include pc_standard {
        font-size: 16px;
      }
      font-size: calc((16 / 1366) * 100vw);
      font-weight: bold;
      
    }
  }
}
</style>


