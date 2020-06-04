<template>
  <header role="header">
    <div class="wrap">
      <nuxt-link title="Aller à l'accueil" id="logo" to="/">MMI Montbéliard</nuxt-link>
      <uiNav/>
    </div>
  </header>
</template>

<script>
import uiNav from '~/components/header/uiNav'

export default {
components: {
    uiNav
  }
}
</script>