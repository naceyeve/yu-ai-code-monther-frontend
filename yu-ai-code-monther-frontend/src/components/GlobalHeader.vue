<template>
  <div class="global-header">
    <div class="header-left">
      <img class="logo" src="/favicon.ico" alt="logo" />
      <span class="site-title">编程导航</span>
    </div>
    <a-menu mode="horizontal" :selectedKeys="[selectedKey]" class="header-menu">
      <a-menu-item v-for="item in menuItems" :key="item.key">
        <router-link :to="item.path">{{ item.label }}</router-link>
      </a-menu-item>
    </a-menu>
    <div class="header-right">
      <a-button type="primary" @click="goLogin">登录</a-button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, watchEffect } from 'vue'
import { useRoute, useRouter } from 'vue-router'

const props = defineProps<{ menuItems: Array<{ key: string; label: string; path: string }> }>()
const route = useRoute()
const router = useRouter()
const selectedKey = ref('')

watchEffect(() => {
  const match = props.menuItems.find((item) => item.path === route.path)
  selectedKey.value = match ? match.key : ''
})

function goLogin() {
  router.push('/user/login')
}
</script>

<style scoped>
.global-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 64px;
  padding: 0 24px;
  background: #fff;
  border-bottom: 1px solid #f0f0f0;
}
.header-left {
  display: flex;
  align-items: center;
}
.logo {
  width: 32px;
  height: 32px;
  margin-right: 12px;
}
.site-title {
  font-size: 20px;
  font-weight: bold;
  color: #1677ff;
}
.header-menu {
  flex: 1;
  margin: 0 32px;
  min-width: 200px;
}
.header-right {
  display: flex;
  align-items: center;
}
</style>
