<template>
  <div id="accueil">
    <Accueil :headPage="headPage"/>
    <BlocHome :name="namepolyvalents" :titre="titrepolyvalents" :texte="textepolyvalents" :lien="lienpolyvalents" :images="imagespolyvalents"/>
    <BlocHomeV2 :name="namealtini" :titre="titrealtini" :soustitre="soustitrealtini" :texte="textealtini" :lien="lienaltini" :images="imagesaltini"/>
    <BlocHome :name="namedepartement" :titre="titredepartement" :texte="textedepartement" :lien="liendepartement" :images="imagesdepartement"/>
    <BlocHome :name="namecontact" :titre="titrecontact" :texte="textecontact" :lien="liencontact" :image="imagecontact"/>
    <EcoutezEtudiants :titre="titrenosetudiants"/>
    <BlocHome :name="namerejoindre" :titre="titrerejoindre" :image="imagerejoindre"/>
  </div>
</template>

<script>
import axios from 'axios'
import Accueil from '~/components/head_pages/accueil'
import BlocHome from '~/components/blocs/blocHome'
import BlocHomeV2 from '~/components/blocs/blocHomeV2'
import EcoutezEtudiants from '~/components/blocs/ecoutezEtudiants'

export default {
  components: {
    Accueil, BlocHome, BlocHomeV2, EcoutezEtudiants
  },
  data() {
    return {
      homeData: [],
      headPage: '',
      namepolyvalents : 'polyvalents',
      titrepolyvalents : '',
      textepolyvalents : '',
      lienpolyvalents : '',
      imagespolyvalents: [],
      namealtini : 'altini',
      titrealtini: '',
      textealtini: '',
      soustitrealtini: '',
      lienaltini: '',
      imagesaltini: [],
      namedepartement: 'departement',
      titredepartement: '',
      textedepartement: '',
      liendepartement: '',
      imagesdepartement: [],
      titrepays: '',
      textepays: '',
      lienvoirdupays: '',
      imagepays: [],
      namecontact : 'contact',
      titrecontact: '',
      textecontact: '',
      liencontact: '',
      imagecontact: [],
      namerejoindre: 'rejoindre',
      titrenosetudiants: '',
      titrerejoindre: '',
      imagerejoindre: ''
    }
  },
  mounted() {
      // Get Accueil Data
    axios.get('http://51.158.125.115/wp-json/wp/v2/pages/8?_embed')
      .then(response => {
          this.homeData = response.data;
          this.headPage = response.data.content.rendered;

          // Etudiants polyvalents
          this.titrepolyvalents = response.data.acf.titre_polyvalents;
          this.textepolyvalents = response.data.acf.texte_polyvalents;
          this.lienpolyvalents = response.data.acf.lien_etudiants_polyvalents;
          this.imagespolyvalents = response.data.acf.images_polyvalents;

          // Alternance ou initial
          this.titrealtini = response.data.acf.titre_alt_init;
          this.textealtini = response.data.acf.texte_alt_ini;
          this.soustitrealtini = response.data.acf.sous_titre_alt_init;
          this.lienaltini = response.data.acf.lien_alt_init;
          this.imagesaltini = response.data.acf.images_alt_init;

          // Notre département
          this.titredepartement = response.data.acf.titre_departement;
          this.textedepartement = response.data.acf.texte_departement;
          this.liendepartement = response.data.acf.lien_departement;
          this.imagesdepartement = response.data.acf.images_departement;

          // Voir du pays
          this.titrepays = response.data.acf.titre_pays;
          this.textepays = response.data.acf.texte_pays;
          this.lienvoirdupays = response.data.acf.lien_voir_du_pays;
          this.imagepays = response.data.acf.image_pays;

          // On s'apelle - Contact
          this.titrecontact = response.data.acf.titre_contact;
          this.textecontact = response.data.acf.texte_contact;
          this.liencontact = response.data.acf.lien_contact;
          this.imagecontact = response.data.acf.image_contact;

          // Nos étudiants
          this.titrenosetudiants = response.data.acf.titre_nos_etudiants;

          // Nous rejoindre
          this.titrerejoindre = response.data.acf.titre_rejoindre;
          this.imagerejoindre = response.data.acf.image_rejoindre;
      })
  }
}
</script>
