<template>
    <div>
      <h1>Lista de Usuários</h1>
      <div v-if="error" class="error">
        <p>Erro ao carregar os usuários: {{ error }}</p>
      </div>
      <ul v-if="users.length > 0">
        <li v-for="user in users" :key="user.id">{{ user.name }}</li>
      </ul>
      <p v-else>Carregando usuários...</p>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue';
  
  // Variáveis reativas para armazenar os dados
  const users = ref([]);
  const error = ref(null);
  
  // Função para buscar os usuários
  const fetchUsers = async () => {
    try {
      const response = await fetch('https://jsonplaceholder.typicode.com/users');
      if (!response.ok) {
        throw new Error('Falha ao carregar os dados');
      }
      users.value = await response.json();
    } catch (err) {
      error.value = err.message;
    }
  };
  
  // Chama a função ao montar o componente
  onMounted(fetchUsers);
  </script>
  
  <style scoped>
  .error {
    color: red;
    font-weight: bold;
  }
  </style>
  