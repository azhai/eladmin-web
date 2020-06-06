<template>
  <div :class="[{'collapse':collapse}, 'sidebar-logo-container']">
    <transition name="sidebarLogoFade">
      <router-link :key="collkey" class="sidebar-logo-link" to="/">
        <img v-if="logo" :src="logo" alt="logo" class="sidebar-logo">
        <h1 v-show="!collapse" class="sidebar-title">{{ title }}</h1>
      </router-link>
    </transition>
  </div>
</template>

<script>
import Logo from '@/assets/images/small_logo.png'
export default {
  name: 'SidebarLogo',
  props: {
    collapse: {
      type: Boolean,
      required: true
    }
  },
  data() {
    return {
      logo: Logo,
      title: process.env.VUE_APP_TITLE,
      collkey: this.collapse ? 'collapse' : 'expand'
    }
  }
}
</script>

<style lang="scss" scoped>
.sidebarLogoFade-enter-active {
  transition: opacity 1.5s;
}

.sidebarLogoFade-enter,
.sidebarLogoFade-leave-to {
  opacity: 0;
}

.sidebar-logo-container {
  position: relative;
  width: 100%;
  height: 50px;
  line-height: 50px;
  overflow: hidden;

  & .sidebar-logo-link {
    height: 100%;
    width: 100%;
    text-align: center;

    & .sidebar-logo {
      width: 32px;
      height: 32px;
      background: #fff;
      border-radius: 50%;
      padding: 3px;
      margin-right: 6px;
      vertical-align: middle;
    }

    & .sidebar-title {
      display: inline-block;
      color: #fff;
      font-weight: 600;
      line-height: 32px;
      font-size: 14px;
      font-family: Avenir, Helvetica Neue, Arial, Helvetica, sans-serif;
      vertical-align: middle;
      margin-left: 6px;
    }
  }

  &.collapse {
    .sidebar-logo {
      margin-right: 0px;
    }
  }
}
</style>
