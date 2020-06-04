<template>
  <div class="head_page wrap">
    <h1 class="bloc_title"><span class="show-for-sr">{{titre}}</span>
      <span v-if="bloc == 'bienvenue'">
        <Bienvenue/>
      </span>
      <span v-if="bloc == 'venezvoir'">
        <VenezVoir/>
      </span>
    </h1>
    <div class="content">
      <img :src="image" alt=""/>
      <img v-if="bloc == 'venezvoir'" src="~/static/imgs/map.PNG" alt=""/>
      <p>{{texte}}</p>
      <nuxt-link to="/postuler" class="action big">Postuler <span v-if="quandmeme">quand même !</span></nuxt-link>
    </div>

    <button class="ancre"><span class="show-for-sr">Découvrir MMI Montbéliard</span></button>
  </div>
</template>

<script>
import Bienvenue from '~/components/titres/bienvenue'
import VenezVoir from '~/components/titres/venezvoir'

export default {
  props: {
    titre: '',
    image:'',
    texte:'',
    quandmeme: Boolean,
    name: ''
  },
  components: {
    Bienvenue, VenezVoir
  },
  data() {
    return {
      bloc: ''
    }
  },
  mounted() {
    this.checkBloc();
  },
  methods: {
    checkBloc: function() {
      if(this.name == 'bienvenue') {
        this.bloc = 'bienvenue';
      } else if (this.name =='venezvoir') {
        this.bloc = 'venezvoir';
      }
    }
  }
}
</script>