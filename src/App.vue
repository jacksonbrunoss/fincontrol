<template>
  <div id="app">
    <BaseSpinner />
    <router-view/>
  </div>
</template>
<script>
import BaseSpinner from '@/components/global/BaseSpinner.vue'
export default {
  name: "App",
  components: {
    BaseSpinner
  },
  methods: {

  },
  mounted () {
    this.$firebase.auth().onAuthStateChanged(user => {
      window.uid = user ? user.uid : null
      this.$router.push({ name: window.uid ? 'home' : 'login' })
      setTimeout(() => {
        this.$root.$emit('Spinner::hide')
      }, 300)
    })
  }
}
</script>

<style lang="scss">

</style>
