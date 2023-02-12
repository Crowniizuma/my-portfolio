<template>
  <div :class="$style.kanban">
    <div :class="$style.imageWrapper">
      <img src="/image/home/home-pic.png"/>
    </div>
    <div :class="$style.textWrapper">
      <div :class="$style.title1Wrapper">
        <p :class="[$style.title1, $style.typingEffect]">{{$t("hi, i'm Anh")}}</p>
      </div>
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
  position: relative;
  //max-height: 400px;

  &::before {
    content: '';
    position: absolute;
    @include pc_standard {
      width: 500px;
      height: 495px;
      left: 80px;
      top: 0;
    }
    width: calc((500 / 1200) * 100%);
    height: calc((495 / 1366) * 100vw);
    left: calc((80 / 1200) * 100%);
    top: 0;
    border-radius: 50%;
    background: linear-gradient($color3, $color1);
    
  }
  
  .imageWrapper {
    z-index: 1;
    img {
      max-width: 400px;
      width: calc((400 / 1366) * 100vw);
    }
  }
  .textWrapper {
    max-width: 600px;
    width: calc((600 / 1366) * 100vw);
    @include pc_standard {
      padding: 70px;  
    }
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding-left: calc((70 / 1366) * 100vw);
    background-color: rgba(234, 220, 166, 0.5);
    border-radius: 10%;
    z-index: 2;
    
    .title1Wrapper {
      width: fit-content;
      .title1 {
        @include pc_standard {
          font-size: 60px;
        }
        font-size: calc((60 / 1366) * 100vw);
        font-weight: bold;
        color: #000;
        margin-bottom: 20px;
      }
    }
  
    .title2 {
      @include pc_standard {
        font-size: 70px;
      }
      font-size: calc((70 / 1366) * 100vw);
      font-weight: bold;
      color: #000;
      line-height: 1.25;
      margin-bottom: 50px;
      text-shadow: 10px 10px 6px $color1;
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
      background-color: #000;
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
          font-size: 30px;
        }
        font-size: calc((30 / 1366) * 100vw);
        color: $color2;
        font-weight: bold;
      }
      &:hover {
        background-color: $color2;
        border: 2px solid $color1;

        &::before {
          background-image: url('/image/home/arrow-right-hover.svg');
        }
        .buttonText {
          color: $color1;
        }
      }
    }

    .typingEffect {
      width: 0;
      overflow: hidden; /* Ensure the text is not visible until the typewriter effect*/
      border-right: 2px solid #000; /* The cursor*/
      white-space: nowrap; /* Keeps the text on a single line */
      animation: typing 2s steps(30) forwards, blink 1s infinite;
    }

    /* The typing animation */
    @keyframes typing {
      from { width: 0 }
      to { width: 100% }
    }

    @keyframes blink {
      0%, 45% {
        border-color: transparent;
      }
      50%, 100% {
        border-color: #000;
      }
    }
  }
}
</style>