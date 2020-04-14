<template>
  <header>
    <div class="wrap">
      <nuxt-link id="logo" to="/">MMI Montbéliard</nuxt-link>
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