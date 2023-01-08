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
  position: absolute;
  bottom: 0;
  width: 100vw;
  background-color: #68b04e;

  .footerWrapper {
    max-width: 1280px;
    margin: auto;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    @include pc_standard {
      padding: 15px 40px;  
    }
    padding: 15px calc((40/1366) * 100vw);
    .copyright {
      color: #fff;
      @include pc_standard {
        font-size: 16px;
      }
      font-size: calc((16 / 1366) * 100vw);
      font-weight: bold;
      
    }
  }
}
</style>


