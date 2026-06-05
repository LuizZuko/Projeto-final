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

<script setup>
import { ref, computed } from 'vue';

defineEmits(['abrir-modal']);
const termoBusca = ref('');

const festaDestaque = { id: 6, nome: 'Rave Eletrônica Sunset', data: '08/01/2027', preco: 250.00 };

const festas = ref([
  { id: 5, nome: 'Festa do Branco', data: '20/12/2026', preco: 80.00, imagem: 'https://images.unsplash.com/photo-1514525253161-7a46d19cd819?auto=format&fit=crop&q=80&w=400' },
  { id: 7, nome: 'Baile de Máscaras', data: '15/02/2027', preco: 100.00, imagem: 'https://images.unsplash.com/photo-1533174000287-4015c19cb074?auto=format&fit=crop&q=80&w=400' }
]);

const eventosFiltrados = computed(() => {
  return festas.value.filter(evento => evento.nome.toLowerCase().includes(termoBusca.value.toLowerCase()));
});
</script>

<style src="../assets/css/festas.css" scoped></style>