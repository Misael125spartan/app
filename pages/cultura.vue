<template>
  <div class="min-h-screen bg-[#FDF8F1] text-[#5D2E17] font-sans pb-10">
    <header class="border-b border-orange-200/50 bg-[#8B4513] sticky top-0 z-50 shadow-md">
      <div class="container mx-auto px-6 py-4 flex justify-between items-center">
        <div class="flex items-center gap-3">
          <div class="h-10 w-10 bg-[#E67E22] rounded-xl flex items-center justify-center font-black text-white shadow-sm">H</div>
          <div>
            <span class="text-xl font-black uppercase tracking-tight text-white">Huamelollan</span>
            <p class="text-[9px] text-orange-200/70 font-mono tracking-widest">ITGAM - TECNM</p>
          </div>
        </div>
        <nav class="hidden md:flex items-center gap-8 text-sm font-semibold text-orange-100/80">
          <NuxtLink to="/cultura" class="text-white transition-colors duration-200 border-b-2 border-[#E67E22] pb-1">1. Cultura</NuxtLink>
          <NuxtLink to="/historias" class="hover:text-white transition-colors duration-200">2. Historias</NuxtLink>
          <NuxtLink to="/aprender" class="hover:text-white transition-colors duration-200">3. Aprender</NuxtLink>
          <NuxtLink to="/perfil" class="hover:text-white transition-colors duration-200">4. Perfil</NuxtLink>
        </nav>
      </div>
    </header>

    <main class="container mx-auto px-6 py-10">
      <div class="flex justify-between items-center mb-12 border-b border-orange-200/50 pb-6">
        <div>
          <h1 class="text-3xl font-black uppercase tracking-tighter text-[#8B4513]">01. Cultura y Tradiciones</h1>
        </div>
        <NuxtLink to="/" class="px-5 py-2.5 bg-white border border-orange-200 text-[#8B4513] text-xs font-bold rounded-xl">Volver</NuxtLink>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
        
        <div class="bg-white p-6 rounded-3xl border border-orange-100 shadow-sm flex flex-col">
          <h2 class="text-xl font-bold mb-4">Tradiciones</h2>
          <div class="flex flex-col gap-2">
            <NuxtLink to="/lectura-tradiciones?id=1" class="text-xs font-bold p-3 bg-orange-50 rounded-lg hover:bg-orange-100">• Antecedentes Históricos</NuxtLink>
            <NuxtLink to="/lectura-tradiciones?id=2" class="text-xs font-bold p-3 bg-orange-50 rounded-lg hover:bg-orange-100">• Festividad del Carnaval</NuxtLink>
            <NuxtLink to="/lectura-tradiciones?id=3" class="text-xs font-bold p-3 bg-orange-50 rounded-lg hover:bg-orange-100">• Semana Santa</NuxtLink>
          </div>
        </div>

        <div class="bg-white p-6 rounded-3xl border border-orange-100 shadow-sm flex flex-col">
          <h2 class="text-xl font-bold mb-4">Danzas</h2>
          <div class="flex flex-col gap-2">
            <NuxtLink to="/lectura-tradiciones?id=4" class="text-xs font-bold p-3 bg-orange-50 rounded-lg hover:bg-orange-100">• La Lagarta</NuxtLink>
            <NuxtLink to="/lectura-tradiciones?id=5" class="text-xs font-bold p-3 bg-orange-50 rounded-lg hover:bg-orange-100">• Las Mulatas</NuxtLink>
            <NuxtLink to="/lectura-tradiciones?id=6" class="text-xs font-bold p-3 bg-orange-50 rounded-lg hover:bg-orange-100">• Los Caballeros</NuxtLink>
          </div>
        </div>

        <div class="bg-white p-6 rounded-3xl border border-orange-100 shadow-sm flex flex-col">
          <h2 class="text-xl font-bold mb-4">Gastronomía</h2>
          <p class="text-xs text-gray-500">Próximamente...</p>
        </div>

        <div class="bg-white p-6 rounded-3xl border border-orange-100 shadow-sm flex flex-col">
          <h2 class="text-xl font-bold mb-4">Vestimenta</h2>
          <p class="text-xs text-gray-500">Próximamente...</p>
        </div>
      </div>
    </main>
  </div>
</template>