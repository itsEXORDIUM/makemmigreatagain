<template>
  <main id="contact">
  </main>
</template>

<script>
import axios from 'axios'
import HeadPage from '~/components/head_pages/headpage'

export default {
  components: {
    HeadPage
  },
  data() {
    return {
    }
  },
  mounted() {
    // Get Contact Data
    axios.get('http://51.158.125.115/wp-json/wp/v2/pages/21?_embed')
      .then(response => {
      })
  }
}
</script>
