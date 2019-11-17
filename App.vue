<template>
  <div id="app">
    <!-- 需求  根据不同需求 实现不同的动画 -->
    <transition :name="transitionName" mode="out-in">
    <router-view class="router-view"></router-view>
    </transition>
    <FooterBar v-if="$route.meta.isShow"></FooterBar>
  </div>
</template>
<script>

import FooterBar from "@/components/FooterBar.vue";
export default {
  name: "app",
  data(){
    return {
      transitionName:'fade'
    }
  },
  components: {
    FooterBar
  },
  watch: {
    $route(to, from) {
      const tabPath = [
        "/home",
        "/cinema",
        "/movie",
        "/ticket",
        "/main"
      ];
      if (
        tabPath.some(item => item == to.path) &&
        tabPath.some(item => item == from.path)
      ) {
        this.transitionName = "fade";
      } else {
        // console.log('to.path',to.path)
        const toDepth = to.path.split("/").length;
        const fromDepth = from.path.split("/").length;
        this.transitionName =
          toDepth < fromDepth ? "slide-right" : "slide-left";
      }
    }
  }
};
</script>
<style lang="scss">
body {
  background-color: #23262d;
}
html,
body {
  height: 100%;
  width: 100%;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
  
 
}
a{
  //用于取消 a标签 高亮显示 
  -webkit-tap-highlight-color: transparent;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
.router-view{
    //避免头部 动画异常
  overflow-x: hidden;
}
.slide-left-enter-active {
  animation: slideLeft 0.4s;
}
.slide-right-enter-active {
  animation: slideRight 0.4s;
}
.fade-enter-active {
  transition: all ease 0.2s;
}
.fade-enter {
  opacity: 0;
}
@keyframes slideLeft {
  0% {
    opacity: 0;
    transform: translateX(100%);
  }
  100% {
    transform: translateX(0);
    opacity: 1;
  }
}
 
@keyframes slideRight {
  0% {
    opacity: 0;
    transform: translateX(-100%);
  }
  100% {
    transform: translateX(0);
    opacity: 1;
  }
}
</style>
