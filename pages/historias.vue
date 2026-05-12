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
          <NuxtLink to="/cultura" class="hover:text-white transition-colors duration-200">1. Cultura</NuxtLink>
          <NuxtLink to="/historias" class="text-white transition-colors duration-200 border-b-2 border-[#E67E22] pb-1">2. Historias</NuxtLink>
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
            02. Historias y Leyendas
          </h1>
          <p class="text-xs text-[#8B4513]/70 font-bold uppercase tracking-widest mt-1">
            Conoce la memoria ancestral del pueblo
          </p>
        </div>
        <NuxtLink
          to="/"
          class="px-5 py-2.5 bg-[#FDF8F1] border border-orange-200 text-[#8B4513] text-xs font-bold rounded-xl hover:bg-[#8B4513] hover:text-white transition-all shadow-sm"
        >
          Volver al Inicio
        </NuxtLink>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <div
          v-for="(historia, index) in tiposHistorias"
          :key="index"
          class="bg-white p-6 rounded-3xl border border-orange-100 hover:border-[#8B4513] transition-all group shadow-md hover:shadow-xl flex flex-col"
        >
          <div class="flex justify-between items-start mb-4">
            <div class="text-[#8B4513] text-xl font-mono font-black bg-[#FDF8F1] w-12 h-12 flex items-center justify-center rounded-xl border border-orange-50">
              0{{ index + 1 }}
            </div>
            <span class="text-3xl bg-[#FDF8F1] p-2 rounded-xl">{{ historia.emoji }}</span>
          </div>

          <h3 class="text-lg font-bold mb-2 text-[#5D2E17]">{{ historia.tipo }}</h3>
          <p class="text-xs text-[#8B4513]/70 mb-6 font-medium leading-relaxed">{{ historia.desc }}</p>

          <div class="space-y-3 mt-auto">
            <button
              v-for="categoria in historia.categorias"
              :key="categoria"
              @click="seleccionarCategoria(categoria)"
              class="w-full text-left px-4 py-3 text-xs font-bold rounded-xl border border-orange-100 text-[#8B4513]/80 hover:text-[#5D2E17] hover:border-[#8B4513] hover:bg-[#FDF8F1] transition-all flex items-center gap-2"
            >
              <span class="text-[#E67E22] text-sm">•</span> {{ categoria }}
            </button>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const tiposHistorias = ref([
  {
    tipo: 'Leyendas',
    desc: 'Narrativas sobre el origen y sucesos sobrenaturales.',
    emoji: '🌿',
    categorias: [
      'Leyendas de la Naturaleza',
      'Leyendas Ancestrales',
      'Leyendas de Animales'
    ]
  },
  {
    tipo: 'Cuentos',
    desc: 'Relatos de transmisión oral y moralejas.',
    emoji: '📚',
    categorias: [
      'Cuentos Tradicionales',
      'Cuentos Infantiles',
      'Cuentos Morales'
    ]
  },
  {
    tipo: 'Poemas',
    desc: 'Expresión poética y lírica de la región.',
    emoji: '📜',
    categorias: [
      'Poemas Ancestrales',
      'Poemas de la Naturaleza',
      'Poemas de Amor'
    ]
  }
])

const seleccionarCategoria = (cat) => {
  alert(
    'Se ha seleccionado la categoría: ' +
      cat +
      '. Cargando contenido de la base de datos...'
  )
}
</script>