<template>
  <div>
    <a
      class="text-blueGray-500 block"
      href="#pablo"
      ref="btnDropdownRef"
      v-on:click="toggleDropdown($event)"
    >
      <div class="items-center flex">
        <span
          class="w-9 h-9 text-sm text-white bg-blueGray-200 inline-flex items-center justify-center rounded-full"
        >
          <img
            alt="..."
            class="w-full rounded-full align-middle border-none shadow-lg"
            :src="image"
          />
        </span>
      </div>
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
        <i :class="'me-2 text-lg text-gray-600 fas ' + listItem.icon"></i>
        {{ listItem.label }}
      </a>
    </div>
  </div>
</template>

<script lang="ts">
import { createPopper } from '@popperjs/core'

import image from '@/assets/img/user-avatar.png'

const listItems = [
  { label: 'Change Password', icon: 'fa-key' },
  { label: 'Arabic', icon: 'fa-language' },
  { label: 'Switch whorehouse', icon: 'fa-refresh' },
  { label: 'Log out', icon: 'fa-sign-out-alt' },
]

export default {
  data() {
    return {
      dropdownPopoverShow: false,
      image: image,
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
