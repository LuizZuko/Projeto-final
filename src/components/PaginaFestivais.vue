<template>
  <div class="festivais-container">
    <header class="festivais-header">
      <h2>Line-up de Festivais 2026</h2>
      <div class="botoes-filtros">
        <button :class="{ ativo: filtroSelecionado === 'todos' }" @click="filtroSelecionado = 'todos'">Todos</button>
        <button :class="{ ativo: filtroSelecionado === 'premium' }" @click="filtroSelecionado = 'premium'">Premium</button>
        <button :class="{ ativo: filtroSelecionado === 'sazonal' }" @click="filtroSelecionado = 'sazonal'">Sazonais</button>
      </div>
    </header>

    <section class="timeline-festivais">
      <p v-if="eventosFiltrados.length === 0" class="sem-resultado-festivais">Nenhum evento nesta categoria.</p>
      
      <div v-for="evento in eventosFiltrados" :key="evento.id" class="timeline-item">
        <div class="timeline-date">
          <span class="dia">{{ evento.data.split('/')[0] }}</span>
          <span class="mes">{{ converterMesTexto(evento.data.split('/')[1]) }}</span>
        </div>
        
        <div class="timeline-card">
          <img :src="evento.imagem" :alt="evento.nome" class="timeline-img" />
          <div class="timeline-details">
            <h3>{{ evento.nome }}</h3>
            <span class="tag-categoria">{{ evento.tipo.toUpperCase() }}</span>
            <p class="timeline-preco">A partir de: <strong>R$ {{ evento.preco.toFixed(2) }}</strong></p>
          </div>
          <button @click="$emit('abrir-modal', evento)" class="btn-timeline">Adquirir Passaporte</button>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

defineEmits(['abrir-modal']);
const filtroSelecionado = ref('todos');

const festivais = ref([
  { id: 8, nome: 'Festival de Inverno', data: '18/07/2026', preco: 180.00, tipo: 'sazonal', imagem: 'https://images.unsplash.com/photo-1506157786151-b8491531f063?auto=format&fit=crop&q=80&w=400' },
  { id: 9, nome: 'Arena Pop Festival', data: '05/09/2026', preco: 220.00, tipo: 'premium', imagem: 'https://images.unsplash.com/photo-1465847899084-d164df4dedc6?auto=format&fit=crop&q=80&w=400' },
  { id: 10, nome: 'Sertanejo Prime Weekend', data: '14/11/2026', preco: 300.00, tipo: 'premium', imagem: 'https://images.unsplash.com/photo-1472653431158-6364773b2a56?auto=format&fit=crop&q=80&w=400' }
]);

const eventosFiltrados = computed(() => {
  if (filtroSelecionado.value === 'todos') return festivais.value;
  return festivais.value.filter(evento => evento.tipo === filtroSelecionado.value);
});

const converterMesTexto = (mes) => {
  const mapeamento = { '07': 'JUL', '09': 'SET', '11': 'NOV' };
  return mapeamento[mes] || 'DEZ';
};
</script>

<style src="../assets/css/festivais.css" scoped></style>

