<template>
  <div class="modal-overlay" @click.self="$emit('fechar')">
    <div class="modal-content">
      <h2>Comprar Ingresso</h2>
      <p style="margin-top: 12px;"><strong>Evento:</strong> {{ eventoSelecionado.nome }}</p>
      <p><strong>Valor Unitário:</strong> R$ {{ eventoSelecionado.preco.toFixed(2) }}</p>