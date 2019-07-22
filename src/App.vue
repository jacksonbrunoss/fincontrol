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
    console.log(this.$firebase)
  }
}
</script>

<style lang="scss">

</style>
