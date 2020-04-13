<template>
  <div class="head_page">
    <div v-html="headPage"></div>
    <nuxt-link to="/" class="action">Voir le profil des étudiants</nuxt-link>
  </div>
</template>

<script>
export default {
  props: {
    headPage: ''
  }
}
</script>