<template>
  <a :href="projectLink">
    <div :class="$style.project" :style="'background-image: url(' + backgroundImage + ')'">
      <div :class="$style.textWrapper">
        <p :class="$style.title">{{ $t(title) }}</p>
        <p :class="$style.content">{{ $t(content) }}</p>
      </div>
    </div>
  </a>
</template>

<script lang="ts">
import { PropType } from 'vue';

export type Props = {
  projectLink: string,
  backgroundImage: string,
  title : string,
  content : string
}
export default defineComponent({
  props: {
    projectLink: {
      type: String as PropType<Props['projectLink']>,
      required: false,
      default: ""
    },
    backgroundImage: {
      type: String as PropType<Props['backgroundImage']>,
      required: true
    },
    title: {
      type: String as PropType<Props['title']>,
      required: true
    },
    content: {
      type: String as PropType<Props['content']>,
      required: true
    }
  },
  setup() {
    
  },
})
</script>

<style module lang="scss">
@import '@/assets/styles/main.scss';
.project {
  width: 100%;
  aspect-ratio: 1/1;
  background-size: cover;
  border-radius: 5% !important;
  .textWrapper {
    position: absolute;
    bottom: 0;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 10%;
    background-color: rgba(0, 0, 0, 0.5);
    height: 0;
    opacity: 0;
    transition: all 0.2s ease-in-out; 
    border-radius: 5%;

    .title {
      font-weight: bold;
      font-size: calc((40 / 360) * 100%);
      @include pc_standard {
        font-size: 40px;
      }
      color: $color2;
      margin-bottom: 10%;
    }
  
    .content {
      font-size: calc((14 / 360) * 100%);
      @include pc_standard {
        font-size: 14px;
      }
      color: $color2;
    }


  }

  &:hover {
    .textWrapper {
      opacity: 1;
      height: 100%;
      transition: all 0.2s ease-in-out; 
    }
  }
}
</style>
