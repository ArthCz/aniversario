<template>
    <div class="componente">
      <h1>Aniversariante</h1>
      <p>Nome: {{ nomePessoa }}</p>
      <p>Idade: {{ idade }}</p>
  
      <button @click="fazerAniversario" class="btn-primary">Fazer Aniversário</button>
  
      <div v-if="idade === 31" class="presente">
        <h2>🎁 UAU! Você ganhou um presente! 🎁</h2>
        <p>Pra você não dizer que nunca te dei nada... Estou falido, mas pegue seu presente que nunca irá usar 😂</p>
        <p>Perdão por ser paia, espero um dia melhorar como amigo.</p>
  
        <div class="text-center">
          <button @click="toggleGiftMenu" class="btn-success">
            Receber Presente
          </button>
  
          <div v-if="giftMenuAberto" class="presente-container">
            <p class="font-bold">Chave da Steam:</p>
            <div class="chave">MZ8ZK-W9P74-JRZA6</div>
            <button @click="copiarChave" class="btn-copy">
              Copiar Chave
            </button>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from "vue";
  
  const nomePessoa = ref("Yuri Uzumaki");
  const idade = ref(30);
  const giftMenuAberto = ref(false);
  
  function fazerAniversario() {
    idade.value += 1;
  }
  
  function toggleGiftMenu() {
    giftMenuAberto.value = !giftMenuAberto.value;
  }
  
  function copiarChave() {
    const chave = "MZ8ZK-W9P74-JRZA6";
    navigator.clipboard.writeText(chave).then(() => {
      alert("Chave copiada!");
    });
  }
  </script>
  
  <style scoped>
 
  .btn-primary, .btn-success, .btn-copy {
    background-color: #006400;
    color: #00ff00;
    border: none;
    padding: 10px 15px;
    margin: 10px;
    cursor: pointer;
    border-radius: 5px;
    transition: background 0.3s;
  }
  
  .btn-primary:hover, .btn-success:hover, .btn-copy:hover {
    background-color: #008000;
  }
  
 
  .presente {
    margin-top: 20px;
    padding: 15px;
    border: 2px solid #00ff00;
    background-color: #001a00;
    border-radius: 5px;
  }
  
 
  .chave {
    background-color: #002200;
    padding: 10px;
    margin-top: 10px;
    border: 1px dashed #00ff00;
    display: inline-block;
    font-weight: bold;
    color: #00ff00;
  }
  </style>
  