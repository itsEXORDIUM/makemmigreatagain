<template>
   <main id="mobilite">
     <HeadPage :titre="titremobilite" :image="imagemobilite" :texte="textemobilite"/>
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
      MobiliteData: [],
      titremobilite: '',
      imagemobilite: '',
      textemobilite: ''
    }
  },
  mounted() {
      // Get Accueil Data
    axios.get('http://51.158.125.115/wp-json/wp/v2/pages/17?_embed')
      .then(response => {
          this.MobiliteData = response.data;

          this.titremobilite = response.data.acf.titre_mobilite;
          this.imagemobilite = response.data.acf.image_mobilite.url;
          this.textemobilite = response.data.acf.texte_mobilite;
      })
  }
}
</script>
