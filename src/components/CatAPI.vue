<template>
  <div>
      <img class="auto-resize" :src="this.Img.url" >
  </div>
</template>

<script>
import axios from 'axios'
export default {
    methods: {
        'fetchImg': function(){
            //URL for the api to call
            var apiUrl = "https://api.thecatapi.com/v1/images/search"

            //Return a promise returning first element in response of api call
            return axios.get(apiUrl).then(function(response){
                return response.data[0]
            })
        },
        'changeImg': function(){
            this.fetchImg().then((response) => {
            this.Img = response
        })
        }
    },
    data: function(){
        return{
            Img: null
        }
    },
    created(){
        this.$parent.$on("apiChange", this.changeImg)
    },
    mounted(){
        this.changeImg()
    }
        
}
</script>

<style>
.auto-resize{
    width: auto;
    height: 100%;
    max-height: 40vh;
}
</style>