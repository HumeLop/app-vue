<template>
  <div>
    <h1>Registrarse</h1>
    <div class="register">
      <input type="text" v-model="nombre" placeholder="Nombre" />
      <input type="text" v-model="username" placeholder="Usuario" />
      <input type="password" v-model="password" placeholder="Contraseña" />
      <input
        type="password"
        v-model="passconf"
        placeholder="Confirmar Contraseña"
      />
      <button v-on:click="signUp">Registrarse</button>
    </div>
    <nav>
      <router-link to="/login">Inicia Sesión</router-link>
    </nav>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: "SignUp",
  data() {
    return {
      nombre: '',
      username: '',
      password: '',
      passconf: '',
    }
  },
  methods: {
    async signUp() {
      let result = await axios.post("http://localhost:3000/users",{
        nombre: this.nombre,
        username: this.username,
        password: this.password,
        passconf: this.passconf,

      });
      console.warn(result)
      if (result.status == 201) {
          this.$router.push({name:'login'})
      }
    },
  },
};
</script>

<style>
.register input {
  border: 1px solid skyblue;
  border-radius: 15px;
  display: block;
  height: 40px;
  margin-bottom: 30px;
  margin-left: auto;
  margin-right: auto;
  padding-left: 20px;
  width: 300px;
}
.register button {
  background-color: skyblue;
  border: 1px solid skyblue;
  cursor: pointer;
  color: #fff;
  height: 40px;
  width: 320px;
}
</style>