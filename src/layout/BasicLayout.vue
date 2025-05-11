<template>
  <div id="basicLayout">
    <a-layout style="min-height: 100vh">
      <a-layout-sider class="side" v-model:collapsed="collapsed" collapsible>
        <div class="logo flex items-center justify-center bg-white/30 border-r border-gray-200" style="height: 64px">
          <img src="../assets/logo.svg" alt="logo" class="h-1/2" />
        </div>
        <a-divider style="margin: 0" />

        <a-menu theme="light" mode="inline" :default-selected-keys="[$route.path]">
          <a-menu-item key="/">
            <router-link to="/" class="flex items-center gap-10">
              <WifiOutlined />
              <span class="nav-text">首页</span>
            </router-link>
          </a-menu-item>
          <a-menu-item key="/about">
            <router-link to="/about" class="flex items-center gap-10">
              <VideoCameraOutlined />
              <span class="nav-text">关于</span>
            </router-link>
          </a-menu-item>
        </a-menu>
      </a-layout-sider>
      <a-layout>
        <a-layout-header class="header">Header</a-layout-header>
        <a-layout-content class="content">
          <router-view />
        </a-layout-content>
        <a-layout-footer class="footer">2025@copyright by victor</a-layout-footer>
      </a-layout>
    </a-layout>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
// import HomeView from '@/views/HomeView.vue'
import { WifiOutlined, VideoCameraOutlined } from '@ant-design/icons-vue'
import { RouterLink, useRoute } from 'vue-router'
import { Divider as ADivider } from 'ant-design-vue'

const collapsed = ref<boolean>(true)
const $route = useRoute()
</script>

<style scoped>
#basicLayout .side {
  background-color: white;
  width: 100px;
}

#basicLayout .header {
  padding-inline: 20px;
  background: white;
  color: unset;
  margin-bottom: 16px;
}

#basicLayout .footer {
  background: #efefef;
  position: fixed;
  padding: 16px;
  bottom: 0;
  left: 0;
  right: 0;
  text-align: center;
}

#basicLayout .content {
  padding: 20px 20px 44px;
  background: linear-gradient(to right, #fefefe, #fff);
  margin-bottom: 28px;
  height: calc(100vh - 64px - 48px); /* 确保内容区域有明确的高度 */
}

.logo-divider {
  height: 1px;
  background: #e5e7eb; /* gray-200 */
  width: 100%;
}
</style>
