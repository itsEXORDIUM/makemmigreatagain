<template>
  <main id="departement">
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
      titrebienvenue: '',
      imagebienvenue: '',
      textebienvenue: ''
    }
  },
  mounted() {
    // Get Departement Data
    axios.get('http://51.158.125.115/wp-json/wp/v2/pages/14?_embed')
      .then(response => {
        // Headpage
        this.titrebienvenue = response.data.acf.titre_bienvenue;
        this.imagebienvenue = response.data.acf.image_bienvenue.url;
        this.textebienvenue = response.data.acf.texte_bienvenue;
      })
  }
}
</script>
