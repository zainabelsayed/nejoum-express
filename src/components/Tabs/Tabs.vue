<!-- Tabs.vue -->
<template>
  <div class="border-borders-500 border-2">
    <!-- Tabs Header -->
    <div class="flex bg-borders-500 px-3 pt-3">
      <button
        v-for="(tab, index) in tabs"
        :key="index"
        @click="setActiveTab(index)"
        :class="[
          'px-4 py-2  focus:outline-none text-base',
          activeTab === index
            ? 'text-secondary-500 bg-white'
            : 'bg-borders-500 text-white border-transparent',
        ]"
      >
        <i v-if="tab.icon" :class="'fas ' + tab.icon"></i>
        {{ tab.label }}
      </button>
    </div>

    <!-- Tabs Content -->
    <div class="p-4 bg-white">
      <slot :name="`tab-${activeTab}`"></slot>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, defineProps } from 'vue'

// Define prop types
interface Tab {
  label: string
  icon?: string
}

const props = defineProps<{
  initialTab?: number
  tabs: Tab[]
}>()

// Default to the initialTab prop or 0
const activeTab = ref(props.initialTab ?? 0)

// Function to set active tab
const setActiveTab = (index: number) => {
  activeTab.value = index
}
</script>
