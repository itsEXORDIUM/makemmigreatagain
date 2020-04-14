<template>
  <div>
    <uiHeader/>
    <nuxt/>
    <uiFooter/>
  </div>
</template>

<script>
import axios from 'axios'
import uiHeader from '~/components/header/uiHeader'
import uiFooter from '~/components/uiFooter'

export default {
  components: {
    uiHeader, uiFooter
  }
}
</script>
