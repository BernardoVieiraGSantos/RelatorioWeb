<template>
  <router-view></router-view> <!-- Isso renderiza as rotas configuradas -->
</template>

<script>
export default {
  name: "App",
};
</script>


<style>
*{
  /* background: linear-gradient(135deg, #2a924a, #74c476); */
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

.btn-login {
  background: transparent;
  border: 2px solid white; /* Borda branca */

  @media (min-width: 768px) {
    border: 2px solid red; /* Borda branca */
  }
}

.btn-login:hover {
  background: rgba(255, 255, 255, 0.2); /* Fundo leve no hover */
}

.btn-register {
  background: rgba(255, 255, 255, 0.4); /* Um pouco mais opaco */
  border: none;
}

.btn-register:hover {
  background: rgba(255, 255, 255, 0.6);
}
</style>
