<template>
  <div class="min-h-screen bg-[#FDF8F1] text-[#5D2E17] font-sans">
    
    <header class="border-b border-orange-200/50 bg-[#8B4513] sticky top-0 z-50 shadow-md">
      <div class="container mx-auto px-6 py-4 flex justify-between items-center">
        <div class="flex items-center gap-3">
          <div class="h-10 w-10 bg-[#E67E22] rounded-xl flex items-center justify-center font-black text-white shadow-sm">
            H
          </div>
          <div>
            <span class="text-xl font-black uppercase tracking-tight text-white">Huamelollan</span>
            <p class="text-[9px] text-orange-200/70 font-mono tracking-widest">
              ITGAM - TECNM
            </p>
          </div>
        </div>
        
        <nav class="hidden md:flex items-center gap-8 text-sm font-semibold text-orange-100/80">
          <NuxtLink to="/cultura" class="text-white transition-colors duration-200 border-b-2 border-[#E67E22] pb-1">1. Cultura</NuxtLink>
          <NuxtLink to="/historias" class="hover:text-white transition-colors duration-200">2. Historias</NuxtLink>
          <NuxtLink to="/aprender" class="hover:text-white transition-colors duration-200">3. Aprender</NuxtLink>
          <NuxtLink to="/perfil" class="hover:text-white transition-colors duration-200">4. Perfil</NuxtLink>
        </nav>
        
        <span class="text-xs text-[#E67E22] bg-white/10 px-3 py-1 rounded-full font-mono uppercase tracking-widest hidden sm:block">
          Halcón Peregrino v2.6
        </span>
      </div>
    </header>

    <main class="container mx-auto px-6 py-10">
      
      <div class="flex justify-between items-center mb-12 border-b border-orange-200/50 pb-6">
        <div>
          <h1 class="text-3xl font-black uppercase tracking-tighter">
            01. Cultura - Huamelollan
          </h1>
          <p class="text-xs text-[#8B4513]/70 font-bold uppercase tracking-widest mt-1">
            Módulo de conocimiento tradicional
          </p>
        </div>
        <NuxtLink
          to="/"
          class="px-5 py-2.5 bg-[#FDF8F1] border border-orange-200 text-[#E67E22] text-xs font-bold rounded-xl hover:bg-[#E67E22] hover:text-white transition-all shadow-sm"
        >
          Volver al Inicio
        </NuxtLink>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-4 gap-6">
        <div
          v-for="(cat, index) in categorias"
          :key="index"
          class="bg-white p-6 rounded-3xl border border-orange-100 hover:border-[#E67E22] transition-all group shadow-md hover:shadow-xl flex flex-col"
        >
          <div class="flex justify-between items-start mb-4">
            <div class="text-[#E67E22] text-xl font-mono font-black bg-[#FDF8F1] w-12 h-12 flex items-center justify-center rounded-xl border border-orange-50">
              0{{ index + 1 }}
            </div>
            <span class="text-3xl bg-[#FDF8F1] p-2 rounded-xl">{{ cat.emoji }}</span>
          </div>
          
          <h3 class="text-lg font-bold mb-2 text-[#5D2E17]">{{ cat.nombre }}</h3>
          <p class="text-xs text-[#8B4513]/70 mb-6 font-medium leading-relaxed flex-grow">{{ cat.desc }}</p>
          
          <button
            @click="verContenido(cat.nombre)"
            class="w-full py-3 bg-[#FDF8F1] text-[#E67E22] border border-orange-100 text-xs font-bold rounded-xl hover:bg-[#E67E22] hover:text-white transition-colors"
          >
            Ver Contenido
          </button>
        </div>
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref } from 'vue'

// Agregamos la propiedad 'emoji' a cada objeto
const categorias = ref([
  {
    nombre: 'Gastronomía',
    desc: 'Conoce los alimentos y platos tradicionales de Huamelollan.',
    emoji: '🥘'
  },
  {
    nombre: 'Tradiciones',
    desc: 'Un acercamiento a las celebraciones ancestrales.',
    emoji: '🕯️'
  },
  { 
    nombre: 'Danzas', 
    desc: 'El ritmo y movimiento de nuestra gente.',
    emoji: '🥁'
  },
  { 
    nombre: 'Vestimenta', 
    desc: 'El significado de los bordados y prendas.',
    emoji: '🧵'
  }
])

const verContenido = (nom) => {
  alert('Módulo de ' + nom + ' cargado correctamente.')
}
</script>