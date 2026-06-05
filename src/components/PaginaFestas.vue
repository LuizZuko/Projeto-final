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