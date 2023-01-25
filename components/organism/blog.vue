<template>
  <div :class="$style.blog">
      <div @mouseover="hover" @mouseleave="unhover" :class="[$style.blogThumbnail, isHover ? $style.hoverThumbnail : undefined]">
        <img :src="blogThumbnailLink" />
      </div>
      <div :class="$style.contentWrapper">
        <AtomHashTag :class="$style.hashtag" :hashtag-content="hashTagContent"></AtomHashTag>
        <p :class="$style.blogDate">{{ $t(blogDate) }}</p>
        <p :class="$style.blogTitle">{{ $t(blogTitle) }}</p>
        <p :class="$style.blogContent">{{ $t(blogContent) }}</p>
        <a @mouseover="hover" @mouseleave="unhover" :href="blogLink" :class="[$style.readMoreButton, isHover ? $style.hoverReadMoreButton : undefined]">{{ $t("Read more") }}</a>
      </div>
  </div>
</template>

<script lang="ts">
import { PropType } from 'vue';
export type Props = {
  blogLink: string,
  blogThumbnailLink: string,
  blogDate: string,
  blogTitle: string,
  blogContent: string,
  hashTagContent: string,
  isHover: boolean
}

export default defineComponent({
  props: {
    blogLink: {
      type: String as PropType<Props['blogLink']>,
      required: true
    },
    blogThumbnailLink: {
      type: String as PropType<Props['blogThumbnailLink']>,
      required: true
    },
    blogDate: {
      type: String as PropType<Props['blogDate']>,
      required: true
    },
    blogTitle: {
      type: String as PropType<Props['blogTitle']>,
      required: true
    },
    blogContent: {
      type: String as PropType<Props['blogContent']>,
      required: true
    },
    hashTagContent: {
      type: String as PropType<Props['hashTagContent']>,
      required: true
    },
    isHover: {
      type: Boolean as PropType<Props['isHover']>,
      required: false,
      default: false
    }
  },
  setup() {
    var isHover = ref<Boolean>(false);
    const hover = () => {
      isHover.value = true;
    }
    const unhover = () => {
      isHover.value = false;
    }
    return {
      isHover,
      hover,
      unhover
    }
  },
})
</script>

<style lang="scss" module>
@import "@/assets/styles/main.scss";
.blog {
  width: 100%;
  display: flex;
  column-gap: calc((50 / 1200) * 100%);
  text-decoration: none;
  align-items: center;
  @include pc_standard {
    height: 300px;
  }
  height: calc((300 / 1366) * 100vw);
  .blogThumbnail {
    width: calc((500 / 1200) * 100%);
    position: relative;
    img {
      object-fit: cover;
      max-width:100%;
      max-height:100%;
      height:100%;
      width:100%;
      border-radius: 10px;
      transition: all 0.3s;
      clip-path: inset(0);
    }

    &::before {
      content: "";
      border: 35px solid $color1;
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      border-radius: 10px;
      transition: border-width 0.3s ease-out;
      box-sizing: border-box;
      z-index: -100; 
    }

    &:hover{
      &::before {
        border: 5px solid $color1;
      }

      img {
        clip-path: inset(35px round 10px);
      }
    }

    &.hoverThumbnail {
      &::before {
        border: 5px solid $color1;
      }

      img {
        clip-path: inset(35px round 10px);
      }
    }
  }

  .contentWrapper {
    width: calc((650 / 1200) * 100%);
    .blogDate {
      color: rgba(95, 95, 95, 0.6);
      @include pc_standard {
        font-size: 13px;
      }
      font-size: calc((13 / 1366) * 100vw);
      margin-bottom: 15px;
    }

    .blogTitle {
      color: #000;
      font-weight: bold;
      @include pc_standard {
        font-size: 32px;
      }
      font-size: calc((32 / 1366) * 100vw);
      margin-bottom: 30px;
      position: relative;

      &::after {
        content: '';
        width: calc((300 / 650) * 100%);
        height: 2px;
        background-image: linear-gradient(180deg, $color4 0%, $color5 100%);
        position: absolute;
        left: 0;
        bottom: -10px;
      }
    }

    .blogContent {
      color: #000;
      @include pc_standard {
        font-size: 16px;
      }
      font-size: calc((16 / 1366) * 100vw);
      margin-bottom: 30px;
    }

    .hashtag {
      margin-bottom: 20px;
    }

    .readMoreButton {
      border: 2px solid $color1;
      padding: 10px;
      border-radius: 5px;
      color: $color1;
      transition: color 0.2s ease;

      &:hover{
        background-color: $color1;
        color: #fff;
      }

      &.hoverReadMoreButton {
        background-color: $color1;
        color: #fff;
      }
    }
  }
}
</style>