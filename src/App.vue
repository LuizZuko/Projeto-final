<template>
  <div id="app">
    <header class="navbar">
      <h1>Pisada Prime</h1>
      <nav>
        <a href="#" :class="{ ativo: paginaAtual === 'shows' }" @click.prevent="paginaAtual = 'shows'">Shows</a>
        <a href="#" :class="{ ativo: paginaAtual === 'festas' }" @click.prevent="paginaAtual = 'festas'">Festas & Baladas</a>
        <a href="#" :class="{ ativo: paginaAtual === 'festivais' }" @click.prevent="paginaAtual = 'festivais'">Festivais</a>
      </nav>
    </header>

    <main class="container">
      <PaginaShows v-if="paginaAtual === 'shows'" @abrir-modal="prepararFluxoCompra" />
      <PaginaFestas v-else-if="paginaAtual === 'festas'" @abrir-modal="prepararFluxoCompra" />
      <PaginaFestivais v-else-if="paginaAtual === 'festivais'" @abrir-modal="prepararFluxoCompra" />
    </main>

    <ModalCompra 
      v-if="modalAberto" 
      :evento-selecionado="eventoAtual" 
      @fechar="modalAberto = false"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import PaginaShows from './components/PaginaShows.vue';
import PaginaFestas from './components/PaginaFestas.vue';
import PaginaFestivais from './components/PaginaFestivais.vue';
import ModalCompra from './components/ModalCompra.vue';

const paginaAtual = ref('shows');
const modalAberto = ref(false);
const eventoAtual = ref(null);