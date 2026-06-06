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
    imagem:  
},

  { 
    id: 2, 
    nome: 'João Gomes', 
    data: '22/10/2026', 
    preco: 150.00, 
    imagem:  
},

  { 
    id: 3,
    nome: 'Tarcísio do Acordeon', 
    data: '05/11/2026', 
    preco: 90.00, 
    imagem:  
},

  { 
    id: 4, 
    nome: 'Nattan', 
    data: '12/11/2026', 
    preco: 180.00, 
    imagem:  
}

]);

const eventosFiltrados = computed(() => {
  return shows.value.filter(evento => evento.nome.toLowerCase().includes(termoBusca.value.toLowerCase()));
});
</script>