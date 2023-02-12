<template>
  <div ref="home" :class="[$style.home, scrolledToProjects ? $style.changeColor : undefined]">
    <div :class="$style.homeWrapper">
      <div :class="$style.kanbanWrapper">
        <OrganismKanban></OrganismKanban>
        <div :class="$style.scrollDownIcon" @click="scrollToLatestProject">
          <AtomScrollDownIcon></AtomScrollDownIcon>
        </div>
      </div>
      <div ref="myLatestProjects" :class="[$style.myLatestProjects, scrolledToProjects ? $style.reveal : undefined]">
        <p :class="$style.bigTitle">{{$t('my latest projects')}}</p>
        <MoleculeCoverFlowProjectsList></MoleculeCoverFlowProjectsList>
        <div :class="$style.more">
          <NuxtLink to="/projects" :class="$style.moreLink">
            <p>{{ $t('more projects') }}</p>
          </NuxtLink>
        </div>
      </div>
      <div ref="blogWrapper" :class="[$style.blogWrapper, scrolledToBlog ? $style.revealBlog : undefined]">
        <p :class="$style.bigTitle">{{$t('my latest blog')}}</p>
        <OrganismBlog v-bind="LatestBlog"></OrganismBlog>
        <div :class="$style.more">
          <NuxtLink to="/blog" :class="$style.moreLink">
            <p>{{ $t('more articles') }}</p>
          </NuxtLink>
        </div>
      </div>
    </div>
  </div>
</template>
<script lang= "ts">
import { Props as BlogProps} from '../components/organism/blog.vue'

export default defineComponent({

  setup(props) {
    //Change home color when scroll
    const myLatestProjects = ref<HTMLDivElement>();
    const home = ref<HTMLDivElement>();
    var scrolledToProjects = ref<Boolean>(false);
    var scrolledToBlog = ref<Boolean>(false);
    
    const scrollToLatestProject = () => {
      if(myLatestProjects.value && home.value) {
        let myLatestProjectsTop = myLatestProjects.value.offsetTop - 50;
        window.scrollTo({
          top: myLatestProjectsTop,
          behavior: 'smooth'
        })
      }
    }

    //projects appear
    const handleScroll = () => {
      console.log("handleScroll");
      if (myLatestProjects.value && home.value) {
        let myLatestProjectsTop = myLatestProjects.value.offsetTop - 100;
        let myLatestProjectsBottom = myLatestProjectsTop + myLatestProjects.value.offsetHeight - 100;
        let windowTop = window.pageYOffset;
        console.log(windowTop, myLatestProjectsTop, myLatestProjectsBottom)
        if(myLatestProjectsTop < windowTop && myLatestProjectsBottom > windowTop) {
          scrolledToProjects.value = true;
          scrolledToBlog.value = false;
        } else {
          scrolledToProjects.value = false;
          scrolledToBlog.value = true;
        }
      }
    }

    onMounted(() => {
      window.addEventListener('scroll', handleScroll);
    });

    //blog
    const LatestBlog = ref<BlogProps>(
      {
        blogLink: "",
        blogThumbnailLink: "https://i.pinimg.com/originals/6a/47/14/6a47145dc35300b4af586067d3743dd2.jpg",
        blogDate:"2023/01/25",
        blogTitle: "Living in Japan",
        blogContent: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
        hashTagContent: "#living-in-japan",
        isHover: false
      }
    )
    return {
      myLatestProjects,
      home,
      scrolledToProjects,
      handleScroll,
      scrollToLatestProject,
      LatestBlog,
      scrolledToBlog
    }
  },
})
</script>

<style lang="scss" module>
@import "@/assets/styles/main.scss";
.home {
  width: 100vw;
  &.changeColor {
    background: linear-gradient(180deg, $color1 0%, $color3 100%);
  }
  .homeWrapper {
    max-width: 1280px;
    margin: auto;
    @include pc {
      padding-left: 40px;
      padding-right: 40px;
    }
    @include pc_standard {
      padding-top: 150px;
    }
    padding-top: calc((150 / 1366) * 100vw);
    padding-left: calc((40 / 1366) * 100vw);
    padding-right: calc((40 / 1366) * 100vw);

    .kanbanWrapper {
      height: 700px;
      .scrollDownIcon {
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        margin-top: 50px;
        cursor: pointer;
      }
    }
    .bigTitle {
      font-weight: bold;
      margin-bottom: 50px;
      @include pc_standard {
        font-size: 40px;
      }
      font-size: calc((40 / 1366) * 100vw);
      color: #000;
      text-shadow: 5px 5px $color3;
    }

    .more {
      width: 100%;
      display: flex;
      justify-content: flex-end;
      margin-top: 20px;
      .moreLink {
        position: relative;
        display: block;
        padding: 15px;
        padding-left: 50px;
        color: #fff;
        @include pc_standard {
          font-size: 20px;
        }
        font-size: calc((20 / 1366) * 100vw);
        font-weight: bold;
        background-color: #000;
        border-radius: 10px;

        &::before {
          content: '';
          background-image: url('/image/home/more-arrow.svg');
          background-size: cover;
          height: calc((24 / 20) * 1em);
          width: calc((27 / 20) * 1em);
          position: absolute;
          left: calc((15 / 20) * 1em);
          top: 50%;
          transform: translate(0, -50%);
          transition: all 0.2s ease;
        }

        &::after {
          content: '';
          background-image: url('/image/home/more-arrow.svg');
          background-size: cover;
          height: calc((24 / 20) * 1em);
          width: calc((27 / 20) * 1em);
          position: absolute;
          left: calc((15 / 20) * 1em);
          top: 50%;
          transform: translate(-20px, -50%);
          opacity: 0;
          transition: all 0.2s ease;
        }

        &:hover {
          &::before {
            transform: translate(20px, -50%);
            opacity: 0;
            transition: all 0.2s ease;
          }
          &::after {
            transform: translate(0, -50%);
            opacity: 1;
            transition: all 0.2s ease;
          }
        }

      }
    }
    .myLatestProjects {
      padding-top: 100px;
      @include pc_standard {
        height: 700px;
      }
      height: calc((700 / 1366) * 100vw + 100px);
      transform: translateY(150px);
      opacity: 0;
      transition: all 0.5s ease;

      .bigTitle {
        text-shadow: 5px 5px $color2;
      }
      &.reveal {
        transform: translateY(0);
        opacity: 1;
      }

    }
    
    .blogWrapper {
      padding-top: 50px;
      padding-bottom: 200px;
      transform: translateY(150px);
      opacity: 0;
      transition: all 0.5s ease;

      &.revealBlog {
        transform: translateY(0);
        opacity: 1;
      }
      
    }
  }
}
</style>
