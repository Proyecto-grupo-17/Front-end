<template>
  
  <div class="bg-light col-md-30" style="height:380px">
    <form class="px-4 py-3">
      <div class="form-group">
        <label for="exampleInputEmail1">Email</label>
        <input
          type="email"
          class="form-control"
          placeholder="example@example.com"
          id="exampleInputEmail1"
          aria-describedby="emailHelp"
          v-model="login.email"
        >
        <small id="emailHelp" class="form-text text-muted"
          >We'll never share your email with anyone else.</small
        >
      </div>
      <div class="form-group">
        <label for="exampleInputPassword1">Password</label>
        <input
          type="password"
          class="form-control"
          id="exampleInputPassword1"
          placeholder="Contraseña"
          v-model="login.password"
        >
      </div>
      <br>
      <div class="form-group">
        <div class="form-check">
          <input type="checkbox" class="form-check-input" id="dropdownCheck">
          <label class="form-check-label" for="dropdownCheck">
            Recuerdame
          </label>
        </div>
      </div>
      <!-- <pre>
          {{ login }}
      </pre> -->
      <br>
      <div class="text-center">

      <button 
      type="submit" 
      class="btn btn-primary" 
      style="width:300px"
      @click.prevent="loginUser">
        Entrar
      </button>
      </div>
    </form>
  <div class="dropdown-divider"></div>
    <a class="dropdown-item text-center" href="#">Registrate</a>
    <a class="dropdown-item text-center" href="#">¿Olvido la contraseña?</a>
  </div>
</template>

<script>
import swal from 'sweetalert';
import jwt from "jsonwebtoken";
export default {
  data() {
    return {
      login: {
        email: '',
        password: '',
      },
    };
  },
  methods: {
    async loginUser() {
      try {
        console.log(this.login);
        let response = await this.$http.post('/api/usuario/signin', this.login);
        console.log(response.data.accessToken);
        let token = response.data.accessToken;
        var decoded = jwt.decode(token, {complete: true});
        // console.log(decoded.payload);
        let user = decoded.payload;

        localStorage.setItem('jwt', token);
        localStorage.setItem('user',JSON.stringify(user));
        if (token){
            swal("Login correcto", `Los datos son correctos, bienvenido!`, "success");
            this.$router.push('/home');
        }
      } catch (e) {
        // console.log(e);
        swal("Oops!","Algo salio mal", "error");
      }
    },
  },
};
</script>
