<template>
    <div class="formulario-card">
      <div class="card__content">
        <form @submit.prevent="handleSubmit">
          <div>
            <label for="marca">Marca do Celular:</label>
            <input id="marca" v-model="novoCelular.marca" placeholder="Marca do Celular" required />
          </div>
          <div>
            <label for="modelo">Modelo:</label>
            <input id="modelo" v-model="novoCelular.modelo" placeholder="Digite o modelo" required />
          </div>
          <div>
            <label for="ano">Ano:</label>
            <input id="ano" v-model="novoCelular.ano" placeholder="Digite o ano" type="number" min="2000" max="2024" required />
          </div>
          <button type="submit" class="add-button">Adicionar Celular</button>
        </form>
        <p v-if="erro" class="error-message">{{ erro }}</p>
      </div>
    </div>
  </template>
  
  <script setup>
  import { reactive, ref, defineEmits } from 'vue';
  
  const novoCelular = reactive({
    marca: '',
    modelo: '',
    ano: ''
  });
  
  const erro = ref('');
  const emit = defineEmits(['adicionar']);
  
  const handleSubmit = () => {
    if (!novoCelular.marca || !novoCelular.modelo || !novoCelular.ano) {
      erro.value = 'Por favor, preencha todos os campos corretamente.';
      return;
    }
  
    emit('adicionar', { ...novoCelular });
    limparFormulario();
  };
  
  const limparFormulario = () => {
    novoCelular.marca = '';
    novoCelular.modelo = '';
    novoCelular.ano = '';
    erro.value = '';
  };
  </script>
  
  <style scoped>
  body {
    margin: 0;
    padding: 0;
    background-image: linear-gradient(to right, #6a11cb, #2575fc);
    height: 100vh;
  }

  .container {
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
    font-family: Arial, sans-serif;
    text-align: center;
  }

  .card {
    width: 300px;
    border-radius: 20px;
    padding: 10px;
    box-shadow: rgba(151, 65, 252, 0.2) 0 15px 30px -5px;
    background-image: linear-gradient(144deg, #FF6B6B, #FFD93D);
    margin: 10px;
  }

  .formulario-card {
    width: 100%;
  }

  .card__content {
    background: rgb(5, 6, 45);
    border-radius: 17px;
    padding: 15px;
  }

  h2,
  p {
    color: white;
  }

  form div {
    margin-bottom: 10px;
  }

  input {
    width: 100%;
    padding: 8px;
    border-radius: 5px;
    border: 1px solid #ddd;
    margin-top: 5px;
  }

  button {
    background-color: #4CAF50;
    color: white;
    border: none;
    padding: 10px 15px;
    border-radius: 5px;
    cursor: pointer;
    margin-top: 10px;
  }

  button:hover {
    background-color: #45a049;
  }

  .delete-button {
    background-color: red;
    color: white;
    border: none;
    padding: 10px 15px;
    border-radius: 5px;
    cursor: pointer;
    margin-top: 10px;
  }

  .delete-button:hover {
    background-color: darkred;
  }

  .no-items-message {
    color: white;
    font-size: 1.2em;
    font-weight: bold;
    margin-top: 20px;
  }

  .error-message {
    color: red;
    margin-top: 10px;
  }

  .temas {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 20px;
  }
</style>