<template>
  <div class="text-center py-5">
    <Breadcrumb class="mb-10" :list-data="detail" />
    <!-- Loading -->
    <div
      class=" flex justify-center items-center spinner-border"
      v-if="loading"
    >
      <div
        class="animate-spin rounded-full h-32 w-32 border-b-8 border-green-900"
      ></div>
    </div>
    <!-- Close Loading -->
    <div class="grid gap-12 grid-cols-1 grid-rows-1">
      <div class="flex justify-center">
        <img src="../assets/img/logopokemon.png" width="150px" />
      </div>
      <div class="flex justify-center">
        <br />
        <div class="text-left">
          <button
            type="button"
            class="w-full text-white bg-gray-700 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600dark:focus:ring-blue-800"
          >
            Detail Pokemon
          </button>
          <div
            class="flex flex-col items-center bg-white rounded-lg border shadow-md md:flex-row md:max-w-xl hover:bg-gray-100 dark:border-gray-700 dark:bg-gray-800 dark:hover:bg-gray-700"
          >
            <img
              class="object-cover w-full h-96 rounded-t-lg md:h-auto md:w-48 md:rounded-none md:rounded-l-lg"
              :src="data.sprites.front_default"
              alt=""
            />
            <div class="flex flex-col justify-between p-4 leading-normal">
              <h5
                class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white"
              >
                {{ data.name }}
              </h5>
              <p class="mb-3 font-normal text-gray-700 dark:text-gray-400"></p>
              <ul class="list-none">
                <li><strong>Height</strong> : {{ data.height }}</li>
                <li><strong>Wight</strong> : {{ data.weight }}</li>
              </ul>
            </div>
          </div>
          <br />
          <div class="text-center btn-block">
            <router-link
              type="submit"
              to="/about"
              class="w-full text-white bg-green-700 hover:bg-green-800 focus:ring-4 focus:outline-none focus:ring-green-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-green-600 dark:hover:bg-green-700 dark:focus:ring-green-800"
              >Back to list pokemon</router-link
            >
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="js">
import axios from 'axios'
import Breadcrumb from '@/layouts/breadcrumb.vue'

export default {
    components: {
      Breadcrumb,
    },

    data(){
        return{
            data: [],
            detail: 'detail',
            loading: false
        }
    },

    mounted(){
        this.location()
    },

    methods: {
         async location(){
            const q =  window.location.href;
            const url = q.split('/')
            const id = url['5']
            this.loading = true
            const {data} = await axios.get(`${process.env.VUE_APP_SERVICE}${id}`);
            setTimeout(() =>{
              this.loading = false
            },1500)
            this.data = data
        }
    }
}
</script>

<style scoped>
.spinner-border {
  display: flex;
  background: rgb(0, 0, 0, 0.6);
  position: fixed;
  inset: 0px;
  transition: 50deg;
  text-align: center;
  align-items: center;
  z-index: 100;
  justify-content: center;
}
</style>
