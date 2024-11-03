<template>
  <div
    class="md:hidden flex justify-between items-start w-full h-full bg-borders-500 text-white"
  >
    <!-- Brand -->
    <router-link
      class="text-left md:pb-2 text-blueGray-600 mr-0 whitespace-nowrap capitalize text-xl p-2"
      to="/admin"
    >
      <div class="flex items-center gap-2">
        <div class="w-10 h-10">
          <img src="@/assets/img/icon-car.gif" class="w-full" alt="car-icon" />
        </div>
        <div>Nejoum Express</div>
      </div>
    </router-link>
    <!-- User -->
    <ul class="md:hidden items-center flex flex-wrap list-none">
      <li class="inline-block relative">
        <notification-dropdown />
      </li>
      <li class="inline-block relative">
        <user-dropdown />
      </li>
    </ul>
  </div>
  <nav
    class="transform transition-transform duration-300 ease-in-out w-full md:w-[222px] md:left-0 md:block md:fixed md:top-0 md:bottom-0 md:overflow-y-auto md:flex-row md:flex-nowrap md:overflow-hidden shadow-xl bg-dark flex flex-wrap items-center justify-between relative z-10"
    :class="{
      'translate-x-0 ': sidebarState.collapseShow,
      'md:-translate-x-[222px] -translate-x-full': !sidebarState.collapseShow,
    }"
  >
    <div
      class="md:flex-col md:items-stretch h-full md:flex-nowrap px-0 flex flex-wrap items-center justify-between w-full mx-auto"
    >
      <!-- Collapse -->
      <div
        class="md:flex md:flex-col bg-dark flex flex-col justify-start md:items-stretch md:opacity-100 md:relative md:shadow-none shadow absolute top-0 left-0 right-0 z-40 overflow-y-auto overflow-x-hidden h-screen items-start w-full flex-1"
      >
        <button
          class="cursor-pointer absolute top-3 right-3 z-20 text-white opacity-50 md:hidden px-3 py-1 text-xl leading-none bg-transparent rounded border border-solid border-transparent"
          type="button"
          v-on:click="toggleCollapseShow()"
        >
          <i class="fas fa-times"></i>
        </button>
        <!-- Collapse header -->
        <div
          class="md:min-w-full w-full hidden md:block pb-3 border-solid border-blueGray-200 pt-4 bg-borders-500 text-white"
        >
          <div class="flex flex-wrap justify-between items-center px-2">
            <div class="w-6/12 md:w-full">
              <router-link
                class="text-left mr-0 whitespace-nowrap capitalize text-xl p-4 px-0"
                to="/admin"
              >
                <div class="flex items-center gap-2">
                  <div class="w-10 h-10">
                    <img
                      src="@/assets/img/icon-car.gif"
                      class="w-full"
                      alt="car-icon"
                    />
                  </div>
                  <div>Nejoum Express</div>
                </div>
              </router-link>
            </div>
          </div>
        </div>
        <!-- Form -->
        <form class="mt-12 md:hidden w-full px-2">
          <input
            type="text"
            placeholder="Search"
            class="px-3 py-2 h-12 border border-solid border-blueGray-500 placeholder-blueGray-300 text-blueGray-600 bg-white rounded text-base leading-snug shadow-none outline-none focus:outline-none w-full font-normal"
          />
        </form>

        <!-- Navigation -->

        <ul class="md:flex-col w-full flex flex-col list-none py-2">
          <li class="items-center w-full">
            <router-link
              v-slot="{ href, navigate, isActive }"
              v-for="link in navLinks"
              :key="link.name"
              :to="link.url"
            >
              <a
                :href="href"
                @click="navigate"
                class="text-base py-[22px] w-full block text-textDark hover:text-white px-5 hover:bg-navActive transform transition-transform duration-300 ease-in-out"
                :class="[
                  isActive
                    ? 'border-l-[5px] border-borders-500 bg-navActive ps-4'
                    : 'border-none',
                ]"
              >
                <div class="flex items-center gap-2 w-full">
                  <i
                    class="fas text-lg hover:text-white w-6"
                    :class="link.icon"
                  ></i>
                  <div class="text-start">
                    {{ link.name }}
                  </div>
                </div>
              </a>
            </router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
) };

<script lang="ts" setup>
import NotificationDropdown from '@/components/Dropdowns/NotificationDropdown.vue'
import UserDropdown from '@/components/Dropdowns/UserDropdown.vue'
import { inject } from 'vue'
import type { SidebarState } from './types'

const sidebarState = inject('sidebarState') as SidebarState

const navLinks = [
  { name: 'Home', url: '/admin', icon: 'fas fa-home' },
  { name: 'Workflow', url: '/admin/workflow', icon: 'fas fa-network-wired' },
  { name: 'Vehicles', url: '/admin/Vehicles', icon: 'fas fa-car' },
  { name: 'Customers', url: '/admin/customers', icon: 'fas fa-users' },
  { name: 'Suppliers', url: '/admin/suppliers', icon: 'fas fa-truck' },
  {
    name: 'Dock Receipts',
    url: '/admin/dock-receipt',
    icon: 'fas fa-file-alt',
  },
  { name: 'Reports', url: '/admin/reports', icon: 'fas fa-file' },
]

const toggleCollapseShow = () => {
  sidebarState.collapseShow = !sidebarState.collapseShow
}
</script>
