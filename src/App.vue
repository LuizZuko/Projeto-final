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