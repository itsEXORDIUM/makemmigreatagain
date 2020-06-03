<template>
  <div :class="`bloc_home v2 wrap ${name}`">
    <div class="ligne">
        <h2 class="bloc_titre">
          <span class="show-for-sr">{{titre}}</span>
            <Forums/>
        </h2>
    </div>
    <div class="ligne">
      <div>
        <img :src="image" alt=""/>
      </div>
      <div>
        <p>{{texte}}</p>
      </div>
    </div>
    <div class="ligne">
      <div>
        <h3 class="bloc_titre">
          <span class="show-for-sr">{{titredeux}}</span>
            <Jpo/>
        </h3>
        <p>{{textedeux}}</p>
      </div>
      <div>
        <img :src="imagedeux" alt=""/>
      </div>
    </div>
  </div>
</template>

<script>
import Forums from '~/components/titres/forums'
import Jpo from '~/components/titres/jpo'

export default {
  props: {
      name: '',
      titre: '',
      titredeux: '',
      texte: '',
      textedeux: '',
      image: '',
      imagedeux: ''
  },
  components: {
    Forums, Jpo
  }
}
</script>