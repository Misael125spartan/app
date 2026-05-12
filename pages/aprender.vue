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
          <NuxtLink to="/aprender" class="text-white transition-colors duration-200 border-b-2 border-[#E67E22] pb-1">3. Aprender</NuxtLink>
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
            03. Aprender
          </h1>
          <p class="text-xs text-[#8B4513]/70 font-bold uppercase tracking-widest mt-1">
            Selección de nivel de aprendizaje
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
        
        <div class="bg-white border border-orange-100 p-6 rounded-3xl group hover:border-green-400 transition-all shadow-md hover:shadow-xl flex flex-col">
          <div class="flex justify-between items-start mb-2">
            <span class="px-3 py-1 bg-green-100 text-green-700 text-[10px] font-bold tracking-widest rounded-lg uppercase">
              Básico
            </span>
            <span class="text-3xl bg-[#FDF8F1] p-2 rounded-xl">🌱</span>
          </div>
          <h2 class="text-xl font-bold mt-2 mb-2 text-[#5D2E17]">Unidad 1</h2>
          <p class="text-[#8B4513]/70 text-xs font-medium leading-relaxed mb-6 flex-grow">
            Contenido introductorio sobre tradiciones locales y comprensión básica
            del entorno.
          </p>
          <button
            @click="irAUnidad('Básico')"
            class="w-full py-3 bg-green-50 text-green-600 border border-green-100 text-xs font-bold rounded-xl hover:bg-green-600 hover:text-white transition-colors"
          >
            Comenzar Unidad
          </button>
        </div>

        <div class="bg-white border border-orange-100 p-6 rounded-3xl group hover:border-amber-400 transition-all shadow-md hover:shadow-xl flex flex-col">
          <div class="flex justify-between items-start mb-2">
            <span class="px-3 py-1 bg-amber-100 text-amber-700 text-[10px] font-bold tracking-widest rounded-lg uppercase">
              Intermedio
            </span>
            <span class="text-3xl bg-[#FDF8F1] p-2 rounded-xl">🪴</span>
          </div>
          <h2 class="text-xl font-bold mt-2 mb-2 text-[#5D2E17]">Unidad 2</h2>
          <p class="text-[#8B4513]/70 text-xs font-medium leading-relaxed mb-6 flex-grow">
            Lectura de cuentos populares y análisis de leyendas de los
            antepasados.
          </p>
          <button
            @click="irAUnidad('Intermedio')"
            class="w-full py-3 bg-amber-50 text-amber-600 border border-amber-100 text-xs font-bold rounded-xl hover:bg-amber-500 hover:text-white transition-colors"
          >
            Comenzar Unidad
          </button>
        </div>

        <div class="bg-white border border-orange-100 p-6 rounded-3xl group hover:border-[#E67E22] transition-all shadow-md hover:shadow-xl flex flex-col">
          <div class="flex justify-between items-start mb-2">
            <span class="px-3 py-1 bg-orange-100 text-[#E67E22] text-[10px] font-bold tracking-widest rounded-lg uppercase">
              Avanzado
            </span>
            <span class="text-3xl bg-[#FDF8F1] p-2 rounded-xl">🌳</span>
          </div>
          <h2 class="text-xl font-bold mt-2 mb-2 text-[#5D2E17]">Unidad 3</h2>
          <p class="text-[#8B4513]/70 text-xs font-medium leading-relaxed mb-6 flex-grow">
            Evaluación integral del módulo, resolución de cuestionario y registro
            de notas.
          </p>
          <button
            @click="irAEvaluacion()"
            class="w-full py-3 bg-orange-50 text-[#E67E22] border border-orange-100 text-xs font-bold rounded-xl hover:bg-[#E67E22] hover:text-white transition-colors"
          >
            Ir a Evaluación
          </button>
        </div>

      </div>
    </main>
  </div>
</template>

<script setup>
const irAUnidad = nivel => {
  alert('Unidad de aprendizaje nivel: ' + nivel + ' seleccionada.')
}
const irAEvaluacion = () => {
  alert('Abriendo evaluación del sistema Huamelollan...')
}
</script>