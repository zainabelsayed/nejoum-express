<template>
  <div>
    <a
      class="text-blueGray-500 py-2 px-3 text-md border bg-gray-100 hover:bg-gray-200 rounded block w-fit whitespace-nowrap"
      href="#pablo"
      ref="btnDropdownRef"
      v-on:click="toggleDropdown($event)"
    >
      <i class="fas fa-cog me-2 text-lg text-gray-600"></i> Settings
      <i
        class="fas fa-chevron-down text-xs ms-2 transform transition-all duration-150 ease-in-out"
        :class="dropdownPopoverShow ? 'rotate-180' : 'rotate-0'"
      ></i>
    </a>
    <div
      ref="popoverDropdownRef"
      class="bg-white text-base z-50 float-left py-2 list-none text-left rounded shadow-lg min-w-48"
      v-bind:class="{
        hidden: !dropdownPopoverShow,
        block: dropdownPopoverShow,
      }"
    >
      <a
        href="javascript:void(0);"
        class="text-sm py-2 px-4 font-normal block w-full whitespace-nowrap bg-transparent text-blueGray-700"
        v-for="listItem in listItems"
        :key="listItem.label"
      >
        <i :class="listItem.icon + ' me-2 text-lg text-gray-600'"></i>
        {{ listItem.label }}
      </a>
    </div>
  </div>
</template>
<script lang="ts">
import { createPopper } from '@popperjs/core'

const listItems = [
  { label: 'Exporting Carriers', icon: 'fas fa-ship' },
  { label: 'Ports', icon: 'fas fa-anchor' },
  { label: 'Consignees', icon: 'fas fa-store' },
  { label: 'User Settings', icon: 'fas fa-user-cog' },
  { label: 'User Roles', icon: 'fas fa-user-lock' },
]

export default {
  data() {
    return {
      dropdownPopoverShow: false,
      listItems,
    }
  },
  methods: {
    toggleDropdown: function (event: Event) {
      event.preventDefault()
      if (this.dropdownPopoverShow) {
        this.dropdownPopoverShow = false
      } else {
        this.dropdownPopoverShow = true
        createPopper(
          this.$refs.btnDropdownRef as HTMLElement,
          this.$refs.popoverDropdownRef as HTMLElement,
          {
            placement: 'bottom-start',
          },
        )
      }
    },
  },
}
</script>
