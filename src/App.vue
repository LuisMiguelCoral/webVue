<template>
  <div class="container">
    <h1>Pesquisa de Celulares</h1>

    <div class="card formulario-card">
      <div class="card__content">
        <form @submit.prevent="adicionarCelular">
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

    <div class="temas">
      <p v-if="listaCelulares.length === 0" class="no-items-message">Nenhum celular cadastrado.</p>
      <div v-for="(celular, index) in listaCelulares" :key="index" class="card">
        <div class="card__content">
          <h2>{{ celular.marca }}</h2>
          <p>Modelo: {{ celular.modelo }}</p>
          <p>Ano: {{ celular.ano }}</p>
          <button @click="removerCelular(index)" class="delete-button">Deletar</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive, ref } from 'vue'

const novoCelular = reactive({
  marca: '',
  modelo: '',
  ano: ''
})

const listaCelulares = ref([])
const erro = ref('')

const adicionarCelular = () => {
  if (!novoCelular.marca || !novoCelular.modelo || !novoCelular.ano) {
    erro.value = 'Por favor, preencha todos os campos corretamente.'
    return
  }

  listaCelulares.value.push({ ...novoCelular })
  limparFormulario()
}

const limparFormulario = () => {
  novoCelular.marca = ''
  novoCelular.modelo = ''
  novoCelular.ano = ''
  erro.value = ''
}

const removerCelular = (index) => {
  listaCelulares.value.splice(index, 1)
}
</script>

<style>
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

h2, p {
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
