<template>
  <!-- Navbar -->
  <nav
    class="w-full z-10 bg-transparent md:flex-row md:flex-nowrap md:justify-start flex items-center p-4"
  >
    <!-- Toggler -->
    <button
      class="cursor-pointer text-black opacity-50 px-3 py-1 text-xl leading-none bg-transparent rounded border border-solid border-transparent"
      type="button"
      v-on:click="toggleCollapseShow()"
    >
      <i class="fas fa-bars"></i>
    </button>
    <div
      class="w-full mx-auto items-center flex justify-between md:flex-nowrap flex-wrap md:px-2 px-4"
    >
      <!-- Form -->
      <form class="flex flex-row flex-wrap items-center w-3/12 border">
        <div class="relative flex w-full flex-wrap items-stretch">
          <span
            class="z-10 h-full leading-snug font-normal text-center text-blueGray-300 absolute bg-transparent rounded text-base items-center justify-center w-8 pl-3 py-3"
          >
            <i class="fas fa-search"></i>
          </span>
          <input
            type="text"
            placeholder="Search here..."
            class="border-0 px-3 py-3 placeholder-blueGray-300 text-blueGray-600 relative bg-white rounded text-sm shadow outline-none focus:outline-none focus:ring w-full pl-10"
          />
        </div>
      </form>

      <!-- User -->
      <ul
        class="flex-col md:flex-row list-none items-center gap-4 hidden md:flex"
      >
        <div class="px-3 text-md rounded py-2 bg-borders-500 text-white">
          New Jersey
        </div>
        <!-- settings -->
        <settingsDropDown />
        <div class="text-md">John Doe (Read only)</div>
        <user-dropdown />
      </ul>
    </div>
  </nav>
  <!-- End Navbar -->
</template>

<script lang="ts" setup>
import UserDropdown from '@/components/Dropdowns/UserDropdown.vue'
import SettingsDropDown from '@/components/Dropdowns/SettingsDropDown.vue'
import { inject } from 'vue'
import type { SidebarState } from '../Sidebar/types'

const sidebarState = inject('sidebarState') as SidebarState

const toggleCollapseShow = () => {
  sidebarState.collapseShow = !sidebarState.collapseShow
}
</script>
