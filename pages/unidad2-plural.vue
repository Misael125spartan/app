<template>
  <div class="min-h-screen bg-[#FDF8F1] text-[#5D2E17] font-sans pb-10">
    <main class="container mx-auto px-6 py-10">
      
      <div class="flex justify-between items-center mb-8 border-b border-orange-200/50 pb-6">
        <div>
          <h1 class="text-3xl font-black tracking-tight">UNIDAD 2: PLURALES</h1>
          <p class="text-sm text-[#8B4513]/70 font-bold uppercase tracking-widest mt-1">
            Gramática del chontal bajo
          </p>
        </div>
        <NuxtLink 
          to="/aprender" 
          class="px-5 py-2.5 bg-white border border-orange-200 text-[#8B4513] text-xs font-bold rounded-lg hover:border-[#8B4513] transition-all"
        >
          Volver a Niveles
        </NuxtLink>
      </div>

      <div v-if="faseActual < 5" class="max-w-3xl mx-auto mb-6 flex gap-2">
        <div class="h-2 flex-1 rounded-full transition-all duration-500" :class="faseActual >= 1 ? 'bg-amber-500' : 'bg-orange-200'"></div>
        <div class="h-2 flex-1 rounded-full transition-all duration-500" :class="faseActual >= 2 ? 'bg-amber-500' : 'bg-orange-200'"></div>
        <div class="h-2 flex-1 rounded-full transition-all duration-500" :class="faseActual >= 3 ? 'bg-amber-500' : 'bg-orange-200'"></div>
        <div class="h-2 flex-1 rounded-full transition-all duration-500" :class="faseActual >= 4 ? 'bg-amber-500' : 'bg-orange-200'"></div>
      </div>

      <div class="max-w-3xl mx-auto bg-white p-8 rounded-3xl border border-orange-100 shadow-md min-h-[450px]">
        
        <div v-if="faseActual === 1" class="animacion-entrada">
          <h2 class="text-2xl font-black mb-4 text-[#8B4513]">El plural en lengua chontal bajo</h2>
          <p class="mb-6 text-sm">El plural indica que hay más de una persona, animal o cosa. No siempre cambia la palabra principal; muchas veces se agregan palabras de apoyo.</p>
          
          <div class="space-y-4 mb-8 text-sm">
            <div class="bg-amber-50 p-4 rounded-xl border border-amber-100">
              <h3 class="font-bold mb-2">1. Uso de "ka"</h3>
              <p class="mb-2">Se usa para indicar plural en algunas personas o grupos.</p>
              <ul class="list-disc pl-5 opacity-80 font-mono">
                <li>Ts'an (hijo) ➔ <span class="font-bold">Ka ts'an</span> (hijos)</li>
                <li>Ñaaju (hermano) ➔ <span class="font-bold">Ka ñaaju</span> (hermanos)</li>
              </ul>
            </div>
            
            <div class="bg-amber-50 p-4 rounded-xl border border-amber-100">
              <h3 class="font-bold mb-2">2. Uso de "manyi"</h3>
              <p class="mb-2">Significa "muchos" o "varios". Expresa una cantidad mayor.</p>
              <ul class="list-disc pl-5 opacity-80 font-mono">
                <li>Ma'yo' (mamá) ➔ <span class="font-bold">Manyi ma'yo'</span> (muchas mamás)</li>
                <li>Ñaaju (hermano) ➔ <span class="font-bold">Manyi ñaaju</span> (muchos hermanos)</li>
              </ul>
            </div>

            <div class="bg-amber-50 p-4 rounded-xl border border-amber-100">
              <h3 class="font-bold mb-2">3. El contexto</h3>
              <p>En algunas oraciones, el plural se entiende por el contexto. Ej: <span class="font-bold font-mono">Ka'nu xanuc'</span> (familia) puede entenderse como "varias familias" según la oración.</p>
            </div>
          </div>

          <button @click="faseActual = 2" class="w-full py-4 bg-amber-500 text-white font-bold rounded-xl hover:bg-amber-600 transition-colors">
            Comenzar Actividades
          </button>
        </div>

        <div v-else-if="faseActual === 2" class="animacion-entrada flex flex-col items-center justify-center h-full">
          <div class="w-full flex justify-between items-center mb-8">
            <span class="text-xs font-bold uppercase tracking-widest text-[#8B4513]/70">Actividad 1: Completa</span>
            <span class="text-sm font-mono bg-[#FDF8F1] px-3 py-1 rounded-md border border-orange-200">{{ indiceCompletar + 1 }} / {{ preguntasCompletar.length }}</span>
          </div>

          <p class="text-center mb-2 text-sm uppercase tracking-widest font-bold">Completa con "ka" o "manyi"</p>
          <p class="text-lg mb-8 text-[#8B4513] text-center">Para decir: <span class="font-bold">"{{ preguntaCompletarActual.traduccion }}"</span></p>
          
          <div class="flex items-center gap-4 mb-10 text-3xl font-black">
            <span class="border-b-4 border-amber-500 px-4 min-w-[120px] text-center" :class="mostrarFeedback ? (respuestaSeleccionada === preguntaCompletarActual.respuestaCorrecta ? 'text-green-600 border-green-500' : 'text-red-500 border-red-500') : 'text-gray-300'">
              {{ respuestaSeleccionada || '_____' }}
            </span>
            <span class="text-[#5D2E17]">{{ preguntaCompletarActual.palabra }}</span>
          </div>

          <div class="grid grid-cols-2 gap-4 w-full max-w-sm">
            <button
              v-for="(opcion, index) in preguntaCompletarActual.opciones"
              :key="index"
              @click="verificarCompletar(opcion)"
              :disabled="mostrarFeedback"
              class="px-5 py-4 font-bold rounded-xl border-2 transition-all text-xl bg-white border-orange-100 text-[#8B4513] hover:border-amber-400 hover:bg-amber-50"
            >
              {{ opcion }}
            </button>
          </div>
        </div>

        <div v-else-if="faseActual === 3" class="animacion-entrada flex flex-col items-center justify-center h-full">
          <div class="w-full flex justify-between items-center mb-8">
            <span class="text-xs font-bold uppercase tracking-widest text-[#8B4513]/70">Actividad 2: Identifica</span>
            <span class="text-sm font-mono bg-[#FDF8F1] px-3 py-1 rounded-md border border-orange-200">1 / 1</span>
          </div>
          
          <h2 class="text-2xl font-black mb-8 text-center text-[#8B4513]">{{ preguntaSeleccionar.pregunta }}</h2>

          <div class="grid grid-cols-1 gap-4 w-full max-w-md">
            <button
              v-for="(opcion, index) in preguntaSeleccionar.opciones"
              :key="index"
              @click="verificarSeleccionar(opcion)"
              :disabled="mostrarFeedback"
              :class="['px-5 py-4 font-bold rounded-xl border-2 transition-all text-lg', obtenerClaseBoton(opcion, preguntaSeleccionar.respuestaCorrecta)]"
            >
              {{ opcion }}
            </button>
          </div>
        </div>

        <div v-else-if="faseActual === 4" class="animacion-entrada flex flex-col items-center justify-center h-full">
          <div class="w-full flex justify-between items-center mb-6">
            <span class="text-xs font-bold uppercase tracking-widest text-[#8B4513]/70">Actividad 3: Clasifica</span>
            <span class="text-sm font-mono bg-[#FDF8F1] px-3 py-1 rounded-md border border-orange-200">{{ indiceClasificar + 1 }} / {{ preguntasClasificar.length }}</span>
          </div>

          <h3 class="text-xl font-bold mb-8 text-center">¿Esta palabra está en singular o plural?</h3>
          
          <div class="text-5xl font-black text-center text-[#8B4513] bg-amber-50 w-full py-10 rounded-2xl border-2 border-amber-200 mb-8">
            {{ preguntaClasificarActual.palabra }}
          </div>

          <div class="grid grid-cols-2 gap-4 w-full max-w-md">
            <button
              v-for="(opcion, index) in ['Singular', 'Plural']"
              :key="index"
              @click="verificarClasificar(opcion)"
              :disabled="mostrarFeedback"
              :class="['px-5 py-4 font-bold rounded-xl border-2 transition-all text-xl', obtenerClaseBoton(opcion, preguntaClasificarActual.respuestaCorrecta)]"
            >
              {{ opcion }}
            </button>
          </div>
        </div>

        <div v-else class="text-center py-10 animacion-entrada">
          <div class="text-6xl mb-4">⭐</div>
          <h2 class="text-3xl font-black mb-4">¡Módulo de Plurales Completado!</h2>
          <p class="text-xl mb-2">Actividad 1 (Completar): <span class="font-bold">{{ puntajeCompletar }} / 3</span></p>
          <p class="text-xl mb-2">Actividad 2 (Identificar): <span class="font-bold text-green-600">Completado</span></p>
          <p class="text-xl mb-8">Actividad 3 (Clasificar): <span class="font-bold">{{ puntajeClasificar }} / 4</span></p>
          
          <div class="flex justify-center gap-4">
            <button @click="reiniciarTodo" class="px-6 py-3 bg-white border-2 border-amber-200 text-amber-700 font-bold rounded-xl hover:bg-amber-50 transition-colors">
              Volver a repasar
            </button>
            <NuxtLink to="/aprender" class="px-6 py-3 bg-amber-500 text-white font-bold rounded-xl hover:bg-amber-600 transition-colors">
              Finalizar
            </NuxtLink>
          </div>
        </div>

      </div>
    </main>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const faseActual = ref(1) 
const mostrarFeedback = ref(false)
const respuestaSeleccionada = ref(null)

// Utilidad visual para los botones
const obtenerClaseBoton = (opcion, correcta) => {
  if (!mostrarFeedback.value) return 'bg-white border-orange-100 text-[#8B4513] hover:border-amber-400 hover:bg-amber-50'
  if (opcion === correcta) return 'bg-green-100 border-green-500 text-green-700'
  if (opcion === respuestaSeleccionada.value && opcion !== correcta) return 'bg-red-100 border-red-500 text-red-700'
  return 'bg-gray-50 border-gray-200 text-gray-400 opacity-50'
}

// ==========================================
// FASE 2: COMPLETAR
// ==========================================
const preguntasCompletar = ref([
  { palabra: "ts'an", traduccion: "hijos", opciones: ['Ka', 'Manyi'], respuestaCorrecta: 'Ka' },
  { palabra: "ñaaju", traduccion: "muchos hermanos", opciones: ['Ka', 'Manyi'], respuestaCorrecta: 'Manyi' },
  { palabra: "ma'yo'", traduccion: "muchas mamás", opciones: ['Ka', 'Manyi'], respuestaCorrecta: 'Manyi' }
])
const indiceCompletar = ref(0)
const puntajeCompletar = ref(0)
const preguntaCompletarActual = computed(() => preguntasCompletar.value[indiceCompletar.value])

const verificarCompletar = (opcion) => {
  if (mostrarFeedback.value) return 
  respuestaSeleccionada.value = opcion
  mostrarFeedback.value = true

  if (opcion === preguntaCompletarActual.value.respuestaCorrecta) puntajeCompletar.value++

  setTimeout(() => {
    if (indiceCompletar.value < preguntasCompletar.value.length - 1) {
      indiceCompletar.value++
      mostrarFeedback.value = false
      respuestaSeleccionada.value = null
    } else {
      mostrarFeedback.value = false
      respuestaSeleccionada.value = null
      faseActual.value = 3 
    }
  }, 1500)
}

// ==========================================
// FASE 3: SELECCIONAR
// ==========================================
const preguntaSeleccionar = {
  pregunta: "Selecciona cuál palabra está en plural",
  opciones: ["Ts'an", "Ka ts'an", "Ña'yo'"],
  respuestaCorrecta: "Ka ts'an"
}

const verificarSeleccionar = (opcion) => {
  if (mostrarFeedback.value) return 
  respuestaSeleccionada.value = opcion
  mostrarFeedback.value = true

  setTimeout(() => {
    mostrarFeedback.value = false
    respuestaSeleccionada.value = null
    faseActual.value = 4 
  }, 1500)
}

// ==========================================
// FASE 4: CLASIFICAR (Singular o Plural)
// ==========================================
const preguntasClasificar = ref([
  { palabra: "Ts'an", respuestaCorrecta: "Singular" },
  { palabra: "Ka ts'an", respuestaCorrecta: "Plural" },
  { palabra: "Manyi ñaaju", respuestaCorrecta: "Plural" },
  { palabra: "Ma'yo'", respuestaCorrecta: "Singular" }
])
const indiceClasificar = ref(0)
const puntajeClasificar = ref(0)
const preguntaClasificarActual = computed(() => preguntasClasificar.value[indiceClasificar.value])

const verificarClasificar = (opcion) => {
  if (mostrarFeedback.value) return 
  respuestaSeleccionada.value = opcion
  mostrarFeedback.value = true

  if (opcion === preguntaClasificarActual.value.respuestaCorrecta) puntajeClasificar.value++

  setTimeout(() => {
    if (indiceClasificar.value < preguntasClasificar.value.length - 1) {
      indiceClasificar.value++
      mostrarFeedback.value = false
      respuestaSeleccionada.value = null
    } else {
      faseActual.value = 5 // Resultados
    }
  }, 1500)
}

// ==========================================
// REINICIO
// ==========================================
const reiniciarTodo = () => {
  faseActual.value = 1
  mostrarFeedback.value = false
  respuestaSeleccionada.value = null
  
  indiceCompletar.value = 0
  puntajeCompletar.value = 0
  
  indiceClasificar.value = 0
  puntajeClasificar.value = 0
}
</script>

<style scoped>
.animacion-entrada {
  animation: fadeIn 0.5s ease-out forwards;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}
</style>