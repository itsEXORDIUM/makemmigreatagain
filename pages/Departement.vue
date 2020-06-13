<template>
  <main id="departement" role="main">
    <div class="greybck">
      <HeadPage name="bienvenue" :titre="titrebienvenue" :image="imagebienvenue" :texte="textebienvenue"/>
    </div>
    <BlocHome name="communaute" :titre="titre331" :texte="texte331" :image="image331"/>
    <BlocHomeV2 name="defi" :titre="titre24h" :texte="texte24h" :images="images24h"/>
    <BlocHome name="frigo" :titre="titrefrigo" :texte="textefrigo" :image="imagefrigo"/>
    <BlocEquipe/>
  </main>
</template>

<script>
import axios from 'axios'
import HeadPage from '~/components/head_pages/headpage'
import BlocHome from '~/components/blocs/blocHome'
import BlocHomeV2 from '~/components/blocs/blocHomeV2'
import BlocEquipe from '~/components/blocs/blocEquipe'

export default {
  components: {
    HeadPage, BlocHome, BlocHomeV2, BlocEquipe
  },
  data() {
    return {
      pageTitle: '',
      titrebienvenue: '',
      imagebienvenue: '',
      textebienvenue: '',
      titre331: '',
      texte331: '',
      image331: '',
      titre24h: '',
      texte24h: '',
      images24h: [],
      titrefrigo: '',
      imagefrigo: '',
      textefrigo: ''
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
    // Get Departement Data
    axios.get('https://palayewordpress.planethoster.world/mmi/wp-json/wp/v2/pages/14?_embed')
      .then(response => {
        this.pageTitle = response.data.title.rendered;

        // Headpage
        this.titrebienvenue = response.data.acf.titre_bienvenue;
        this.imagebienvenue = response.data.acf.image_bienvenue;
        this.textebienvenue = response.data.acf.texte_bienvenue;

        // 331
        this.titre331 = response.data.acf.titre_331;
        this.texte331 = response.data.acf.texte_331;
        this.image331 = response.data.acf.image_331;

        // Defi 24h
        this.titre24h = response.data.acf.titre_24h;
        this.texte24h = response.data.acf.texte_24h;
        this.images24h = response.data.acf.images_24h;

        // Frigo
        this.titrefrigo = response.data.acf.titre_frigo;
        this.imagefrigo = response.data.acf.image_frigo;
        this.textefrigo = response.data.acf.texte_frigo;
      })
  }
}
</script>
