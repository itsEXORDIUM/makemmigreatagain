<template>
  <div class="head_page">
    <div class="left">
      <div class="content wrap">
        <div v-html="headPage"></div>
        <nuxt-link to="/formation" class="action big dark">Voir le profil des étudiants</nuxt-link>
      </div>
    </div>
    <div class="right">
      <img src="~/static/imgs/students.png" alt=""/>
    </div>
    <button tabindex="0" aria-label="Découvrir MMI Montbéliard" role="button" class="ancre">Découvrir MMI Montbéliard</button>
  </div>
</template>

<script>
export default {
  props: {
    headPage: ''
  }
}
</script>