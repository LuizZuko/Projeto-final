<template>
  <div class="modal-overlay" @click.self="$emit('fechar')">
    <div class="modal-content">
      <h2>Comprar Ingresso</h2>
      <p style="margin-top: 12px;"><strong>Evento:</strong> {{ eventoSelecionado.nome }}</p>
      <p><strong>Valor Unitário:</strong> R$ {{ eventoSelecionado.preco.toFixed(2) }}</p>

      <form @submit.prevent="finalizarCompra">
        <div class="form-group">
          <label for="nome">Nome Completo:</label>
          <input type="text" id="nome" v-model="nomeComprador" required placeholder="Digite seu nome" />
        </div>