<!-- src/components/FormCard.vue -->
<template>
    <div class="container">
      <div class="card formulario-card">
        <div class="card__content">
          <h2>Título do Formulário</h2>
          <form>
            <div>
              <label for="campo">Campo</label>
              <input type="text" id="campo" />
            </div>
            <button type="submit">Enviar</button>
            <button class="delete-button">Excluir</button>
          </form>
        </div>
      </div>
      <p class="no-items-message">Nenhum item encontrado</p>
      <p class="error-message">Erro ao carregar itens</p>
    </div>
  </template>
  
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
  