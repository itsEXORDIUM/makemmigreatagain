<template>
  <div :class="`bloc_equipe wrap ${name}`">
    <div class="bloc_title">
      <h2 class="bloc_titre"><span class="show-for-sr">{{titre}}</span>
          <Equipe/>
      </h2>
    </div>
    <div class="membrepedago" v-for="(mb, index) in membres" :key="index">
      <img :src="mb.acf.image" alt=""/>
      <div class="content">
        <p class="name">{{mb.title.rendered}}</p>
        <p class="commentaire">{{mb.acf.commentaire}}</p>
        <div class="stats">
          <div>
            <p>Charisme : {{mb.acf.charisme}}</p>
            <p>Sagesse : {{mb.acf.sagesse}}</p>
          </div>
          <div>
            <p>Intellect : {{mb.acf.intellect}}</p>
            <p>Force : {{mb.acf.force}}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Equipe from '~/components/titres/equipe'

export default {
  props: {
      name:'',
      titre: '',
      infosun: Array,
      infosdeux: Array,
      infostrois: Array,
      texte: ''
  },
  components: {
    Equipe
  },
  data() {
    return {
      membres: []
    }
  },
  mounted() {
    // Get Equipe Data
    axios.get('http://51.158.125.115/wp-json/wp/v2/equipe?_embed')
      .then(response => {
        this.membres = response.data;
      })
  }
}
</script>