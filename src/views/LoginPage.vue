<template>
  <div class="login-container">
    <div class="login-card">
      <div class="logo-section">
        <img src="@/assets/iconeLoja.png" alt="Logo" class="logo" />
        <h2>LojaFácil</h2>
      </div>
      <p class="description">Login</p>
      <form @submit.prevent="login">
        <div class="input-group">
          <i class="icon user-icon"></i>
          <input
            type="text"
            placeholder="Usuario"
            v-model="username"
            class="input"
          />
        </div>
        <div class="input-group">
          <i class="icon lock-icon"></i>
          <input
            type="password"
            placeholder="Senha"
            v-model="password"
            class="input"
          />
        </div>
        <p class="forgot-password">Esqueceu minha senha</p>
        <button class="btn btn-login" :disabled="isLoading" type="submit">
          <span v-if="!isLoading">Login</span>
          <span v-else class="loader"></span>
        </button>
        <button class="btn btn-register" type="button">Registrar</button>
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios"; // Importa o Axios

export default {
  name: "LoginPage",
  data() {
    return {
      username: "", // Nome de usuário inserido no formulário
      password: "", // Senha inserida no formulário
      isLoading: false, // Controla o estado de carregamento
      error: "", // Armazena mensagens de erro
      dados: null, // Armazena a resposta da API
    };
  },
  methods: {
    async login() {

      //atraves do form receber os valores de login e senha

      const json = {
          usuario: this.username,
          senha: this.password
        }

        var resposta = await axios.post("http://localhost:5003/autenticar", json);

        console.log(resposta.data)

        //nao tem necessidade de colocar == true, dessa forma que fiz ela ja enterpreta
        if(resposta.data.success){
          //logica para direcionar para a pagina de home
            console.log("Login bem  sucedido!");
            this.$router.push("/HomePage");
        }else{
          console.log('Login invalido')
        }
        return resposta
    },
  },
};
</script>




<style scoped>
/* Container geral */
.login-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: linear-gradient(135deg, #4caf50, #81c784);
}

/* Cartão de login */
.login-card {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  padding: 40px;
  border-radius: 20px;
  width: 340px;
  box-shadow: 0px 10px 20px rgba(0, 0, 0, 0.2);
  text-align: center;
}

/* Logo e título */
.logo-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 30px; /* Aumenta o espaçamento entre a logo e o próximo elemento */
  gap: 10px; /* Adiciona espaço entre os elementos dentro da seção */
}


.logo {
  width: 80px;
  height: 80px;
  border-radius: 30%;
  object-fit: cover;
  border: 2px solid white;
  margin-bottom: 20px; /* Aumenta o espaçamento abaixo da logo */
}


.logo-section h2 {
  margin: 10px 0 0;
  font-size: 1.5rem;
  font-weight: bold;
  color: white;
}

/* Responsividade */
@media (max-width: 480px) {
  .login-card {
    width: 280px;
  }

  .btn {
    padding: 10px;
    font-size: 0.9rem;
  }
}

/* Descrição */
.description {
  color: #d0d0d0;
  font-size: 1rem;
  margin-bottom: 30px;
}

/* Grupo de inputs */
.input-group {
  display: flex;
  align-items: center;
  border-bottom: 1px solid white;
  margin-bottom: 20px;
  padding: 5px 0;
}

.icon {
  font-size: 1.5rem;
  color: white;
  margin-right: 10px;
}

.user-icon::before {
  content: "👤";
  color: white;
}

.lock-icon::before {
  content: "🔒";
  color: white;
}

.input {
  flex: 1;
  border: none;
  background: none;
  outline: none;
  color: white;
  font-size: 1rem;
  padding: 5px 0;
}

.input::placeholder {
  color: #d0d0d0;
}

.input:focus {
  border-bottom: 2px solid #ece107; /* Cor destacada para o foco */
  transition: all 0.3s ease;
}


/* Esqueceu a senha */
.forgot-password {
  color: #15660da5;
  font-size: 0.9rem;
  margin-bottom: 20px;
  text-align: right;
  cursor: pointer;
}

.forgot-password:hover {
  text-decoration: underline;
}

/* Botões */
.btn {
  width: 100%;
  padding: 12px;
  border-radius: 25px;
  font-size: 1rem;
  font-weight: bold;
  cursor: pointer;
  margin-top: 15px; /* Espaçamento entre os botões */
  text-align: center;
  transition: all 0.3s ease;
}

.btn-login {
  background: transparent;
  color: white;
  border: 2px solid white; /* Borda branca */
}

.btn-login:hover {
  background: rgba(255, 255, 255, 0.2); /* Fundo leve no hover */
}

.btn-register {
  background: rgba(255, 255, 255, 0.4); /* Um pouco mais opaco */
  color: white;
  border: none;
}

.btn-register:hover {
  background: rgba(255, 255, 255, 0.6);
}

/* Botão com animação de carregamento */
.btn-login .loader {
  width: 20px;
  height: 20px;
  border: 3px solid white;
  border-top: 3px solid transparent;
  border-radius: 50%;
  animation: spin 1s linear infinite;
  display: inline-block;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

/* Desativar o botão enquanto carrega */
.btn[disabled] {
  background: #4caf50;
  color: #d0d0d0;
  border: 2px solid #d0d0d0;
  cursor: not-allowed;
}


</style>
