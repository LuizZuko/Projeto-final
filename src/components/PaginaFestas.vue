<template>
  <div class="festas-container">
    <div class="festa-hero">
      <div class="hero-content">
        <span class="hero-badge">DESTAQUE DA SEMANA</span>
        <h2>Rave Eletrônica Sunset</h2>
        <p>A maior experiência audiovisual do ano.</p>
        <button @click="$emit('abrir-modal', festaDestaque)" class="btn-hero">Reservar VIP</button>
      </div>
    </div>

    <section class="busca-section-festas">
      <h3>Outras Festas & Baladas</h3>
      <input type="text" v-model="termoBusca" placeholder="Filtrar eventos..." class="input-busca-festas" />
    </section>

    <section class="lista-horizontal-festas">
      <p v-if="eventosFiltrados.length === 0" class="sem-resultado-festas">Nenhuma festa localizada.</p>
      
      <div v-for="evento in eventosFiltrados" :key="evento.id" class="festa-row-item">
        <img :src="evento.imagem" :alt="evento.nome" class="row-img" />
        <div class="row-info">
          <h4>{{ evento.nome }}</h4>
          <p class="row-data">📅 Data: {{ evento.data }}</p>
          <p class="row-preco">R$ {{ evento.preco.toFixed(2) }}</p>
        </div>
        <button @click="$emit('abrir-modal', evento)" class="btn-comprar-row">Comprar</button>
      </div>
    </section>
  </div>
</template>