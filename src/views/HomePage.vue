<template>
  <div class="homepage">
    <!-- Saudação Dinâmica -->
    <HelloWorld nome="Bernardo" mensagem="Bem-vindo de volta!" class="saudacao" />
    
    <!-- Menu Principal -->
    <main class="menu">
      <button class="button" @click="abrirRelatorios">
        <div class="icon-container">
          📄 
        </div>
        <p>Relatórios</p>
      </button>

      <button class="button" @click="abrirVender">
        <div class="icon-container">
          🛒 
        </div>
        <p>Vender</p>
      </button>

      <button class="button" @click="abrirEstoque">
        <div class="icon-container">
          📦 
        </div>

        <!-- <img src="../CaminhoDoArquivo" alt=""> -->

        
        <span>Estoque</span>
      </button>
    </main>

    <!-- "Fale Conosco" -->
    <button class="help-button" @click="faleConosco">
      <i class="fas fa-phone-alt"></i> Fale Conosco
    </button>

    <!-- Logout -->
    <button class="logout-button" @click="logout">
      ➡ 
    </button>
  </div>
</template>

<script>
import HelloWorld from "@/components/HelloWorld.vue"; // Importando o componente 

export default {
  name: "HomePage",
  components: {
    HelloWorld, // Registra o componente
  },
  methods: {
    abrirRelatorios() {
      console.log("Abrir Relatórios");
    },
    abrirVender() {
      console.log("Abrir Vender");
    },
    abrirEstoque() {
      console.log("Abrir Estoque");
    },
    faleConosco() {
      console.log("Fale Conosco");
    },
    logout() {
      console.log("Logout");
    },
  },
};
</script>

<style scoped>

/* Página principal */
.homepage {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background: linear-gradient(135deg, #2a924a, #74c476);
  color: #fff;
  font-family: "Arial", sans-serif;
  position: relative;
  
}

/* Saudação no canto superior esquerdo */
.saudacao {
  position: absolute;
  top: 20px;
  left: 20px;
  font-size: 1.5rem; /* Aumenta o tamanho da saudação */
  text-align: left;
  color: #fff;
}

/* Menu de botões maior */
.menu {
  display: flex;
  flex-direction: column;
  gap: 2rem; /* Aumenta o espaçamento entre os botões */
  margin-top: 100px; /* Espaçamento maior abaixo da saudação */
  width: 80%; /* Aumenta a largura do menu */
  max-width: 400px; /* Limita a largura máxima */
}

.button {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: flex-start;
  background: rgba(255, 255, 255, 0.2); /* Fundo mais visível */
  padding: 1.5rem 2rem; /* Aumenta o tamanho do botão */
  width: 100%; /* Botão ocupa toda a largura do menu */
  border: none;
  border-radius: 10px;
  cursor: pointer;
  transition: transform 0.3s, background-color 0.3s;
  color: #fff;
  font-size: 1.2rem; /* Aumenta o tamanho do texto do botão */
}

.button:hover {
  transform: scale(1.05);
  background: rgba(255, 255, 255, 0.3); /* Hover mais claro */
}

/* Ícones nos botões */
.icon-container {
  width: 50px; /* Aumenta o tamanho do ícone */
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 1.5rem; /* Aumenta o espaço entre o ícone e o texto */
  font-size: 2rem; /* Aumenta o tamanho do ícone */
}

/* Botão "Fale Conosco" */
.help-button {
  position: absolute;
  bottom: 20px;
  right: 20px;
  background: rgba(255, 255, 255, 0.2);
  border: none;
  padding: 0.8rem 1.5rem;
  border-radius: 20px;
  color: #fff;
  font-size: 1rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  cursor: pointer;
  transition: transform 0.3s, background-color 0.3s;
}

.help-button:hover {
  background: rgba(255, 255, 255, 0.3);
  transform: scale(1.1);
}

/* Botão de Logout */
.logout-button {
  position: absolute;
  top: 20px;
  right: 20px;
  background: none;
  border: none;
  color: #fff;
  font-size: 1.5rem;
  cursor: pointer;
  transition: transform 0.2s ease-in-out;
}

.logout-button:hover {
  transform: scale(1.1);
}
</style>
