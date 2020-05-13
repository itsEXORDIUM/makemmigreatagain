<template>
  <div :class="`wrap ${name}`">
    <div class="bloc_title">
      <h2 class="bloc_titre"><span class="show-for-sr">{{titre}}</span>
          <Prets/>
          <Boss/>
      </h2>
    </div>
    <div class="content">
      <p class="en_avant"><span>{{infosun.partie_1}} </span>{{infosun.partie_2}}</p>
      <p class="en_avant"><span>{{infosdeux.partie_1}} </span>{{infosdeux.partie_2}}</p>
      <p class="en_avant"><span>{{infostrois.partie_1}} </span>{{infostrois.partie_2}}</p>
      <p>{{texte}}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Prets from '~/components/titres/prets'
import Boss from '~/components/titres/boss'

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
    Prets, Boss
  }
}
</script>