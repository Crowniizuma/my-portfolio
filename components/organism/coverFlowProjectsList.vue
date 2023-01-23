<template>
  <div :class="$style.projectSlide">
    <swiper 
      :effect="'coverflow'"
      :grabCursor="true"
      :centeredSlides="true"
      :slidesPerView="'auto'"
      :coverflowEffect="{
        rotate: 0,
        stretch: 0,
        depth: 100,
        modifier: 2,
        slideShadows: true
      }"
      :spaceBetween="100"
      :loop="true"
      :pagination="true"
      :modules="modules"
      :class="$style.swiper"
    >
      <swiper-slide v-for="project in projects" :key="project.title" :class="$style.swiperSlide">
        <AtomProject v-bind="project" ></AtomProject>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/effect-coverflow";
import "swiper/css/pagination";
import { EffectCoverflow, Pagination } from "swiper";

import {Props as ProjectProps} from "../atom/project.vue";

export default defineComponent({
  components: {
    Swiper,
    SwiperSlide
  },
  setup(props) {
    const projects = ref<Array<ProjectProps>>([
      { 
        projectLink: "",
        backgroundImage: "https://i.pinimg.com/564x/4f/83/9e/4f839ee9c09222b873ad0db5eba2730e.jpg",
        title: "Title",
        content: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
      },
      {
        projectLink: "",
        backgroundImage: "https://i.pinimg.com/564x/27/a6/6a/27a66a3f173ea74f6e879322ab19b200.jpg",
        title: "Title",
        content: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
      },
      {
        projectLink: "",
        backgroundImage: "https://i.pinimg.com/564x/64/94/e6/6494e607d7d4101a5b875e706678a341.jpg",
        title: "Title",
        content: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
      }
    ])
    return {
      modules: [EffectCoverflow, Pagination],
      projects
    }
  },
})
</script>

<style module lang="scss">
.projectSlide {
  width: 100%;
  height: 1000px;
  .swiper {
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
    width: 100%;

    .swiperSlide {
      width: 30% !important;
    }

    
  }
}


</style>

<style lang="scss">
@import "@/assets/styles/main.scss";
.swiper-3d .swiper-slide-shadow-right {
  background: none;
}
.swiper-3d .swiper-slide-shadow-left {
  background: none;
}
.swiper-pagination {
  z-index: 100;
  .swiper-pagination-bullet-active  {
    background-color: $color1 !important;
  }
}
</style>