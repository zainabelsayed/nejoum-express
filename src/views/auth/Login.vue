<template>
  <div
    class="container mx-auto px-4 lg:px-12 flex flex-col justify-center w-full items-center md:items-end md:px-0"
  >
    <div
      class="flex content-center w-full items-center justify-end h-full lg:w-6/12 md:w-6/12 md:px-4"
    >
      <div
        class="w-full flex justify-items-center mx-auto sm:max-w-128 align-items-center lg:px-4"
      >
        <div
          class="relative w-full justify-center items-center flex flex-col break-words max-w-128 mb-6 shadow-outline bg-white border-0"
        >
          <div
            class="flex flex-col justify-center items-center mx-auto gap-4 p-8 lg:p-12 py-10 w-full"
          >
            <div class="flex flex-col justify-center items-center gap-3">
              <div class="w-8 h-8">
                <img
                  src="@/assets/img/icon-car.gif"
                  class="w-full"
                  alt="car-icon"
                />
              </div>
              <h2 class="text-3xl text-gray-800 font-normal mb-3 font-jost">
                Sign Into Your Account
              </h2>
            </div>

            <form class="w-full flex flex-col gap-6">
              <div class="relative w-full">
                <input
                  type="email"
                  class="border-0 px-4 py-5 text-gray-600 shadow-outline bg-white rounded text-sm focus:outline-none focus:ring w-full ease-linear transition-all duration-150 placeholder:text-lg placeholder:text-gray-500"
                  placeholder="Email Address"
                />
                <i
                  class="far fa-envelope text-lg absolute right-3 top-1/2 transform -translate-y-1/2 text-gray-500 hover:rotate-[360deg] transition-all duration-150"
                ></i>
              </div>

              <div class="relative w-full">
                <input
                  type="password"
                  class="border-0 px-4 py-5 text-gray-600 bg-white rounded text-sm shadow-outline focus:outline-none focus:ring w-full ease-linear transition-all duration-150 placeholder:text-lg placeholder:text-gray-500"
                  placeholder="Password"
                />
                <i
                  class="fa fa-lock text-lg absolute right-3 top-1/2 transform -translate-y-1/2 text-gray-500 hover:rotate-[360deg] transition-all duration-150"
                ></i>
              </div>

              <div class="text-center">
                <RouterLink to="/select-branch">
                  <button
                    class="bg-primary-500 hover:bg-primary-600 text-white active:bg-blueGray-600 text-lg font-bold px-6 py-5 rounded shadow hover:shadow-lg outline-none focus:outline-none mr-1 mb-1 w-full ease-linear transition-all duration-150"
                    type="button"
                  >
                    Login
                  </button>
                </RouterLink>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import github from '@/assets/img/github.svg'
import google from '@/assets/img/google.svg'

export default {
  data() {
    return {
      github,
      google,
    }
  },
}
</script>
