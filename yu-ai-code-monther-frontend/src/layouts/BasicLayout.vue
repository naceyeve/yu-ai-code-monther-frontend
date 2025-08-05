<template>
  <a-layout style="min-height: 100vh">
    <a-layout-header style="padding: 0; background: #fff">
      <GlobalHeader :menu-items="menuItems" />
    </a-layout-header>
    <a-layout-content style="margin: 24px 16px 0">
      <router-view />
    </a-layout-content>
    <a-layout-footer style="padding: 0; background: #fff">
      <GlobalFooter />
    </a-layout-footer>
  </a-layout>
</template>

<script setup lang="ts">
import GlobalHeader from '../components/GlobalHeader.vue'
import GlobalFooter from '../components/GlobalFooter.vue'

const menuItems = [
  { key: 'home', label: '首页', path: '/' },
  { key: 'about', label: '关于', path: '/about' },
]
</script>
