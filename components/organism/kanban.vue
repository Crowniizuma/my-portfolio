<template>
  <div :class="$style.kanban">
    <div :class="$style.textWrapper">
      <p :class="$style.title1">{{$t("hi, i'm anh")}}</p>
      <p :class="$style.title2">{{$t("a front-end developer")}}</p>
      <a :class="$style.button" >
        <p :class="$style.buttonText">{{ $t('my resume') }}</p>
      </a>
    </div>
  </div>
</template>

<script>
import { defineComponent } from '@vue/composition-api'

export default defineComponent({
  setup() {
    
  },
})
</script>

<style lang="scss" module>
@import '@/assets/styles/main.scss';
.kanban {
  width: calc((2/3) * 100%);
  position: relative;
  .textWrapper {
    max-width: 600px;
    width: calc((600 / 1366) * 100vw);
    padding: 50px;
    background-color: rgba(212, 238, 195, 0.5);
    border-radius: 10%;
  
    .title1 {
      @include pc_standard {
        font-size: 64px;
      }
      font-size: calc((64 / 1366) * 100vw);
      font-weight: bold;
      color: #000;
      margin-bottom: 20px;
    }
  
    .title2 {
      @include pc_standard {
        font-size: 75px;
      }
      font-size: calc((80 / 1366) * 100vw);
      font-weight: bold;
      color: #68b04e;
      line-height: 1.25;
      margin-bottom: 40px;
    }
  
    .button {
      width: fit-content;
      display: flex;
      align-items: center;
      @include pc_standard {
        font-size: 32px;
        padding-top: 15px;
        padding-bottom: 15px;
        padding-right: 30px;
        padding-left: 70px;
      }
      padding-top: calc((15 / 1366) * 100vw);
      padding-bottom: calc((15 / 1366) * 100vw);
      padding-right: calc((30 / 1366) * 100vw);
      padding-left: calc((70 / 1366) * 100vw);
      background-color: #68b04e;
      border: 2px solid transparent;
      border-radius: 10px;
      cursor: pointer;
      position: relative;
      transition: color 0.2s ease-in-out;

      &::before {
        content: "";
        background-image: url('/image/home/arrow-right.svg');
        background-size: cover;
        position: absolute;
        @include pc_standard {
          width: 30.5px;
          height: 32.5px;
        }
        width: calc((30.5 / 1366) * 100vw);
        height: calc((32.5 / 1366) * 100vw);
        left: calc((20 / 1366) * 100vw);
      }
      .buttonText {
        @include pc_standard {
          font-size: 32px;
        }
        font-size: calc((32 / 1366) * 100vw);
        color: #fff;
        font-weight: bold;
      }
      &:hover {
        background-color: #fff;
        border: 2px solid #68b04e;

        &::before {
          background-image: url('/image/home/arrow-right-hover.svg');
        }
        .buttonText {
          color: #68b04e;
        }
      }
    }

  }
}
</style>