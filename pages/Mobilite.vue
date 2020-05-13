<template>
   <main id="mobilite">
     <HeadPage :titre="titremobilite" :image="imagemobilite" :texte="textemobilite"/>
     <BlocHome :name="namestage" :titre="titrestage" :texte="textestage" :image="imagestage"/>
   </main>
</template>

<script>
import axios from 'axios'
import HeadPage from '~/components/head_pages/headpage'
import BlocHome from '~/components/blocs/blocHome'

export default {
  components: {
    HeadPage, BlocHome
  },
  data() {
    return {
      titremobilite: '',
      imagemobilite: '',
      textemobilite: '',
      namestage: 'stageetranger',
      titrestage: '',
      textestage: '',
      imagestage: ''
    }
  },
  mounted() {
    // Get Mobilite Data
    axios.get('http://51.158.125.115/wp-json/wp/v2/pages/17?_embed')
      .then(response => {
          // Headpage
          this.titremobilite = response.data.acf.titre_mobilite;
          this.imagemobilite = response.data.acf.image_mobilite.url;
          this.textemobilite = response.data.acf.texte_mobilite;

          // Stage Etranger
          this.titrestage = response.data.acf.titre_stage_etranger;
          this.textestage = response.data.acf.texte_stage_etranger;
          this.imagestage = response.data.acf.image_stage_etranger.url;
      })
  }
}
</script>
