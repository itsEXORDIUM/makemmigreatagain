<template>
  <header>
    <nuxt-link to="/">MMI Montbéliard</nuxt-link>
    <uiNav/>
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