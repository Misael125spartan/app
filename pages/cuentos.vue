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
        <NuxtLink to="/historias" class="px-5 py-2 bg-[#FDF8F1] text-[#8B4513] text-xs font-bold rounded-xl hover:bg-orange-100 transition-colors">
          Volver a Historias
        </NuxtLink>
      </div>
    </header>

    <main class="container mx-auto px-6 py-10">
      <div class="mb-8 border-b border-orange-200/50 pb-6">
        <h1 class="text-3xl font-black uppercase tracking-tighter text-[#8B4513]">02. Sección de Cuentos</h1>
        <p class="text-xs text-[#8B4513]/70 font-bold uppercase tracking-widest mt-1">Relatos orales y crónicas históricas</p>
      </div>

      <div class="flex flex-col lg:flex-row gap-8">
        <div class="lg:w-1/3 flex flex-col gap-4">
          <button 
            v-for="(obra, index) in biblioteca" 
            :key="index"
            @click="seleccionarObra(obra)"
            class="text-left p-5 rounded-2xl border-2 transition-all duration-300 relative overflow-hidden group shadow-sm"
            :class="obraSeleccionada.id === obra.id ? 'bg-[#8B4513] border-[#8B4513] text-white shadow-lg' : 'bg-white border-orange-100 text-[#5D2E17] hover:border-orange-300'"
          >
            <span class="text-[10px] font-bold uppercase tracking-widest opacity-70 mb-1 block">{{ obra.tipo }}</span>
            <h3 class="text-lg font-black mb-1" :class="obraSeleccionada.id === obra.id ? 'text-white' : 'text-[#8B4513]'">{{ obra.titulo }}</h3>
            <p class="text-xs opacity-80">Por: {{ obra.autor }}</p>
          </button>
        </div>

        <div class="lg:w-2/3 bg-white p-8 md:p-12 rounded-3xl border border-orange-100 shadow-xl min-h-[600px]">
          <div class="mb-10 text-center border-b border-orange-100 pb-8">
            <span class="inline-block px-4 py-1 bg-orange-50 text-[#E67E22] text-xs font-bold tracking-widest rounded-full uppercase mb-4">{{ obraSeleccionada.tipo }}</span>
            <h2 class="text-3xl font-black text-[#8B4513] mb-4">{{ obraSeleccionada.titulo }}</h2>
            <p class="text-[#5D2E17] font-bold italic text-sm">Autor: {{ obraSeleccionada.autor }}</p>
          </div>

          <div class="prose prose-orange max-w-none text-lg text-[#5D2E17]/90 leading-relaxed font-serif">
            <p v-for="(parrafo, i) in obraSeleccionada.contenido" :key="i" class="mb-6 indent-8 text-justify">
              {{ parrafo }}
            </p>
          </div>
          <div class="mt-12 pt-8 border-t border-orange-100 text-center text-sm opacity-50 font-mono">Fin de la lectura.</div>
        </div>
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const biblioteca = ref([
  {
    id: 6,
    titulo: 'La Guerra de Castas y la Cruz Parlante',
    tipo: 'Cuento Histórico',
    autor: 'Ma. Guadalupe Flores Rodríguez',
    contenido: [
      "En la primera mitad del siglo XIX, los mayas de la costa oriental de Yucatán luchaban por su libertad y el derecho a vivir de acuerdo con sus usos y costumbres. Este reclamo incluía el derecho ancestral a poseer la tierra y posteriormente se levantaron en armas en 1847, cuando el líder indígena Cecilio Chí tomó la población de Tepich en el actual estado de Quintana Roo.",
      "Esta es la memoria histórica y el origen de la 'Cruz Parlante', una manifestation que sirvió como un pilar fundamental de resistencia espiritual y social, uniendo los esfuerzos del pueblo para defender su identidad y sus tierras comunales frente a las injusticias de la época."
    ]
  }
])

const obraSeleccionada = ref(biblioteca.value[0])
const seleccionarObra = (obra) => { obraSeleccionada.value = obra }

onMounted(() => {
  const queryId = Number(route.query.id)
  if (queryId) {
    const seleccionada = biblioteca.value.find(item => item.id === queryId)
    if (seleccionada) obraSeleccionada.value = seleccionada
  }
})
</script>

<style scoped>
.indent-8 { text-indent: 2rem; }
</style>