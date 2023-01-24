<template>
  <div ref="home" :class="[$style.home, scrolledToBottom ? $style.changeColor : undefined]">
    <div :class="$style.homeWrapper">
      <div :class="$style.kanbanWrapper">
        <OrganismKanban></OrganismKanban>
        <div :class="$style.scrollDownIcon" @click="scrollToNewestProject">
          <AtomScrollDownIcon></AtomScrollDownIcon>
        </div>
      </div>
      <div ref="myNewestProjects" :class="[$style.myNewestProjects, scrolledToBottom ? $style.reveal : undefined]">
        <p :class="$style.bigTitle">{{$t('my newest projects')}}</p>
        <OrganismCoverFlowProjectsList></OrganismCoverFlowProjectsList>
      </div>
    </div>
  </div>
</template>
<script lang= "ts">


export default defineComponent({

  setup() {
    const myNewestProjects = ref<HTMLDivElement>();
    const home = ref<HTMLDivElement>();
    var scrolledToBottom = ref<Boolean>(false);
    const scrollToNewestProject = () => {
      if(myNewestProjects.value && home.value) {
        let myNewestProjectsTop = myNewestProjects.value.offsetTop;
        window.scrollTo({
          top: myNewestProjectsTop,
          behavior: 'smooth'
        })
      }
    }
    const handleScroll = () => {
      console.log("handleScroll");
      if (myNewestProjects.value && home.value) {
        let myNewestProjectsTop = myNewestProjects.value.offsetTop - 100;
        console.log(myNewestProjectsTop)
        let windowTop = window.pageYOffset;
        if(myNewestProjectsTop < windowTop) {
          scrolledToBottom.value = true;
        } else {
          scrolledToBottom.value = false;
        }
      }
    }
    onMounted(() => {
      window.addEventListener('scroll', handleScroll);
    });
    return {
      myNewestProjects,
      home,
      scrolledToBottom,
      handleScroll,
      scrollToNewestProject
    }
  },
})
</script>

<style lang="scss" module>
@import "@/assets/styles/main.scss";
.home {
  width: 100vw;
  transition: background-color 0.2s ease-out;
  &.changeColor {
    background-color: $color3;
  }
  .homeWrapper {
    max-width: 1280px;
    padding-left: 40px;
    padding-right: 40px;
    margin: auto;
    @include pc_standard {
    padding-top: 150px;
    }
    padding-top: calc((150 / 1366) * 100vw);

    .kanbanWrapper {
      height: 700px;
      .scrollDownIcon {
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        margin-top: 100px;
        cursor: pointer;
      }
    }
    .bigTitle {
      font-weight: bold;
      margin-bottom: 50px;
      display: flex;
      justify-content: flex-end;
      @include pc_standard {
        font-size: 32px;
      }
      font-size: calc((32 / 1366) * 100vw);
      color: $color2;

    }
    .myNewestProjects {
      padding-top: 100px;
      transform: translateY(150px);
      opacity: 0;
      transition: all 0.5s ease;

      &.reveal {
        transform: translateY(0);
        opacity: 1;
      }
    }
    
  }
}
</style>
