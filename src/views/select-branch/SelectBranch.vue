<script lang="ts" setup>
const branches = [
  'New Jersey',
  'California',
  'Texas',
  'Savannah',
  'Washington',
  'Incheon, South Korea',
]
</script>
<template>
  <div
    class="flex justify-center items-center w-full h-full py-5 bg-wheat select-branch"
  >
    <div
      class="max-w-[415px] max-h-[723px] md:h-[723px] border bg-white border-borders-500 md:min-w-[415px] md:mx-0 mx-4"
    >
      <div class="w-full text-lg text-white bg-borders-500 py-[10px] px-[14px]">
        Select Warehouse
      </div>
      <div class="p-5 flex flex-col items-center justify-center">
        <img src="@/assets/img/logo.jpg" class="w-full object-cover" />
        <div class="py-3 text-[15px] font-semibold">
          Please Choose one of the following Warehouses
        </div>
        <ul class="w-full">
          <li
            v-for="branch in branches"
            :key="branch"
            class="py-[9px] cursor-pointer w-full"
          >
            <RouterLink to="/admin">
              <button
                class="text-lg w-full bg-secondary-500 hover:bg-secondary-600 text-white px-5 py-3 flex justify-center items-center"
              >
                <div class="mb-1">
                  {{ branch }}
                </div>
                <i class="ml-2 fas fa-angle-right text-[21px]"></i>
              </button>
            </RouterLink>
          </li>
        </ul>
        <div class="border-t border-black mt-2 mb-4 w-full"></div>
        <RouterLink class="w-full" to="/">
          <button
            class="text-lg w-full bg-red-500 hover:bg-red-600 text-white px-5 py-2 flex justify-center items-center"
          >
            <div class="mb-1">Logout</div>
            <i class="ml-2 fas fa-sign-out-alt text-3xl"></i>
          </button>
        </RouterLink>
      </div>
    </div>
  </div>
</template>
