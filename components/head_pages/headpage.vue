<template>
  <div class="head_page wrap">
    <div class="content">
      <h1 class="bloc_title"><span class="show-for-sr">{{titre}}</span>
        <Balader/>
      </h1>
      <p>{{texte}}</p>
    </div>
    <img :src="image" alt=""/>
    <button class="ancre">Découvrir MMI Montbéliard</button>
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