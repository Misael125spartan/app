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
          <h1 class="text-3xl font-black uppercase tracking-tighter text-[#8B4513]">
            02. Historias y Leyendas
          </h1>
          <p class="text-xs text-[#8B4513]/70 font-bold uppercase tracking-widest mt-1">
            Conoce la memoria ancestral del pueblo
          </p>
        </div>
        <NuxtLink
          to="/"
          class="px-5 py-2.5 bg-white border border-orange-200 text-[#8B4513] text-xs font-bold rounded-xl hover:bg-[#FDF8F1] transition-all shadow-sm"
        >
          Volver al Inicio
        </NuxtLink>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
        
        <div class="bg-white border border-orange-100 p-8 rounded-3xl shadow-sm hover:shadow-md transition-all flex flex-col">
          <div class="flex justify-between items-start mb-6">
            <span class="text-2xl font-black text-[#8B4513]">01</span>
            <span class="text-3xl bg-[#FDF8F1] p-2 rounded-xl">🌿</span>
          </div>
          <h2 class="text-2xl font-bold mb-2 text-[#5D2E17]">Leyendas</h2>
          <p class="text-[#8B4513]/70 text-sm font-medium mb-6">
            Narrativas sobre el origen, tradiciones sagradas y sucesos memorables de San Pedro Huamelula.
          </p>
          
          <div class="flex flex-col gap-3 mt-auto">
            <NuxtLink to="/leyendas?id=1" class="w-full text-left px-5 py-3.5 border border-orange-100 rounded-xl text-sm font-bold text-[#8B4513] hover:border-orange-400 hover:bg-orange-50 transition-colors flex items-center gap-3">
              <span class="text-[#E67E22] text-2xl leading-none mb-1">•</span> El Boquerón (Cocógua)
            </NuxtLink>
            <NuxtLink to="/leyendas?id=2" class="w-full text-left px-5 py-3.5 border border-orange-100 rounded-xl text-sm font-bold text-[#8B4513] hover:border-orange-400 hover:bg-orange-50 transition-colors flex items-center gap-3">
              <span class="text-[#E67E22] text-2xl leading-none mb-1">•</span> La Leyenda del Amigo
            </NuxtLink>
            <NuxtLink to="/leyendas?id=3" class="w-full text-left px-5 py-3.5 border border-orange-100 rounded-xl text-sm font-bold text-[#8B4513] hover:border-orange-400 hover:bg-orange-50 transition-colors flex items-center gap-3">
              <span class="text-[#E67E22] text-2xl leading-none mb-1">•</span> La Mesa
            </NuxtLink>
            <NuxtLink to="/leyendas?id=4" class="w-full text-left px-5 py-3.5 border border-orange-100 rounded-xl text-sm font-bold text-[#8B4513] hover:border-orange-400 hover:bg-orange-50 transition-colors flex items-center gap-3">
              <span class="text-[#E67E22] text-2xl leading-none mb-1">•</span> Soy San Pedro Huamelula
            </NuxtLink>
          </div>
        </div>

        <div class="bg-white border border-orange-100 p-8 rounded-3xl shadow-sm hover:shadow-md transition-all flex flex-col">
          <div class="flex justify-between items-start mb-6">
            <span class="text-2xl font-black text-[#8B4513]">02</span>
            <span class="text-3xl bg-[#FDF8F1] p-2 rounded-xl">📚</span>
          </div>
          <h2 class="text-2xl font-bold mb-2 text-[#5D2E17]">Cuentos</h2>
          <p class="text-[#8B4513]/70 text-sm font-medium mb-8">
            Relatos de transmisión oral, hechos históricos y moralejas de la cultura indígena.
          </p>
          
          <div class="flex flex-col gap-3 mt-auto">
            <NuxtLink to="/cuentos?id=6" class="w-full text-left px-5 py-3.5 border border-orange-100 rounded-xl text-sm font-bold text-[#8B4513] hover:border-orange-400 hover:bg-orange-50 transition-colors flex items-center gap-3">
              <span class="text-[#E67E22] text-2xl leading-none mb-1">•</span> La Cruz Parlante
            </NuxtLink>
            <button @click="alertaDesarrollo" class="w-full text-left px-5 py-4 border border-orange-50 rounded-xl text-xs font-bold text-[#8B4513]/40 flex items-center gap-3 cursor-not-allowed">
              <span class="text-gray-300 text-2xl leading-none mb-1">•</span> Próximamente...
            </button>
          </div>
        </div>

        <div class="bg-white border border-orange-100 p-8 rounded-3xl shadow-sm hover:shadow-md transition-all flex flex-col">
          <div class="flex justify-between items-start mb-6">
            <span class="text-2xl font-black text-[#8B4513]">03</span>
            <span class="text-3xl bg-[#FDF8F1] p-2 rounded-xl">📜</span>
          </div>
          <h2 class="text-2xl font-bold mb-2 text-[#5D2E17]">Poemas</h2>
          <p class="text-[#8B4513]/70 text-sm font-medium mb-8">
            Expresión lírica, metáforas y versos bilingües de la herencia chontal.
          </p>
          
          <div class="flex flex-col gap-3 mt-auto">
            <NuxtLink to="/poemas?id=5" class="w-full text-left px-5 py-3.5 border border-orange-100 rounded-xl text-sm font-bold text-[#8B4513] hover:border-orange-400 hover:bg-orange-50 transition-colors flex items-center gap-3">
              <span class="text-[#E67E22] text-2xl leading-none mb-1">•</span> Encima de la Roca / El Mirador
            </NuxtLink>
            <button @click="alertaDesarrollo" class="w-full text-left px-5 py-4 border border-orange-50 rounded-xl text-xs font-bold text-[#8B4513]/40 flex items-center gap-3 cursor-not-allowed">
              <span class="text-gray-300 text-2xl leading-none mb-1">•</span> Próximamente...
            </button>
          </div>
        </div>

      </div>
    </main>
  </div>
</template>

<script setup>
const alertaDesarrollo = () => {
  alert('¡Pronto agregaremos más material a esta sección!');
}
</script>