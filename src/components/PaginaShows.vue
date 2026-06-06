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