<template>
  <div class="head_page wrap">
    <div class="content">
      <h1 class="bloc_title"><span class="show-for-sr">{{titre}}</span>
        <Balader/>
      </h1>
      <p>{{texte}}</p>
    </div>
    <img :src="image" alt=""/>
    <button class="ancre" tabindex="0" aria-label="Découvrir MMI Montbéliard" role="button" ><span class="show-for-sr">Découvrir MMI Montbéliard</span></button>
  </div>
</template>

<script>
import Balader from '~/components/titres/balader'

export default {
  props: {
    titre: '',
    image:'',
    texte:''
  },
  components: {
    Balader
  }
}
</script>