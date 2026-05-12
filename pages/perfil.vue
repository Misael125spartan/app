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
          <NuxtLink to="/historias" class="hover:text-white transition-colors duration-200">2. Historias</NuxtLink>
          <NuxtLink to="/aprender" class="hover:text-white transition-colors duration-200">3. Aprender</NuxtLink>
          <NuxtLink to="/perfil" class="text-white transition-colors duration-200 border-b-2 border-[#E67E22] pb-1">4. Perfil</NuxtLink>
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
            04. Perfil - Halcón Peregrino
          </h1>
          <p class="text-xs text-[#8B4513]/70 font-bold uppercase tracking-widest mt-1">
            Progreso y logros acumulados
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
        
        <div class="bg-white p-8 rounded-3xl border border-orange-100 shadow-md">
          <div class="text-xs text-[#8B4513]/70 font-bold uppercase tracking-widest mb-1">
            Puntaje Total
          </div>
          <div class="text-4xl font-black text-[#5D2E17] mb-8 flex items-baseline gap-2">
            {{ userStore.points }} <span class="text-xl text-green-600">XP</span>
          </div>

          <div class="text-xs text-[#8B4513]/70 font-bold uppercase tracking-widest mb-1">
            Nivel Actual
          </div>
          <div class="text-3xl font-black text-[#E67E22]">
            0{{ userStore.currentLevel }}
          </div>
        </div>

        <div class="bg-white p-8 rounded-3xl border border-orange-100 shadow-md">
          <h3 class="text-sm font-bold mb-5 uppercase text-[#5D2E17]">Logros e Insignias</h3>
          <ul class="space-y-3">
            <li
              v-for="logro in userStore.achievements"
              :key="logro"
              class="px-4 py-3 bg-[#FDF8F1] text-xs font-bold rounded-xl text-[#E67E22] border border-orange-100 flex items-center gap-3 shadow-sm"
            >
              <span class="text-base">🏆</span> {{ logro }}
            </li>
          </ul>
        </div>

        <div class="bg-white p-8 rounded-3xl border border-orange-100 shadow-md">
          <h3 class="text-sm font-bold mb-5 uppercase text-[#5D2E17]">Módulos Completados</h3>
          <ul class="space-y-3">
            <li
              v-for="unidad in userStore.completedUnits"
              :key="unidad"
              class="px-4 py-3 bg-[#FDF8F1] text-xs font-bold rounded-xl text-blue-700 border border-blue-100 flex items-center gap-3 shadow-sm"
            >
              <span class="text-blue-500 font-black text-sm">✓</span> {{ unidad }}
            </li>
          </ul>
        </div>
        
      </div>
    </main>
  </div>
</template>

<script setup>
import { useUserStore } from '~/stores/user'
const userStore = useUserStore()
</script>