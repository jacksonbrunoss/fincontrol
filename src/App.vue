<template>
  <div id="app">
    <BaseSpinner />

    <div class="container-fluid" v-if="isLogged">
      <div class="row">
        <div class="col-2 navigation-sidebar">
          <h2 class="app-title">fincontrol</h2>
          <layoutNavigation />
        </div>
        <div class="col">
          <router-view />
        </div>
      </div>
    </div>
    <router-view v-else />
  </div>
</template>
<script>
import BaseSpinner from '@/components/global/BaseSpinner.vue'
import LayoutNavigation from '@/components/layout/LayoutNavigation.vue'
export default {
  name: "App",
  data: () => ({ isLogged: false }),
  components: {
    BaseSpinner,
    LayoutNavigation
  },
  methods: {

  },
  mounted () {
    this.$firebase.auth().onAuthStateChanged(user => {
      window.uid = user ? user.uid : null
      this.isLogged = !!user

      this.$router.push({ name: window.uid ? 'home' : 'login' })
      setTimeout(() => {
        this.$root.$emit('Spinner::hide')
      }, 300)
    })
  }
}
</script>

<style lang="scss">
  #app {
    min-height: 100vh;
  }
  .navigation-sidebar {
      background-color: var(--dark);
      color: #fff;
      > .app-title {
        font-size: 1.5rem;
        margin-top: 10px;
        text-align: center;
      }
    }
</style>
