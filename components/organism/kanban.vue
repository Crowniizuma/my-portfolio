<template>
  <div :class="$style.kanban">
    <div :class="$style.imageWrapper">
      <img src="/image/home/home-pic.png"/>
    </div>
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
  width: 100%;
  display: flex;
  justify-content: center;
  @include pc_standard {
    margin-top: 50px;
  }
  margin-top: calc((50 / 1366) * 100vw);
  position: relative;

  &::before {
    content: '';
    position: absolute;
    @include pc_standard {
      width: 400px;
      height: 395px;
      left: 150px;
      top: 0;
    }
    width: calc((400 / 1200) * 100%);
    height: calc((395 / 1366) * 100vw);
    left: calc((150 / 1200) * 100%);
    top: 0;
    border-radius: 50%;
    background-color: #68b04e;
    z-index: -1;
  }
  
  .imageWrapper {
    
    
    img {
      max-width: 300px;
      width: calc((300 / 1366) * 100vw);
    }
  }
  .textWrapper {
    max-width: 500px;
    width: calc((500 / 1366) * 100vw);
    @include pc_standard {
      padding: 40px;  
    }
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding-left: calc((40 / 1366) * 100vw);
    background-color: rgba(212, 238, 195, 0.5);
    border-radius: 10%;
  
    .title1 {
      @include pc_standard {
        font-size: 45px;
      }
      font-size: calc((45 / 1366) * 100vw);
      font-weight: bold;
      color: #000;
      margin-bottom: 10px;
    }
  
    .title2 {
      @include pc_standard {
        font-size: 60px;
      }
      font-size: calc((60 / 1366) * 100vw);
      font-weight: bold;
      color: #68b04e;
      line-height: 1.25;
      margin-bottom: 20px;
    }
  
    .button {
      width: fit-content;
      display: flex;
      align-items: center;
      @include pc_standard {
        padding-top: 10px;
        padding-bottom: 10px;
        padding-right: 20px;
        padding-left: 40px;
      }
      padding-top: calc((15 / 1366) * 100vw);
      padding-bottom: calc((15 / 1366) * 100vw);
      padding-right: calc((30 / 1366) * 100vw);
      padding-left: calc((40 / 1366) * 100vw);
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
          width: 19.5px;
          height: 21px;
          left: 10px;
        }
        width: calc((19.5 / 1366) * 100vw);
        height: calc((21 / 1366) * 100vw);
        left: calc((10 / 1366) * 100vw);
      }
      .buttonText {
        @include pc_standard {
          font-size: 20px;
        }
        font-size: calc((20 / 1366) * 100vw);
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