<template>
  <div class="login-page">
    <div class="organoBanner"></div>
    <div class="main-container">
      <div class="row d-flex justify-content-center mt-5 mb-5">
        <div class="col-5 text-left login-form-container">
          <div class="d-flex justify-content-center">
            <img
              src="https://cdn0.iconfinder.com/data/icons/pretty-shop/512/1-512.png"
              width="70"
              alt=""
            />
          </div>
          <p class="h3 text-center">Autenticar como fornecedor</p>
          <br />
          <div>
            <div class="form-group">
              <label for="exampleInputEmail1">E-mail</label>
              <input
                type="email"
                class="form-control"
                id="exampleInputEmail1"
                aria-describedby="emailHelp"
                v-model="email"
              />
            </div>
            <div class="form-group">
              <label for="exampleInputPassword1">Senha</label>
              <input
                type="password"
                class="form-control"
                id="exampleInputPassword1"
                v-model="senha"
              />
            </div>
            <button
              @click="loginUsuario()"
              type="submit"
              class="btn btn-primary btn-block"
              style="border: none"
            >
              Login
            </button>
            <medium id="fornecedorNaoCadastrado" class="form-text text-muted"
              ><b>Não possui uma conta?</b></medium
            >
            <router-link
              type="submit"
              class="btn btn-primary btn-block"
              style="border: none"
              :to="'/cadastroFornecedor/'"
              >Cadastrar-se</router-link
            >
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { mapActions } from "vuex";
export default {
  name: "LoginFornecedor",
  data() {
    return {
      email: "",
      senha: "",
    };
  },
  methods: {
    ...mapActions("usuario", ["login"]),
    loginUsuario() {
      const user = {
        email: this.email,
        senha: this.senha,
        type: "fornecedor",
      };
      this.login(user);
    },
  },
};
</script>

<style>
.form-control {
  border-radius: 0%;
  height: 50px;
}
.login-form-container {
  padding: 20px;
  box-shadow: 0px 2px 5px 2px #888888;
}
</style>