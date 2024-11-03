<template>
  <Tabs :tabs="tabs" :initialTab="0">
    <template #tab-0>
      <div class="w-full h-fit">
        <div class="flex flex-wrap">
          <div class="w-full xl:w-6/12 mb-12 xl:mb-0 px-4">
            <card-bar-chart />
          </div>
        </div>
        <div class="flex flex-wrap mt-4">
          <div class="w-full xl:w-8/12 mb-12 xl:mb-0 px-4">
            <card-page-visits />
          </div>
          <div class="w-full xl:w-4/12 px-4">
            <card-social-traffic />
          </div>
        </div>
      </div>
    </template>
  </Tabs>
</template>
<script lang="ts" setup>
import CardBarChart from '@/components/Cards/CardBarChart.vue'
import CardPageVisits from '@/components/Cards/CardPageVisits.vue'
import CardSocialTraffic from '@/components/Cards/CardSocialTraffic.vue'
import Tabs from '@/components/Tabs/Tabs.vue'

const tabs = [
  {
    label: 'Dashboard',
    icon: 'fa-chart-column',
  },
  {
    label: 'Statistics Reports',
    icon: 'fa-tachometer-alt',
  },
]
</script>
