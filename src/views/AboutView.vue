<template>
  <div class="about">
    <h1>This is an about page</h1>
    <h3>{{$route.params.id}}</h3>
    <li v-for =" cat in catlist" :key="cat.url"><img :src="cat.url" /></li>
  </div>
</template>
<script>
import axios from 'axios'
export default {

  data() {

    return {
      catlist: [

      ]
    }
  },
  async created() {
                  
    const catId = this.$route.params.id;//!!!!
    try {

      const res = await axios.get('https://api.thecatapi.com/v1/images/search?breed_ids='+catId+'')
      //console.log(res),
        this.catlist = res.data;
    } catch (e) {
      console.log('error');
    }
  },

  // methods(){
  //   console.log($route.params.id);
  // },
}
</script>