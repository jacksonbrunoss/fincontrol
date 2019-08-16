<template>
  <button class="btn btn-logout" @click="logout()">
    <i class="fa fa-power-off"></i>
    Sair
  </button>
</template>

<script>
export default {
  name: 'LayoutLogout',
  methods: {
    async logout() {
      this.$root.$emit('Spiner::show')

      await this.$firebase.auth().signOut()
      this.$router.push({ name: 'login'})

      this.$root.$emit('Spiner::hide')
    }
  }
}
</script>

<style scoped lang="scss">
  .btn-logout {
    width: 100%;
    cursor: pointer;
    color: var(--white) !important;
    &:hover {
      color: var(--featured) !important;
    }
  }
</style>
