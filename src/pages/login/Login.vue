<template>
  <form @submit.prevent="doLogin()" class="form-login">
    <div class="card">
      <div class="card-header text-center">
        <h1>Fincontrol</h1>
      </div>
      <div class="card-body">
        <div class="form-group">
          <input
            required
            type="email"
            class="form-control"
            placeholder="E-mail"
            v-model="email"
          />
        </div>
        <div class="form-group">
          <input
            required
            type="password"
            class="form-control"
            placeholder="Senha"
            v-model="password"
          />
        </div>
        <button class="btn btn-primary w-100" :disabled="loading">
          <template v-if="loading">
            <i class="fa fa-spinner fa-spin"></i>
          </template>
          <template v-else>
            Entrar
            <i class="fa fa-sign-in-alt"></i>
          </template>
        </button>
      </div>
    </div>
  </form>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      loading: false,
      email: 'jackson@fincontrol.com.br',
      password: '123123'
    }
  },
  methods: {
    async doLogin() {
      this.loading = true
      const { email, password } = this
      try {
        const res = await this.$firebase.auth().signInWithEmailAndPassword(email, password)
        window.uid = res.user.uid
        this.$router.push({ name: 'home'})
      }
      catch(err) {
        console.log(err)
      }
      this.loading = false
    }
  },
  beforeRouterEnter(to, from, next) {
    next(vm => {
      if(window.uid) {
        vm.$router.push({ name: 'home' })
      }
    })
  }
}
</script>

<style lang="scss" scoped>
  .form-login {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
    > .card {
      widows: 25%;
      color: var(--darker);
      > .card-header {
        text-transform: uppercase;
        font-weight: 900;
        font-size: 2.0rem;
      }
    }
  }
</style>
