<template>
  <div class="hello">
    <h1>Olá, {{ nome }}!</h1>
    <p>{{ mensagem }}</p>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    nome: {
      type: String,
      required: true,
    },
    mensagem: {
      type: String,
      default: "Bem-vindo ao sistema!",
    },
  },
};
</script>

<style scoped>
.hello {
  text-align: center;
  margin: 20px 0;
}
h1 {
  color: #000000;
  font-size: 2rem;
}
p {
  color: #000000;
  font-size: 1.2rem;
}
</style>
