<template>
  <div class="home py-5">
    <Breadcrumb :list-data="home" />
    <div
      class="container flex flex-wrap justify-between items-center mx-auto py-5 bg-green-300 mt-20"
    >
      <div class="grid grid-rows-2 grid-flow-col gap-4">
        <div class="row-span-3 pl-10">
          <figcaption class="flex justify-center items-center mt-6 space-x-3">
            <img
              class="w-500 h-500 rounded-full"
              src="../assets/img/pokemon.png"
            />
          </figcaption>
        </div>
        <br />
        <div class="col-span-2 pr- text-left">
          <blockquote>
            <p
              class="text-2xl italic font-medium text-gray-900 dark:text-white"
            >
              "Hello everyone, welcome to the pokemon web, here you can see the
              types of pokemon you like."
            </p>
          </blockquote>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="js">
import Breadcrumb from '@/layouts/breadcrumb.vue'
export default {
  data(){
    return{
      home: 'home'
    }
  },
  components:{
    Breadcrumb
  }
}
</script>
