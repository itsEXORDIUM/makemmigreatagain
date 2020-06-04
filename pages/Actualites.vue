<template>
  <main id="actu" role="main"></main>
</template>

<script>
import axios from 'axios'

export default {
  components: {
  },
  data() {
    return {
      pageTitle: ''
    }
  },
  head () {
    return {
      title: this.pageTitle,
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        { hid: 'description', name: 'description', content: 'My custom description' }
      ]
    }
  },
  mounted() {
    // Get Mobilite Data
    axios.get('http://51.158.125.115/wp-json/wp/v2/pages/19?_embed')
      .then(response => {
        this.pageTitle = response.data.title.rendered;
      })
  }
}
</script>
