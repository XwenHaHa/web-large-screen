<template>
  <div class="nav-wrapper">
    <div class="bar-title" @click.stop="toHome">轴承匹配系统</div>
  </div>
</template>

<script>
import { computed } from 'vue'
import useResize from '@/componentApi/useResize.js'
import { useRoute, useRouter } from 'vue-router'

export default {
  name: 'navBar',

  setup(props, context) {
    const router = useRouter()
    const route = useRoute()
    const { parentInfo, removeCommitMapInfo } = useResize()
    let isHome = computed(() => route.path == '/homepage')

    const chooseArea = (item, index) => {
      if (parentInfo.value.length === index + 1) {
        return
      }
      removeCommitMapInfo(index + 1)
    }

    const toHome = () => {
      if (route.path == '/homepage') {
        return
      }
      router.push('/homepage')
    }

    return {
      parentInfo,
      chooseArea,
      toHome,
      isHome
    }
  }
}
</script>

<style lang="scss" scoped>
.nav-wrapper {
  height: 65px;
  line-height: 50px;
  width: 100%;
  background: url('../../assets/image/nav.png') no-repeat;
  background-size: 100% 100%;
  text-align: center;
  position: relative;
  color: #b3efff;

  .bar-title {
    font-size: 1.23rem;
    font-family: '黑体';
    cursor: pointer;
  }

  .mapChoose {
    position: absolute;
    left: 10px;
    bottom: -5px;
    color: #eee;

    .title {
      padding: 4px;
      border-top: 1px solid rgba(147, 235, 248, 0.8);
      border-bottom: 1px solid rgba(147, 235, 248, 0.8);
      cursor: pointer;
      font-size: 14px;
    }

    .icon {
      font-family: 'simsun';
      font-size: 25px;
      margin: 0 11px;
    }
  }
}
</style>
