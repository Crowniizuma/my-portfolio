<template>
  <div :class="$style.nav">
    <div :class="$style.navLinkList">
      <AtomNavLink v-for="route in routes" v-bind="route" :key="route.link"></AtomNavLink>
    </div>
    <div :class="$style.snsLinkList">
      <AtomSnsLink v-for="sns in snsLinks" v-bind="sns" :key="sns.link"></AtomSnsLink>
    </div>
  </div>
</template>

<script lang="ts">
import { PropType } from "vue";
import {Props as NavLinkProps} from "../atom/navLink.vue";
import {Props as SnsLinkProps} from "../atom/snsLink.vue";

export type Props = {
  isFooterNav: boolean
}

export default defineComponent({
  props: {
    isFooterNav: {
      type: Boolean as PropType<Props['isFooterNav']>,
      required: false,
      default: false
    }
  },
  setup(props) {
    const $route = useRoute();
    const routes = ref<Array<NavLinkProps>>([
      {
        link: "/",
        title: "home",
        isFooter: props.isFooterNav,
        isVisiting: $route.path === "/"
      },
      {
        link: "/about",
        title: "about",
        isFooter: props.isFooterNav,
        isVisiting: $route.path === "/about"
      },
      {
        link: "/projects",
        title: "projects",
        isFooter: props.isFooterNav,
        isVisiting: $route.path === "/projects"
      },
      {
        link: "/blog",
        title: "blog",
        isFooter: props.isFooterNav,
        isVisiting: $route.path === "/blog"
      },
    ])
    
    const snsLinks = ref<Array<SnsLinkProps>>([
      {
        link: "https://www.linkedin.com/in/nguyen-thi-hoang-anh-b7688a193/",
        imgSourceHeader: "/image/sns/linkedin-header.png",
        imgSourceFooter: "/image/sns/linkedin-footer.png",
        isSnsFooter: props.isFooterNav
      },
      {
        link: "https://github.com/Crowniizuma",
        imgSourceHeader: "/image/sns/github-header.png",
        imgSourceFooter: "/image/sns/github-footer.png",
        isSnsFooter: props.isFooterNav
      },
      {
        link: "mailto: nthoanganh10997@gmail.com",
        imgSourceHeader: "/image/sns/mail-header.png",
        imgSourceFooter: "/image/sns/mail-footer.png",
        isSnsFooter: props.isFooterNav
      }
    ])
    
    watch(
      () => $route.path, 
      (newPathName) => {
      console.log('newPathName', newPathName)
      for(const route of routes.value) {
        if(route.link == newPathName) {
          route.isVisiting = true;
        } else {
          route.isVisiting = false;
        }
      }
    }) 
    return {
      routes,
      snsLinks
    };
  },
})
</script>

<style lang="scss" module>
@import '@/assets/styles/main.scss';
.nav{
  display: flex;
  @include pc_standard {
    column-gap: 50px;
  }
  column-gap: calc((50/1366)*100vw);
  justify-content: right;
  align-items: center;
  .navLinkList {
    display: flex;
    @include pc_standard {
    column-gap: 50px;
    }
    column-gap: calc((50/1366)*100vw);
    justify-content: right;
    align-items: center;
    list-style: none;
  }
  
  .snsLinkList {
    display: flex;
    flex-direction: row;
    @include pc_standard {
    column-gap: 30px;
    }
    column-gap: calc((30/1366)*100vw);
    justify-content: flex-start;
    list-style: none;
  }
}
</style>