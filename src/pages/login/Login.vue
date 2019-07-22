<template>
  <form class="form-login">
    <div class="card">
      <div class="card-header text-center">
        <h1>Fincontrol</h1>
      </div>
      <div class="card-body">
        <div class="form-group">
          <input type="text" class="form-control" placeholder="E-mail" />
        </div>
        <div class="form-group">
          <input type="password" class="form-control" placeholder="Senha" />
        </div>
        <button class="btn btn-primary w-100">Enviar</button>
      </div>
    </div>
  </form>
</template>

<script>
export default {

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
