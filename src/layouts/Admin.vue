<template>
  <div>
    <sidebar />
    <div
      class="relative bg-blueGray-100 transform transition-transform duration-300 ease-in-out"
      :class="{ 'md:ml-[222px]': sidebarState.collapseShow }"
    >
      <admin-navbar />
      <div class="px-4 md:px-10 mx-auto w-full h-full py-5 bg-wheat">
        <router-view />
      </div>
    </div>
  </div>
</template>
<script lang="ts" setup>
import AdminNavbar from '@/components/Navbars/AdminNavbar.vue'
import Sidebar from '@/components/Sidebar/Sidebar.vue'
import { provide, reactive } from 'vue'
import type { SidebarState } from '@/components/Sidebar/types'

const sidebarState = reactive({
  collapseShow: true,
}) as SidebarState

provide('sidebarState', sidebarState)
</script>
