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
        
        <span class="text-xs text-[#E67E22] bg-white/10 px-3 py-1 rounded-full font-mono uppercase tracking-widest hidden sm:block">
          Halcón Peregrino v2.6
        </span>
      </div>
    </header>

    <main class="container mx-auto px-6 py-10">
      
      <div class="flex justify-between items-center mb-12 border-b border-orange-200/50 pb-6">
        <div>
          <h1 class="text-3xl font-black uppercase tracking-tighter text-[#8B4513]">
            01. Tradiciones y Costumbres
          </h1>
          <p class="text-xs text-[#8B4513]/70 font-bold uppercase tracking-widest mt-1">
            La riqueza viva de San Pedro Huamelula
          </p>
        </div>
        <NuxtLink
          to="/cultura"
          class="px-5 py-2.5 bg-white border border-orange-200 text-[#8B4513] text-xs font-bold rounded-xl hover:bg-[#FDF8F1] transition-all shadow-sm"
        >
          Volver a Cultura
        </NuxtLink>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
        
        <div class="bg-white border border-orange-100 p-6 rounded-3xl shadow-sm hover:shadow-md transition-all flex flex-col">
          <div class="flex justify-between items-start mb-4">
            <span class="text-xl font-black text-[#8B4513]">01</span>
            <span class="text-2xl bg-[#FDF8F1] p-2 rounded-xl">🎉</span>
          </div>
          <h2 class="text-xl font-bold mb-2 text-[#5D2E17]">Tradiciones</h2>
          <p class="text-[#8B4513]/70 text-xs font-medium mb-6 flex-grow">
            Mitos, crónicas de origen, festividades del carnaval de la costa y celebraciones religiosas de la comunidad.
          </p>
          
          <div class="flex flex-col gap-2 mt-auto">
            <NuxtLink to="/lectura-tradiciones?id=1" class="w-full text-left px-4 py-3 border border-orange-100 rounded-xl text-xs font-bold text-[#8B4513] hover:border-orange-400 hover:bg-orange-50 transition-colors flex items-center gap-2">
              <span class="text-[#E67E22] text-xl leading-none">•</span> Antecedentes Históricos
            </NuxtLink>
            <NuxtLink to="/lectura-tradiciones?id=2" class="w-full text-left px-4 py-3 border border-orange-100 rounded-xl text-xs font-bold text-[#8B4513] hover:border-orange-400 hover:bg-orange-50 transition-colors flex items-center gap-2">
              <span class="text-[#E67E22] text-xl leading-none">•</span> Festividad del Carnaval
            </NuxtLink>
            <NuxtLink to="/lectura-tradiciones?id=3" class="w-full text-left px-4 py-3 border border-orange-100 rounded-xl text-xs font-bold text-[#8B4513] hover:border-orange-400 hover:bg-orange-50 transition-colors flex items-center gap-2">
              <span class="text-[#E67E22] text-xl leading-none">•</span> Semana Santa
            </NuxtLink>
          </div>
        </div>

        <div class="bg-white border border-orange-100 p-6 rounded-3xl shadow-sm hover:shadow-md transition-all flex flex-col">
          <div class="flex justify-between items-start mb-4">
            <span class="text-xl font-black text-[#8B4513]">02</span>
            <span class="text-2xl bg-[#FDF8F1] p-2 rounded-xl">🎭</span>
          </div>
          <h2 class="text-xl font-bold mb-2 text-[#5D2E17]">Danzas</h2>
          <p class="text-[#8B4513]/70 text-xs font-medium mb-6 flex-grow">
            Las representaciones teatrales, el simbolismo sagrado de los animales y los grupos de danza del pueblo.
          </p>
          
          <div class="flex flex-col gap-2 mt-auto">
            <NuxtLink to="/lectura-tradiciones?id=4" class="w-full text-left px-4 py-3 border border-orange-100 rounded-xl text-xs font-bold text-[#8B4513] hover:border-orange-400 hover:bg-orange-50 transition-colors flex items-center gap-2">
              <span class="text-[#E67E22] text-xl leading-none">•</span> La Lagarta
            </NuxtLink>
            <NuxtLink to="/lectura-tradiciones?id=5" class="w-full text-left px-4 py-3 border border-orange-100 rounded-xl text-xs font-bold text-[#8B4513] hover:border-orange-400 hover:bg-orange-50 transition-colors flex items-center gap-2">
              <span class="text-[#E67E22] text-xl leading-none">•</span> Las Mulatas (Lan Mulyatas)
            </NuxtLink>
            <NuxtLink to="/lectura-tradiciones?id=6" class="w-full text-left px-4 py-3 border border-orange-100 rounded-xl text-xs font-bold text-[#8B4513] hover:border-orange-400 hover:bg-orange-50 transition-colors flex items-center gap-2">
              <span class="text-[#E67E22] text-xl leading-none">•</span> Los Caballeros
            </NuxtLink>
          </div>
        </div>

        <div class="bg-white border border-orange-100 p-6 rounded-3xl shadow-sm hover:shadow-md transition-all flex flex-col opacity-70">
          <div class="flex justify-between items-start mb-4">
            <span class="text-xl font-black text-[#8B4513]">03</span>
            <span class="text-2xl bg-[#FDF8F1] p-2 rounded-xl">🍲</span>
          </div>
          <h2 class="text-xl font-bold mb-2 text-[#5D2E17]">Gastronomía</h2>
          <p class="text-[#8B4513]/70 text-xs font-medium mb-6 flex-grow">
            Sabores tradicionales, platillos rituales y recetas herencia de los antepasados chontales.
          </p>
          
          <div class="flex flex-col gap-2 mt-auto">
            <button class="w-full text-left px-4 py-3 border border-orange-50 rounded-xl text-xs font-bold text-[#8B4513]/50 flex items-center gap-2 cursor-not-allowed">
              <span class="text-gray-300 text-xl leading-none">•</span> Cocina Tradicional
            </button>
            <button class="w-full text-left px-4 py-3 border border-orange-50 rounded-xl text-xs font-bold text-[#8B4513]/50 flex items-center gap-2 cursor-not-allowed">
              <span class="text-gray-300 text-xl leading-none">•</span> Bebidas Rituales
            </button>
          </div>
        </div>

        <div class="bg-white border border-orange-100 p-6 rounded-3xl shadow-sm hover:shadow-md transition-all flex flex-col opacity-70">
          <div class="flex justify-between items-start mb-4">
            <span class="text-xl font-black text-[#8B4513]">04</span>
            <span class="text-2xl bg-[#FDF8F1] p-2 rounded-xl">👑</span>
          </div>
          <h2 class="text-xl font-bold mb-2 text-[#5D2E17]">Vestimenta</h2>
          <p class="text-[#8B4513]/70 text-xs font-medium mb-6 flex-grow">
            Indumentaria típica, trajes usados en representaciones dancísticas y textiles regionales.
          </p>
          
          <div class="flex flex-col gap-2 mt-auto">
            <button class="w-full text-left px-4 py-3 border border-orange-50 rounded-xl text-xs font-bold text-[#8B4513]/50 flex items-center gap-2 cursor-not-allowed">
              <span class="text-gray-300 text-xl leading-none">•</span> Trajes de Gala
            </button>
            <button class="w-full text-left px-4 py-3 border border-orange-50 rounded-xl text-xs font-bold text-[#8B4513]/50 flex items-center gap-2 cursor-not-allowed">
              <span class="text-gray-300 text-xl leading-none">•</span> Indumentaria de Danza
            </button>
          </div>
        </div>

      </div>
    </main>
  </div>
</template>