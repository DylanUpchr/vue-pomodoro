<template>
  <div>
      <img :src="this.Img.url">
  </div>
</template>

<script>
import axios from 'axios'
export default {
    methods: {
        'fetchImg': function(){
            var apiUrl = "https://api.thecatapi.com/v1/images/search"
            //var result
            return axios.get(apiUrl).then(function(response){
                //this.Img = response.data[0]
                //alert(JSON.stringify(response.data[0]))
                return response.data[0]
            })
        }
    },
    data: function(){
        return{
            Img: null
        }
    },
    mounted(){
        this.fetchImg().then((response) => {
            this.Img = response
        })
    }
}


</script>

<style>

</style>