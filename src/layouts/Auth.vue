<template>
  <div>
    <main>
      <section
        class="relative w-full h-full flex justify-center items-center min-h-screen"
      >
        <div class="absolute top-0 w-full h-full bg-beige bg-no-repeat bg-full">
          <div
            class="bg-auth-image hidden lg:flex bg-cover bg-center h-screen z-10 w-6/12 relative"
          >
            <div
              class="w-full flex flex-col justify-items-start items-center text-white absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2"
            >
              <h1
                class="text-6xl font-jost leading-tight uppercase font-semibold"
              >
                Welcome to <br />
                <span class="text-primary-500">Nejoum Express</span>
              </h1>
            </div>
          </div>
        </div>
        <router-view />
      </section>
    </main>
  </div>
</template>
<script lang="ts">
import registerBg2 from '@/assets/img/register_bg_2.png'

export default {
  data() {
    return {
      registerBg2,
    }
  },
}
</script>
