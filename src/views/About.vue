<template>
  <div>
    <div class="grid grid-cols-4 gap-4">
      <div v-for="item in data" :key="item.id">
        <div class="flex justify-center">
          <div class="block p-6 rounded-lg shadow-lg bg-white max-w-sm">
            <h5 class="text-gray-900 text-xl leading-tight font-medium mb-2">
              Title
            </h5>
            <p class="text-gray-700 text-base mb-4">
              {{ item.name }}
            </p>
            <a
              type="button"
              :href="item.url"
              target="_blank"
              class=" inline-block px-6 py-2.5 bg-blue-600 text-white font-medium text-xs leading-tight uppercase rounded shadow-md hover:bg-blue-700 hover:shadow-lg focus:bg-blue-700 focus:shadow-lg focus:outline-none focus:ring-0 active:bg-blue-800 active:shadow-lg transition duration-150 ease-in-out"
            >
              Button
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      data: '',
    }
  },

  mounted () {
    this.pokemonGet()
    console.log(process.env.VUE_APP_SERVICE, 'dwdw')
  },

  methods: {
    async pokemonGet () {
      const { data } = await axios.get(process.env.VUE_APP_SERVICE)
      this.data = data.results
      console.log(this.data, 'testing')
    }
  }
}
</script>
