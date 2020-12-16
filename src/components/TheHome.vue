<template>
  <div class="container">
    <h1>Bienvenido {{ user.name }}</h1>
    <p> En esta pagina podrás contar con toda la información diligenciada en la base de datos</p>
    <div class="container col-md-9">

    <nav class="navbar navbar-light bg-light" >
      <a class="navbar-brand">Información de contacto</a>
      <form class="form-inline">
        <button
          class="btn btn-outline-info my-2 my-sm-0"
          type="submit"
          @click.prevent="logOutUser"
          > Cerrar sesión
        </button>
      </form>
    </nav>
    <ul class="list-group">
      <li class="list-group-item"><span>Nombre: </span>{{ user.name }}</li>
      <li class="list-group-item"><span>Email: </span>{{ user.email }}</li>
    </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: {}
    }
  },
  methods: {
    logOutUser() {
      localStorage.removeItem('jwt');
      localStorage.removeItem('user');
      this.$router.push('/');
    },
    getUserData() {
      let token = localStorage.getItem('jwt');
      let user = localStorage.getItem('user');
      this.user = JSON.parse(user);
    }
  },
  created () {
    this.getUserData();
  },
}
</script>