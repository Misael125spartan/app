<template>
  <div class="min-h-screen bg-[#FDF8F1] text-[#5D2E17] font-sans pb-10">
    <main class="container mx-auto px-6 py-10">
      
      <div class="flex justify-between items-center mb-8 border-b border-orange-200/50 pb-6">
        <div>
          <h1 class="text-3xl font-black tracking-tight">UNIDAD 1: NÚMEROS</h1>
          <p class="text-sm text-[#8B4513]/70 font-bold uppercase tracking-widest mt-1">
            Sistema de numeración en chontal
          </p>
        </div>
        <NuxtLink 
          to="/aprender" 
          class="px-5 py-2.5 bg-white border border-orange-200 text-[#8B4513] text-xs font-bold rounded-lg hover:border-[#8B4513] transition-all"
        >
          Volver a Niveles
        </NuxtLink>
      </div>

      <div v-if="faseActual < 4" class="max-w-3xl mx-auto mb-6 flex gap-2">
        <div class="h-2 flex-1 rounded-full transition-all duration-500" :class="faseActual >= 1 ? 'bg-[#8B4513]' : 'bg-orange-200'"></div>
        <div class="h-2 flex-1 rounded-full transition-all duration-500" :class="faseActual >= 2 ? 'bg-[#8B4513]' : 'bg-orange-200'"></div>
        <div class="h-2 flex-1 rounded-full transition-all duration-500" :class="faseActual >= 3 ? 'bg-[#8B4513]' : 'bg-orange-200'"></div>
      </div>

      <div class="max-w-3xl mx-auto bg-white p-8 rounded-3xl border border-orange-100 shadow-md min-h-[450px]">
        
        <div v-if="faseActual === 1" class="animacion-entrada">
          <h2 class="text-2xl font-black mb-4 text-[#8B4513]">Reglas de numeración</h2>
          
          <div class="space-y-4 mb-8 text-sm">
            <div class="bg-orange-50 p-4 rounded-xl border border-orange-100">
              <h3 class="font-bold mb-2">1. Números del 1 al 9:</h3>
              <p>Tienen nombres específicos: ñulyi (1), ukwe' (2), fane' (3), malpu' (4), mague' (5), k'anchux (6), kote' (7), malfa' (8) y penla' (9).</p>
            </div>
            
            <div class="bg-orange-50 p-4 rounded-xl border border-orange-100">
              <h3 class="font-bold mb-2">2. Sistema Vigesimal (Base 20):</h3>
              <p>Las decenas se forman con base 20. Ejemplo: mbama' (10), ñuxans (20), fane' jmbama' (30 = 3*10), ukwej ñuxans' (40 = 2*20).</p>
            </div>

            <div class="bg-orange-50 p-4 rounded-xl border border-orange-100 flex justify-between items-center">
              <div>
                <h3 class="font-bold mb-1">3. El número Cien:</h3>
                <p>La palabra para cien es <span class="font-bold text-[#8B4513]">maxñu</span>.</p>
              </div>
            </div>
          </div>

          <button @click="faseActual = 2" class="w-full py-4 bg-[#8B4513] text-white font-bold rounded-xl hover:bg-[#5D2E17] transition-colors">
            Comenzar Actividades
          </button>
        </div>

        <div v-else-if="faseActual === 2" class="animacion-entrada flex flex-col items-center justify-center h-full">
          <div class="w-full flex justify-between items-center mb-8">
            <span class="text-xs font-bold uppercase tracking-widest text-[#8B4513]/70">Actividad 1: Selecciona</span>
            <span class="text-sm font-mono bg-[#FDF8F1] px-3 py-1 rounded-md border border-orange-200">{{ indiceSeleccion + 1 }} / {{ preguntasSeleccion.length }}</span>
          </div>

          <h3 class="text-3xl font-black mb-8 text-center text-[#8B4513]">{{ preguntaSeleccionActual.pregunta }}</h3>

          <div class="grid grid-cols-1 gap-4 w-full max-w-md">
            <button
              v-for="(opcion, index) in preguntaSeleccionActual.opciones"
              :key="index"
              @click="verificarSeleccion(opcion)"
              :disabled="mostrarFeedback"
              :class="[
                'px-5 py-4 font-bold rounded-xl border-2 transition-all text-lg',
                !mostrarFeedback ? 'bg-white border-orange-100 text-[#8B4513] hover:border-[#8B4513] hover:bg-[#FDF8F1]' : '',
                mostrarFeedback && opcion === preguntaSeleccionActual.respuestaCorrecta ? 'bg-green-100 border-green-500 text-green-700' : '',
                mostrarFeedback && opcion === respuestaSeleccionada && opcion !== preguntaSeleccionActual.respuestaCorrecta ? 'bg-red-100 border-red-500 text-red-700' : '',
                mostrarFeedback && opcion !== respuestaSeleccionada && opcion !== preguntaSeleccionActual.respuestaCorrecta ? 'bg-gray-50 border-gray-200 text-gray-400 opacity-50' : ''
              ]"
            >
              {{ opcion }}
            </button>
          </div>
        </div>

        <div v-else-if="faseActual === 3" class="animacion-entrada flex flex-col items-center justify-center h-full">
          <div class="w-full flex justify-between items-center mb-8">
            <span class="text-xs font-bold uppercase tracking-widest text-[#8B4513]/70">Actividad 2: Escribe</span>
            <span class="text-sm font-mono bg-[#FDF8F1] px-3 py-1 rounded-md border border-orange-200">{{ indiceEscribe + 1 }} / {{ preguntasEscribe.length }}</span>
          </div>
          
          <p class="text-center mb-2 text-sm uppercase tracking-widest font-bold">Traduce el número</p>
          <div class="text-8xl font-black mb-8 text-[#8B4513]">{{ preguntaEscribeActual.numero }}</div>

          <div class="w-full max-w-md">
            <input 
              v-model="textoEscrito" 
              @keyup.enter="verificarEscritura"
              type="text" 
              placeholder="Escribe aquí en chontal..." 
              class="w-full text-center text-2xl p-4 border-2 border-orange-200 rounded-xl focus:outline-none focus:border-[#8B4513] text-[#5D2E17] mb-4"
              :disabled="mostrarFeedbackEscritura"
              :class="{ 'border-green-500 bg-green-50 text-green-700': feedbackEscritura === 'correcto', 'border-red-500 bg-red-50 text-red-700': feedbackEscritura === 'incorrecto' }"
            />
            
            <button 
              @click="verificarEscritura" 
              v-if="!mostrarFeedbackEscritura"
              class="w-full py-4 bg-[#8B4513] text-white font-bold rounded-xl hover:bg-[#5D2E17] transition-colors"
            >
              Comprobar
            </button>
            
            <div v-if="mostrarFeedbackEscritura" class="text-center font-bold text-lg mt-4">
              <span v-if="feedbackEscritura === 'correcto'" class="text-green-600">¡Correcto!</span>
              <span v-else class="text-red-500">La respuesta correcta era: {{ preguntaEscribeActual.respuestaCorrecta }}</span>
            </div>
          </div>
        </div>

        <div v-else class="text-center py-10 animacion-entrada">
          <div class="text-6xl mb-4">📜</div>
          <h2 class="text-3xl font-black mb-4">¡Módulo de Números Completado!</h2>
          <p class="text-xl mb-4">Actividad 1 (Selecciona): <span class="font-bold">{{ puntajeSeleccion }} / 2</span></p>
          <p class="text-xl mb-8">Actividad 2 (Escribe): <span class="font-bold">{{ puntajeEscribe }} / 3</span></p>
          
          <div class="flex justify-center gap-4">
            <button @click="reiniciarTodo" class="px-6 py-3 bg-white border-2 border-orange-200 text-[#8B4513] font-bold rounded-xl hover:bg-[#FDF8F1] transition-colors">
              Volver a repasar
            </button>
            <NuxtLink to="/aprender" class="px-6 py-3 bg-[#8B4513] text-white font-bold rounded-xl hover:bg-[#5D2E17] transition-colors">
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

// ==========================================
// FASE 2: SELECCIONA
// ==========================================
const preguntasSeleccion = ref([
  { pregunta: '¿Cómo se dice "2" en chontal?', opciones: ['ñulyi', 'ukwe\'', 'malpu\''], respuestaCorrecta: 'ukwe\'' },
  { pregunta: '¿Cómo se dice "5"?', opciones: ['mague\'', 'penla\'', 'kote\''], respuestaCorrecta: 'mague\'' }
])
const indiceSeleccion = ref(0)
const puntajeSeleccion = ref(0)
const mostrarFeedback = ref(false)
const respuestaSeleccionada = ref(null)

const preguntaSeleccionActual = computed(() => preguntasSeleccion.value[indiceSeleccion.value])

const verificarSeleccion = (opcion) => {
  if (mostrarFeedback.value) return 
  respuestaSeleccionada.value = opcion
  mostrarFeedback.value = true

  if (opcion === preguntaSeleccionActual.value.respuestaCorrecta) puntajeSeleccion.value++

  setTimeout(() => {
    if (indiceSeleccion.value < preguntasSeleccion.value.length - 1) {
      indiceSeleccion.value++
      mostrarFeedback.value = false
      respuestaSeleccionada.value = null
    } else {
      mostrarFeedback.value = false
      faseActual.value = 3 
    }
  }, 1500)
}

// ==========================================
// FASE 3: ESCRIBE (Simulando la actividad 2 y 3)
// ==========================================
const preguntasEscribe = ref([
  { numero: '1', respuestaCorrecta: 'ñulyi' },
  { numero: '4', respuestaCorrecta: 'malpu\'' },
  { numero: '9', respuestaCorrecta: 'penla\'' }
])
const indiceEscribe = ref(0)
const puntajeEscribe = ref(0)
const textoEscrito = ref('')
const mostrarFeedbackEscritura = ref(false)
const feedbackEscritura = ref('') // 'correcto' o 'incorrecto'

const preguntaEscribeActual = computed(() => preguntasEscribe.value[indiceEscribe.value])

const verificarEscritura = () => {
  if (mostrarFeedbackEscritura.value || textoEscrito.value.trim() === '') return
  
  mostrarFeedbackEscritura.value = true
  
  // Normalizar para no penalizar mayúsculas/minúsculas o espacios extra
  const ingresado = textoEscrito.value.trim().toLowerCase()
  const correcto = preguntaEscribeActual.value.respuestaCorrecta.toLowerCase()

  if (ingresado === correcto) {
    puntajeEscribe.value++
    feedbackEscritura.value = 'correcto'
  } else {
    feedbackEscritura.value = 'incorrecto'
  }

  setTimeout(() => {
    if (indiceEscribe.value < preguntasEscribe.value.length - 1) {
      indiceEscribe.value++
      textoEscrito.value = ''
      mostrarFeedbackEscritura.value = false
      feedbackEscritura.value = ''
    } else {
      faseActual.value = 4
    }
  }, 2000)
}

// ==========================================
// REINICIO GLOBAL
// ==========================================
const reiniciarTodo = () => {
  faseActual.value = 1
  indiceSeleccion.value = 0
  puntajeSeleccion.value = 0
  respuestaSeleccionada.value = null
  mostrarFeedback.value = false
  
  indiceEscribe.value = 0
  puntajeEscribe.value = 0
  textoEscrito.value = ''
  mostrarFeedbackEscritura.value = false
  feedbackEscritura.value = ''
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