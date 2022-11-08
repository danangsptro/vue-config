<template>
  <div class="text-center py-5 ">
    <Breadcrumb class="mb-10" :list-data="about" />
    <!-- <Search :search-data="search" /> -->

    <div
      class="container flex flex-wrap justify-between items-center mx-auto m-3 p-2"
    >
      <input
        type="text"
        @keyup="pokemonGet"
        v-model="search"
        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full pl-10 p-2.5  dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
        placeholder="Search pokemon name"
      />
    </div>

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

    <div
      class="grid lg:grid-cols-5 lg:gap-5 md:grid-cols-3 md:gap-3 sm:grid-cols-2 sm:gap-2 xs:grid-cols-2 xs:gap-2 container mx-auto px-4 mt-10"
    >
      <div v-for="item in data" :key="item.id">
        <div class="flex justify-center">
          <div
            class="w-full max-w-sm  bg-white rounded-lg border border-gray-200 shadow-md dark:bg-gray-800 dark:border-gray-700"
          >
            <div class="flex flex-col items-center pb-10 mt-5">
              <img
                class="mb-3 w-24 h-24 rounded-full shadow-lg"
                src="../assets/img/poke-logo.png"
                alt="Bonnie image"
              />
              <h5
                class="mb-1 text-xl font-medium text-gray-900 dark:text-white"
              >
                {{ item.name }}
              </h5>
              <span class="text-sm text-bold text-gray-500 dark:text-gray-400">
                Pokemon
              </span>
              <br />
              <Star />
              <div class="flex mt-4 space-x-3 md:mt-6">
                <a
                  type="button"
                  :href="`/#/detail/${item.url}`"
                  class=" inline-block px-6 py-2.5 bg-yellow-500 text-white font-medium text-xs leading-tight uppercase rounded shadow-md hover:bg-yellow-700 hover:shadow-lg focus:bg-yellow-700 focus:shadow-lg focus:outline-none focus:ring-0 active:bg-yellow-800 active:shadow-lg transition duration-150 ease-in-out"
                >
                  Detail
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- <Pagination class="py-10" :pagination="pagination" /> -->
    <br />
    <br />

    <div class="flex flex-col items-center">
      <span class="text-sm text-gray-700 dark:text-gray-400">
        Showing
        <span class="font-semibold text-gray-900 dark:text-white">{{
          first
        }}</span>
        to
        <span class="font-semibold text-gray-900 dark:text-white">{{
          end
        }}</span>
        of
        <span class="font-semibold text-gray-900 dark:text-white">{{
          count
        }}</span>
        Entries
      </span>
      <div class="inline-flex mt-2 xs:mt-0">
        <button
          class="py-2 px-4 text-sm font-medium text-white bg-gray-800 rounded-l hover:bg-gray-900 dark:bg-gray-800 dark:border-gray-700 dark:text-gray-400 dark:hover:bg-gray-700 dark:hover:text-white"
        >
          Prev
        </button>
        <button
          @click="next()"
          class="py-2 px-4 text-sm font-medium text-white bg-gray-800 rounded-r border-0 border-l border-gray-700 hover:bg-gray-900 dark:bg-gray-800 dark:border-gray-700 dark:text-gray-400 dark:hover:bg-gray-700 dark:hover:text-white"
        >
          Next
        </button>
      </div>
    </div>
  </div>
</template>

<script lang="js">
import axios from 'axios'
import Star from '@/components/star/index.vue'
import Breadcrumb from '@/layouts/breadcrumb.vue'
export default {
    components: {
      Star,
      Breadcrumb
    },

  data () {
    return {
      data: [],
      pagination:'',
      offset: '',
      limit: 10,
      about:'about',
      search: '',
      count: 0,
      previe: null,
      loading: false,
      first: '',
      end: ''
    }
  },

  created () {
    this.pokemonGet()
},

  methods: {
    async pokemonGet () {
      this.loading = true
      const { data } = await axios.get(`${process.env.VUE_APP_SERVICE}?${'offset'}=${this.offset}&${`limit`}=${this.limit}`)
      setTimeout(() =>{
        this.loading = false
      },2000)
      this.previe = data.preview
      this.count = data.count
      data.results.map(element => {
        const q = element.url;
        const split = q.split('/')
        element.url = split[6]
      })
      this.first = data.results[0].url
      this.end = data.results[9].url
      this.data = data.results
      this.pagination = data.next
      if (this.search) {
        this.data = data.results.filter(people =>
          people.name.toLowerCase().includes(this.search.toLowerCase())
        );
        console.log(this.data, 'data test')
      } else {
        this.people = data.results;
      }
    },

    next(){
      this.loading = true
      this.offset = this.data[9].url * 1
      this.pokemonGet()
      this.loading = false

    },

    // preview(){
    //   if(this.previe === null){

    //   }
    // }

  },

  // computed: {
  //     resultQuery(){
  //       if(this.search){
  //       return this.data.filter((item)=>{
  //         const q = this.search.toLowerCase().split(' ').every(v => item.name.toLowerCase().includes(v))
  //         this.search = q
  //         console.log(this.search,'wdw')
  //       })
  //       }else{
  //         return this.data;
  //       }
  //     }
  //   }
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
