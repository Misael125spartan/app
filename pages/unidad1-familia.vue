<template>
  <div class="min-h-screen bg-[#FDF8F1] text-[#5D2E17] font-sans pb-10">
    <main class="container mx-auto px-6 py-10">
      
      <div class="flex justify-between items-center mb-8 border-b border-orange-200/50 pb-6">
        <div>
          <h1 class="text-3xl font-black tracking-tight">UNIDAD 1: FAMILIA</h1>
          <p class="text-sm text-[#8B4513]/70 font-bold uppercase tracking-widest mt-1">
            Miembros de la familia en chontal
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
        <div class="h-2 flex-1 rounded-full transition-all duration-500" :class="faseActual >= 1 ? 'bg-[#8B4513]' : 'bg-orange-200'"></div>
        <div class="h-2 flex-1 rounded-full transition-all duration-500" :class="faseActual >= 2 ? 'bg-[#8B4513]' : 'bg-orange-200'"></div>
        <div class="h-2 flex-1 rounded-full transition-all duration-500" :class="faseActual >= 3 ? 'bg-[#8B4513]' : 'bg-orange-200'"></div>
        <div class="h-2 flex-1 rounded-full transition-all duration-500" :class="faseActual >= 4 ? 'bg-[#8B4513]' : 'bg-orange-200'"></div>
      </div>

      <div class="max-w-3xl mx-auto bg-white p-8 rounded-3xl border border-orange-100 shadow-md min-h-[450px]">
        
        <div v-if="faseActual === 1" class="animacion-entrada">
          <h2 class="text-2xl font-black mb-6 text-[#8B4513] text-center">Ka'nu xanuc' (Familia)</h2>
          
          <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-8 text-sm">
            <div v-for="(item, index) in vocabulario" :key="index" class="bg-orange-50 p-4 rounded-xl border border-orange-100 flex flex-col">
              <span class="font-black text-lg text-[#8B4513]">{{ item.chontal }}</span>
              <span class="font-bold text-[#5D2E17] mb-2">{{ item.espanol }}</span>
              <span class="text-xs text-[#8B4513]/70 font-mono bg-white px-2 py-1 rounded inline-block w-max mt-auto border border-orange-100">
                Pronunciación: {{ item.pronunciacion }}
              </span>
            </div>
          </div>

          <button @click="faseActual = 2" class="w-full py-4 bg-[#8B4513] text-white font-bold rounded-xl hover:bg-[#5D2E17] transition-colors">
            Comenzar Actividades
          </button>
        </div>

        <div v-else-if="faseActual === 2" class="animacion-entrada flex flex-col items-center justify-center h-full">
          <div class="w-full flex justify-between items-center mb-8">
            <span class="text-xs font-bold uppercase tracking-widest text-[#8B4513]/70">Actividad 1: Relaciona</span>
            <span class="text-sm font-mono bg-[#FDF8F1] px-3 py-1 rounded-md border border-orange-200">{{ indiceRelacionar + 1 }} / {{ preguntasRelacionar.length }}</span>
          </div>

          <h3 class="text-xl mb-2 text-center text-[#5D2E17] font-bold">¿Qué significa?</h3>
          <h2 class="text-5xl font-black mb-8 text-center text-[#8B4513]">{{ preguntaRelacionarActual.pregunta }}</h2>

          <div class="grid grid-cols-1 gap-4 w-full max-w-md">
            <button
              v-for="(opcion, index) in preguntaRelacionarActual.opciones"
              :key="index"
              @click="verificarRelacionar(opcion)"
              :disabled="mostrarFeedback"
              :class="['px-5 py-4 font-bold rounded-xl border-2 transition-all text-lg', obtenerClaseBoton(opcion, preguntaRelacionarActual.respuestaCorrecta)]"
            >
              {{ opcion }}
            </button>
          </div>
        </div>

        <div v-else-if="faseActual === 3" class="animacion-entrada flex flex-col items-center justify-center h-full">
          <div class="w-full flex justify-between items-center mb-8">
            <span class="text-xs font-bold uppercase tracking-widest text-[#8B4513]/70">Actividad 2: Pronunciación</span>
            <span class="text-sm font-mono bg-[#FDF8F1] px-3 py-1 rounded-md border border-orange-200">1 / 1</span>
          </div>
          
          <div class="text-6xl mb-6 animate-bounce">🎧</div>
          <p class="text-center mb-2 text-sm uppercase tracking-widest font-bold">Escucha la pronunciación:</p>
          <div class="text-4xl font-black mb-8 text-[#8B4513] bg-orange-50 px-8 py-4 rounded-2xl border-2 border-orange-200">
            "nia-yó"
          </div>

          <div class="grid grid-cols-3 gap-4 w-full max-w-lg">
            <button
              v-for="(opcion, index) in ['mamá', 'papá', 'abuelo']"
              :key="index"
              @click="verificarPronunciacion(opcion)"
              :disabled="mostrarFeedback"
              :class="['px-5 py-4 font-bold rounded-xl border-2 transition-all', obtenerClaseBoton(opcion, 'papá')]"
            >
              {{ opcion }}
            </button>
          </div>
        </div>

        <div v-else-if="faseActual === 4" class="animacion-entrada flex flex-col items-center justify-center h-full">
          <div class="w-full flex justify-between items-center mb-6">
            <span class="text-xs font-bold uppercase tracking-widest text-[#8B4513]/70">Actividad 3: ¿Quién es?</span>
            <span class="text-sm font-mono bg-[#FDF8F1] px-3 py-1 rounded-md border border-orange-200">{{ indiceVisual + 1 }} / {{ preguntasVisual.length }}</span>
          </div>

          <div class="w-48 h-48 mb-6 bg-[#FDF8F1] rounded-2xl border border-orange-200 flex items-center justify-center overflow-hidden">
            <img 
              :src="preguntaVisualActual.imagen" 
              class="object-contain w-full h-full p-4 transition-opacity duration-300"
              :class="{ 'opacity-50': mostrarFeedback }"
            />
          </div>
          
          <h3 class="text-xl font-bold mb-6 text-center">Selecciona la palabra correcta</h3>

          <div class="grid grid-cols-1 md:grid-cols-3 gap-4 w-full">
            <button
              v-for="(opcion, index) in preguntaVisualActual.opciones"
              :key="index"
              @click="verificarVisual(opcion)"
              :disabled="mostrarFeedback"
              :class="['px-5 py-4 font-bold rounded-xl border-2 transition-all', obtenerClaseBoton(opcion, preguntaVisualActual.respuestaCorrecta)]"
            >
              {{ opcion }}
            </button>
          </div>
        </div>

        <div v-else class="text-center py-10 animacion-entrada">
          <div class="text-6xl mb-4">🏠</div>
          <h2 class="text-3xl font-black mb-4">¡Módulo de Familia Completado!</h2>
          <p class="text-xl mb-2">Actividad 1 (Relacionar): <span class="font-bold">{{ puntajeRelacionar }} / 4</span></p>
          <p class="text-xl mb-2">Actividad 2 (Pronunciación): <span class="font-bold text-green-600">Completado</span></p>
          <p class="text-xl mb-8">Actividad 3 (Visual): <span class="font-bold">{{ puntajeVisual }} / 2</span></p>
          
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
const mostrarFeedback = ref(false)
const respuestaSeleccionada = ref(null)

// --- UTILIDAD PARA COLORES DE BOTONES ---
const obtenerClaseBoton = (opcion, correcta) => {
  if (!mostrarFeedback.value) return 'bg-white border-orange-100 text-[#8B4513] hover:border-[#8B4513] hover:bg-[#FDF8F1]'
  if (opcion === correcta) return 'bg-green-100 border-green-500 text-green-700'
  if (opcion === respuestaSeleccionada.value && opcion !== correcta) return 'bg-red-100 border-red-500 text-red-700'
  return 'bg-gray-50 border-gray-200 text-gray-400 opacity-50'
}

// ==========================================
// DATOS: TEORÍA
// ==========================================
const vocabulario = [
  { chontal: "Ña'yo'", espanol: "papá", pronunciacion: "nia-yó" },
  { chontal: "Ma'yo'", espanol: "mamá", pronunciacion: "ma-yó" },
  { chontal: "Ñaaju", espanol: "hermano", pronunciacion: "niaa-jú" },
  { chontal: "Ts'an", espanol: "hijo", pronunciacion: "tsán" },
  { chontal: "Ts'an xquic", espanol: "hija", pronunciacion: "tsán sh-kík" },
  { chontal: "Ña'yo' wane", espanol: "abuelo", pronunciacion: "nia-yó ua-né" },
  { chontal: "Ma'yo' wane", espanol: "abuela", pronunciacion: "ma-yó ua-né" },
  { chontal: "Ka'nu xanuc'", espanol: "familia", pronunciacion: "ka-nú sha-núk" }
]

// ==========================================
// FASE 2: RELACIONAR
// ==========================================
const preguntasRelacionar = ref([
  { pregunta: "Ña'yo'", opciones: ['mamá', 'papá', 'hija'], respuestaCorrecta: 'papá' },
  { pregunta: "Ma'yo'", opciones: ['abuela', 'mamá', 'hijo'], respuestaCorrecta: 'mamá' },
  { pregunta: "Ts'an", opciones: ['hermano', 'hijo', 'abuelo'], respuestaCorrecta: 'hijo' },
  { pregunta: "Ka'nu xanuc'", opciones: ['familia', 'hermana', 'abuela'], respuestaCorrecta: 'familia' }
])
const indiceRelacionar = ref(0)
const puntajeRelacionar = ref(0)
const preguntaRelacionarActual = computed(() => preguntasRelacionar.value[indiceRelacionar.value])

const verificarRelacionar = (opcion) => {
  if (mostrarFeedback.value) return 
  respuestaSeleccionada.value = opcion
  mostrarFeedback.value = true

  if (opcion === preguntaRelacionarActual.value.respuestaCorrecta) puntajeRelacionar.value++

  setTimeout(() => {
    if (indiceRelacionar.value < preguntasRelacionar.value.length - 1) {
      indiceRelacionar.value++
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
// FASE 3: PRONUNCIACIÓN
// ==========================================
const verificarPronunciacion = (opcion) => {
  if (mostrarFeedback.value) return 
  respuestaSeleccionada.value = opcion
  mostrarFeedback.value = true

  setTimeout(() => {
    mostrarFeedback.value = false
    respuestaSeleccionada.value = null
    faseActual.value = 4 
  }, 2000)
}

// ==========================================
// FASE 4: VISUAL
// ==========================================
const preguntasVisual = ref([
  { imagen: '/familia/abuelo.png', opciones: ["Ña'yo' wane", "Ma'yo'", "Ts'an"], respuestaCorrecta: "Ña'yo' wane" },
  { imagen: '/familia/abuela.png', opciones: ["Ma'yo' wane", "Ts'an xquic", "Ñaaju"], respuestaCorrecta: "Ma'yo' wane" }
])
const indiceVisual = ref(0)
const puntajeVisual = ref(0)
const preguntaVisualActual = computed(() => preguntasVisual.value[indiceVisual.value])

const verificarVisual = (opcion) => {
  if (mostrarFeedback.value) return 
  respuestaSeleccionada.value = opcion
  mostrarFeedback.value = true

  if (opcion === preguntaVisualActual.value.respuestaCorrecta) puntajeVisual.value++

  setTimeout(() => {
    if (indiceVisual.value < preguntasVisual.value.length - 1) {
      indiceVisual.value++
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
  
  indiceRelacionar.value = 0
  puntajeRelacionar.value = 0
  
  indiceVisual.value = 0
  puntajeVisual.value = 0
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