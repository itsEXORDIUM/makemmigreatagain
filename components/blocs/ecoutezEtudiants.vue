<template>
  <div class="bloc_home wrap temoignage">
    <h2 class="bloc_titre">
      <span class="show-for-sr">{{titre}}</span>
        <EcoutezEtudiantsTitre/>
    </h2>

    <div class="slideshow-container">

      <div v-for="(temoin, index) in temoignages" :key="index" class="mySlides fade">
        <div class="identite">
          <h3 class="nom_temoin">{{temoin.title.rendered}}</h3>
          <img :src="temoin._embedded['wp:featuredmedia']['0'].source_url" alt=""/>
        </div>
        <div class="contenu">
          <h4 class="title">Profil</h4>
          <p>{{temoin.acf.profil}}</p>
          <h4 class="title">Âge</h4>
          <p>{{temoin.acf.age}}</p>
          <h4 class="title">Réseaux Sociaux</h4>
          <ul class="reseaux">
            <li v-for="(lien, index) in temoin.acf.reseaux_sociaux" :key="index">
              <a :class="index" v-if="lien" :href="lien" target="_blank" :title="`Suivez-nous sur ${index} (Nouvelle Fenêtre)`">{{index}}</a>
            </li>
          </ul>

          <h4 class="show-for-sr">Témoignage</h4>
          <blockquote v-html="temoin.content.rendered"></blockquote>
        </div>
      </div>

      <button tabindex="0" aria-label="Témoignage Précédent" aria-pressed="false" role="button" class="prev" @click="plusSlides(-1)">&#10094;</button>
      <button tabindex="0" aria-label="Témoignage Suivant" aria-pressed="false" role="button" class="next" @click="plusSlides(1)" title="Voir le témoignage suivant">&#10095;</button>
    </div>

  </div>
</template>

<script>
import axios from 'axios'
import EcoutezEtudiantsTitre from '~/components/titres/ecoutezetudiantstitre'

export default {
  props: {
      titre: ''
  },
  components: {
    EcoutezEtudiantsTitre
  },
  data() {
    return {
      temoignages: [],
      slideIndex: 1
    }
  },
  mounted() {
     // Get Temoignages
    axios.get('http://51.158.125.115/wp-json/wp/v2/temoignage_ancien?_embed')
      .then(response => {
          this.temoignages = response.data;
          this.showSlides();
      })
  },
  methods: {
    plusSlides: function(n) {
      this.slideIndex = this.slideIndex += n;
      this.showSlides(n);
    },

    showSlides: function(n) {
      var slideIndex = this.slideIndex;
      var i;
      var slides = this.$el.getElementsByClassName("mySlides");
      if (this.slideIndex > slides.length) {this.slideIndex = 1}
      if (n < 1) {this.slideIndex = slides.length}
      for (i = 0; i < slides.length; i++) {
          slides[i].style.display = "none";  
      }
      console.log(slides[this.slideIndex-1]);
      slides[this.slideIndex-1].style.display = "flex";  
    }
  }
}
</script>