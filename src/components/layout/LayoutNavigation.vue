<template>
  <nav class="nav flex-column justify-content-between">
        <div class="menu">
          <router-link
            exact
            exact-active-class="active"
            class="nav-link"
            :key="i"
            :to="{ name: router.name }"
            v-for="(router, i) in routerLinks"
          >
            <i class="fa" :class="`fa-${router.meta.icon}`"></i>
            {{ router.meta.title }}
          </router-link>
          <LayoutNewExpense />
        </div>
        <LayoutLogout />
  </nav>
</template>

<script>
import LayoutLogout from './LayoutLogout'
import LayoutNewExpense from './LayoutNewExpense'
export default {
  name: 'LayoutNavigation',
  components: {
    LayoutLogout,
    LayoutNewExpense
  },
  computed: {
    routerLinks () {
      return this.$router.options.routes.filter(r => r.name !== 'login')
    }
  }
}
</script>

<style scoped lang="scss">
  .nav {
    margin-left: -15px;
    height: calc(100vh - 49px);
    width: calc(100% + 30px);
      > .menu {
        > .nav-link {
        transition: .4s;
        color: var(--white);
          &.active {
            color: var(--featured);
          }
          &:hover {
            color: var(--dark);
            background-color: var(--featured);
          }
        }
      }
  }
</style>
