<template>
  <main id="errornotfound" role="main"></main>
</template>

<script>

export default {
  components: {
  },
  head () {
    return {
      title: 'Erreur 404 - Page non trouvée',
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        { hid: 'description', name: 'description', content: 'My custom description' }
      ]
    }
  },
  mounted() {
    document.querySelector('body').className = '';
    document.querySelector('body').classList.add('404');
  }
}
</script>
