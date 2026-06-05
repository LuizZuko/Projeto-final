<template>
  <div class="card">
    <img :src="evento.imagem" :alt="evento.nome" class="card-img" />
    <div class="card-content">
      <div>
        <h3>{{ evento.nome }}</h3>
        <p class="data">Data: {{ evento.data }}</p>
        <p class="preco">R$ {{ evento.preco.toFixed(2) }}</p>
      </div>
      <button @click="$emit('abrir-modal', evento)" class="btn-comprar">
        Comprar Ingresso
      </button>
    </div>
  </div>
</template>