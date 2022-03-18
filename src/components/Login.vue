<template>
  <div>
    <h1>Inicio de Sesión</h1>
    <div class="login">
      <input type="text" v-model="username" placeholder="Usuario" />
      <input type="password" v-model="password" placeholder="Contraseña" />
      <button v-on:click="login">Iniciar Sesión</button>
    </div>
    <nav>
      <router-link to="/sign-up">Registrate</router-link>
    </nav>
  </div>
</template>


<script>
import axios from "axios";
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Login",
  data() {
    return {
      username: "",
      password: "",
    };
  },
  methods: {
    async login() {
      let result = await axios.get(
        `http://localhost:3000/users?username=${this.username}&password=${this.password}`
      );
      console.log(result);
      if (result.status == 200 && result.data.length > 0) {
        this.$router.push({name:'home'})
      }
    },
  },
};
</script>


<style>
.login input {
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
.login button {
  background-color: skyblue;
  border: 1px solid skyblue;
  cursor: pointer;
  color: #fff;
  height: 40px;
  width: 320px;
}
</style>