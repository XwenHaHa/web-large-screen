<template>
  <div class="app-container">
    <nav-bar />
    <div class="main-container">
      <router-view v-slot="{ Component }">
        <keep-alive include="homepage,more">
          <component :is="Component" />
        </keep-alive>
      </router-view>
    </div>
  </div>
</template>

<script>
import navBar from './components/navBar'
import { useRoute } from 'vue-router'
export default {
  name: 'layout',
  components: {
    navBar
  },
  setup() {
    const keepAlive = useRoute().meta.keepAlive

    return {
      keepAlive
    }
  }
}
</script>

<style lang="scss" scoped>
.app-container {
  width: 100%;
  height: 100%;
  position: relative;
  background: rgba(1, 53, 103);
  background-size: cover;

  .main-container {
    height: calc(100% - 65px);
    box-sizing: border-box;
    padding-bottom: 10px;
    width: 100%;
  }
}
</style>
