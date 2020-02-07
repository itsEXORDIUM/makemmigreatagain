<template>
  <div>
    {{siteData.name}}
    <uiNav/>
    <nuxt/>
  </div>
</template>

<script>
import axios from 'axios'
import uiNav from '~/components/uiNav'

export default {
  components: {
    uiNav
  },
  data() {
    return {
      siteData: []
    }
  },
  mounted() {
    // Get Site Data
    axios.get('http://51.158.125.115/wp-json')
      .then(response => {
          this.siteData = response.data;
      })
  }
}
</script>
