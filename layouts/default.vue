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
  },
  mounted() {
    // Scroll event
    window.onscroll = function() {
        if(document.documentElement.scrollTop > 500 || document.body.scrollTop > 500) {
          document.body.classList.add('scrolled');
        } else if (document.documentElement.scrollTop < 500 || document.body.scrollTop < 500) {
          document.body.classList.remove('scrolled');
        }
    }
  }
}
</script>
