<template>
  <div class="container">
    <h1>Index</h1>
    {{homeData.acf.texte}}
    <img :src="homeData.acf.image" alt=''/>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  components: {
  },
  data() {
    return {
      homeData: []
    }
  },
  mounted() {
      // Get Accueil Data
    axios.get('http://51.158.125.115/wp-json/wp/v2/pages/8')
      .then(response => {
          this.homeData = response.data;
      })
  }
}
</script>
