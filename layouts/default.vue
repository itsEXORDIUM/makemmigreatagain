<template>
  <div>
    <uiHeader/>
    <nuxt/>
  </div>
</template>

<script>
import axios from 'axios'
import uiHeader from '~/components/header/uiHeader'

export default {
  components: {
    uiHeader
  }
}
</script>
