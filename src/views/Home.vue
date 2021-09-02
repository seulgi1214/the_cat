<template>
  <v-main>
    <v-container>
      <v-layout>
        <v-flex>
          <v-select 
            :items="['gif', 'jpg,png', 'jpg,png,gif' ]"
            v-model="image_type"
            label="mime types"
            attach
          >
          </v-select>
        </v-flex>
        <v-btn large @click="getData">
          새로고침
        </v-btn>
      </v-layout>
      <v-layout>
        <v-card>
          <v-img :src="image.url">
          </v-img>
        </v-card>
      </v-layout>
    </v-container>
  </v-main>
</template>

<script>

import axios from 'axios';
export default {
  data() {
    return {
      image: {url: ""},
      image_type: 'gif'
    }
  },
  watch: {           
  image_type: function()
  {
    this.getData();
  }
  },
  created() {
    this.getData()
  },
  methods: {
    async getData() {
      try {
        axios.defaults.baseURL = 'process.env.VUE_APP_api_key'
        
        let response = await axios.get('https://api.thecatapi.com/v1/images/search', {params: {limit:1, size:"full", mime_types: this.image_type}})

        this.image =  response.data[0]

        console.log("-- Image from TheCatAPI.com")
        console.log("id:", this.image.id)
        console.log("url:", this.image.url)

      } catch(err) {
        console.log(err)
      }
    }
  },
}
</script>
