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
        <button class="btn btn-primary w-100">Entrar</button>
      </div>
    </div>
  </form>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    async doLogin() {
      const { email, password } = this
      try {
        const res = await this.$firebase.auth().signInWithEmailAndPassword(email, password)
        console.log(res)
      }
      catch(err) {
        console.log(err)
      }
    }
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
