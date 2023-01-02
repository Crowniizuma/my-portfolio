<template>
  <div :class="$style.nav">
    <ul :class="$style.navLinkList">
      <AtomNavLink v-for="route in routes" v-bind="route" :key="route.link" @click="handleClick(route)"></AtomNavLink>
    </ul>
    <ul :class="$style.snsLinkList">
      <AtomSnsLink v-for="sns in snsLinks" v-bind="sns" :key="sns.link"></AtomSnsLink>
    </ul>
    <select id="locale-select" v-model="$i18n.locale">
      <option value="en">en</option>
      <option value="ja">ja</option>
    </select>
  </div>
</template>

<script lang="ts">
import {Props as NavLinkProps} from "../atom/navLink.vue";
import {Props as SnsLinkProps} from "../atom/snsLink.vue";
export default defineComponent({
  setup() {
    const routes = ref<Array<NavLinkProps>>([
      {
        link: "/",
        title: "home",
      },
      {
        link: "/about",
        title: "about"
      },
      {
        link: "/projects",
        title: "projects"
      },
      {
        link: "/blog",
        title: "blog"
      },
    ])

    const snsLinks = ref<Array<SnsLinkProps>>([
      {
        link: "https://www.linkedin.com/in/nguyen-thi-hoang-anh-b7688a193/",
        imgSource: "@/assets/image/sns/icons8-linkedin-circled-50.png"
      },
      {
        link: "https://github.com/Crowniizuma",
        imgSource: "@/assets/image/sns/icons8-github-48.png"
      },
      {
        link: "mailto: nthoanganh10997@gmail.com",
        imgSource: "@/assets/image/sns/icons8-mail-50.png"
      }
    ])

    const handleClick = (target: NavLinkProps) => {
      for(const route of routes.value) {
        route.isClicked = false;
      }
      target.isClicked = true;
    }
    return {
      routes,
      handleClick,
      snsLinks
    };
  },
})
</script>

<style lang="scss" module>
.nav{
  display: flex;
  column-gap: calc((50/1366)*100vw);
  justify-content: right;
  width: calc(100vw - 200px);
  padding: 25px 100px;
  .navLinkList {
    display: flex;
    column-gap: calc((50/1366)*100vw);
    justify-content: right;
    align-items: center;
    list-style: none;
  }
  
  .snsLinkList {
    display: flex;
    flex-direction: row;
    column-gap: calc((30/1366)*100vw);
    justify-content: flex-start;
    list-style: none;
  }
}


</style>