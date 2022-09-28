<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="hello">
      <li v-for =" cat in catlist" :key="cat.id">
      <router-link :to="{ name: 'About',  params: { id: cat.id },component: About }">
            {{ cat.id }}
          </router-link> </li>
      <!-- <li v-for =" cat in catlist" :key="cat.id">{{ cat.id }}<img :src="cat.url" />R</li> -->
      <!-- <table>
        <tr>
          <td>Question</td>
          <td>choices</td>
        </tr>
        <tr v-for="qtn in qtnlist" v-bind:key="qtn.choice">
          <router-link :to="{ name: 'About',  params: { id: qtn.question },component: About }">
            <td>{{qtn.question}}</td>
          </router-link> -->
          <!-- <router-link :to="{name: 'About', params: { qtn: qtn.question } }"> -->

          <!-- </router-link> -->
          <!-- <td>{{qtn.published_at}}</td>
        </tr>
      </table> -->
    </div>
  </div>
</template>

<script>

import axios from 'axios'
export default {
  name: 'HelloWorld',
  props: {
    About: Object

  },
  data() {
    return {
      catlist: [

      ]
    };
  },
  async created() {
    try {
      const res = await axios.get('https://api.thecatapi.com/v1/breeds')
      console.log(res),
      this.catlist = res.data;
    } catch (e) {
      console.log('error');
    }
  },
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
