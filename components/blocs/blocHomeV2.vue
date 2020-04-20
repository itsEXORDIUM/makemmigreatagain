<template>
  <div :class="`bloc_home wrap ${name}`">
    <div class="ligne">
      <div>
        <h2 class="bloc_titre">
          <span class="show-for-sr">{{titre}}</span>
          <span v-if="bloc == 'altini'">
            <Alternanceini/>
          </span>
        </h2>
      </div>
      <div>
        <img :src="images.image_1" alt=""/>
      </div>
    </div>
    <div class="ligne">
      <div>
        <h3 class="subtitle">{{soustitre}}</h3>
        <p v-if="texte">{{texte}}</p>
        <nuxt-link v-if="lien" :to="lien" class="action big">En savoir plus</nuxt-link>
      </div>
      <div>
        <img :src="images.image_2" alt=""/>
      </div>
    </div>
  </div>
</template>

<script>
import Alternanceini from '~/components/titres/alternanceouini'

export default {
  props: {
      name: '',
      titre: '',
      soustitre: '',
      texte: '',
      lien: '',
      images: Array,
      image: ''
  },
  components: {
    Alternanceini
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
      if(this.name == 'altini') {
        this.bloc = 'altini';
      }
    }
  }
}
</script>