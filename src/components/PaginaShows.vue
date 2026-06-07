<script setup>
import { ref, computed } from 'vue';
import CardEvento from './CardEvento.vue';

defineEmits(['abrir-modal']);
const termoBusca = ref('');

const shows = ref([
  { 
    id: 1, 
    nome: 'Os Barões da Pisadinha', 
    data: '15/10/2026', 
    preco: 120.00, 
    imagem: 'Baroes.jfif'
},

  { 
    id: 2, 
    nome: 'João Gomes', 
    data: '22/10/2026', 
    preco: 150.00, 
    imagem: 'João.jfif'
},

  { 
    id: 3,
    nome: 'Tarcísio do Acordeon', 
    data: '05/11/2026', 
    preco: 90.00, 
    imagem: 'Tarcisio.jfif' 
},

  { 
    id: 4, 
    nome: 'Filho do piseiro', 
    data: '12/11/2026', 
    preco: 180.00, 
    imagem: 'Filho.jfif'
}

]);

const eventosFiltrados = computed(() => {
  return shows.value.filter(evento => evento.nome.toLowerCase().includes(termoBusca.value.toLowerCase()));
});
</script>

<template>
  <div class="shows-page">
    <section class="busca-section-shows">
      <h2>Shows Nordestinos</h2>
      <p>O melhor do Forró, Piseiro e Arrocha!</p>
      <input type="text" v-model="termoBusca" placeholder="Busque por artista..." class="input-busca-shows" />
    </section>

    <section class="grid-eventos-shows">
      <p v-if="eventosFiltrados.length === 0" class="sem-resultado-shows">Nenhum show encontrado.</p>
      
      <CardEvento 
        v-for="evento in eventosFiltrados" 
        :key="evento.id" 
        :evento="evento"
        @abrir-modal="(e) => $emit('abrir-modal', e)"
      />
    </section>
  </div>
</template>


<style src="../assets/css/shows.css" scoped></style>
