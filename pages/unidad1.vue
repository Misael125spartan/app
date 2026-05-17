<template>
  <div class="min-h-screen bg-[#FDF8F1] text-[#5D2E17] font-sans pb-10">
    <main class="container mx-auto px-6 py-10">
      
      <div class="flex justify-between items-center mb-8 border-b border-orange-200/50 pb-6">
        <div>
          <h1 class="text-3xl font-black tracking-tight">UNIDAD 1</h1>
          <p class="text-sm text-[#8B4513]/70 font-bold uppercase tracking-widest mt-1">
            Vocabulario Básico: Animales
          </p>
        </div>
        <NuxtLink 
          to="/aprender" 
          class="px-5 py-2.5 bg-white border border-orange-200 text-[#8B4513] text-xs font-bold rounded-lg hover:border-[#8B4513] transition-all"
        >
          Volver a Niveles
        </NuxtLink>
      </div>

      <div v-if="faseActual < 4" class="max-w-2xl mx-auto mb-6 flex gap-2">
        <div class="h-2 flex-1 rounded-full transition-all duration-500" :class="faseActual >= 1 ? 'bg-[#8B4513]' : 'bg-orange-200'"></div>
        <div class="h-2 flex-1 rounded-full transition-all duration-500" :class="faseActual >= 2 ? 'bg-[#8B4513]' : 'bg-orange-200'"></div>
        <div class="h-2 flex-1 rounded-full transition-all duration-500" :class="faseActual >= 3 ? 'bg-[#8B4513]' : 'bg-orange-200'"></div>
      </div>

      <div class="max-w-2xl mx-auto bg-white p-8 rounded-3xl border border-orange-100 shadow-md min-h-[400px]">
        
        <div v-if="faseActual === 1" class="animacion-entrada">
          <div class="flex justify-between items-center mb-6">
            <span class="text-xs font-bold uppercase tracking-widest text-[#8B4513]/70">1. Adivina el animal</span>
            <span class="text-sm font-mono bg-[#FDF8F1] px-3 py-1 rounded-md border border-orange-200">{{ indiceAdivina + 1 }} / {{ preguntasAdivina.length }}</span>
          </div>

          <div class="flex flex-col items-center">
            <div class="w-48 h-48 mb-6 bg-[#FDF8F1] rounded-2xl border border-orange-200 flex items-center justify-center overflow-hidden">
              <img :src="preguntaAdivinaActual.imagen" class="object-contain w-full h-full p-4 transition-opacity duration-300" :class="{ 'opacity-50': mostrarFeedback }"/>
            </div>
            <h3 class="text-xl font-bold mb-6 text-center">¿Cómo se dice {{ preguntaAdivinaActual.animal.toLowerCase() }}?</h3>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-4 w-full">
              <button
                v-for="(opcion, index) in preguntaAdivinaActual.opciones"
                :key="index"
                @click="verificarAdivina(opcion)"
                :disabled="mostrarFeedback"
                :class="[
                  'px-5 py-4 font-bold rounded-xl border-2 transition-all',
                  !mostrarFeedback ? 'bg-white border-orange-100 text-[#8B4513] hover:border-[#8B4513] hover:bg-[#FDF8F1]' : '',
                  mostrarFeedback && opcion === preguntaAdivinaActual.respuestaCorrecta ? 'bg-green-100 border-green-500 text-green-700' : '',
                  mostrarFeedback && opcion === respuestaSeleccionada && opcion !== preguntaAdivinaActual.respuestaCorrecta ? 'bg-red-100 border-red-500 text-red-700' : '',
                  mostrarFeedback && opcion !== respuestaSeleccionada && opcion !== preguntaAdivinaActual.respuestaCorrecta ? 'bg-gray-50 border-gray-200 text-gray-400 opacity-50' : ''
                ]"
              >
                {{ opcion }}
              </button>
            </div>
          </div>
        </div>

        <div v-else-if="faseActual === 2" class="animacion-entrada">
          <div class="flex justify-between items-center mb-6">
            <span class="text-xs font-bold uppercase tracking-widest text-[#8B4513]/70">2. Memorama / Relacionar</span>
            <span class="text-sm font-mono bg-[#FDF8F1] px-3 py-1 rounded-md border border-orange-200">Encuentra los pares</span>
          </div>
          
          <p class="text-center mb-6 text-sm">Relaciona la imagen con su palabra correcta en chontal.</p>

          <div class="grid grid-cols-3 gap-4">
            <button 
              v-for="(tarjeta, index) in tarjetasMemorama" 
              :key="index"
              @click="voltearTarjeta(index)"
              :disabled="tarjeta.resuelta || tarjetasVolteadas.length >= 2 || tarjeta.volteada"
              class="h-32 rounded-2xl border-2 flex items-center justify-center text-lg font-bold transition-all p-2"
              :class="[
                tarjeta.resuelta ? 'bg-green-50 border-green-200 opacity-50' : 
                tarjeta.volteada ? 'bg-[#FDF8F1] border-[#8B4513] text-[#8B4513] shadow-inner' : 
                'bg-white border-orange-100 text-transparent hover:border-orange-300 shadow-sm'
              ]"
            >
              <template v-if="tarjeta.volteada || tarjeta.resuelta">
                <img v-if="tarjeta.tipo === 'img'" :src="tarjeta.contenido" class="h-full object-contain" />
                <span v-else>{{ tarjeta.contenido }}</span>
              </template>
              <span v-else class="text-orange-200 text-3xl">?</span>
            </button>
          </div>
        </div>

        <div v-else-if="faseActual === 3" class="animacion-entrada">
          <div class="flex justify-between items-center mb-6">
            <span class="text-xs font-bold uppercase tracking-widest text-red-600">3. Velocidad</span>
            <div class="flex items-center gap-2">
              <span class="text-2xl animate-pulse">⏱️</span>
              <span class="text-xl font-black" :class="tiempoRestante <= 2 ? 'text-red-500' : 'text-[#8B4513]'">{{ tiempoRestante }}s</span>
            </div>
          </div>

          <div class="flex flex-col items-center">
            <div class="w-48 h-48 mb-6 bg-[#FDF8F1] rounded-2xl border border-red-200 flex items-center justify-center overflow-hidden relative">
              <img :src="preguntaVelocidadActual.imagen" class="object-contain w-full h-full p-4"/>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-3 gap-4 w-full">
              <button
                v-for="(opcion, index) in preguntaVelocidadActual.opciones"
                :key="index"
                @click="verificarVelocidad(opcion)"
                class="px-5 py-4 font-bold rounded-xl border-2 bg-white border-orange-100 text-[#8B4513] hover:border-red-400 hover:bg-red-50 transition-all"
              >
                {{ opcion }}
              </button>
            </div>
          </div>
        </div>

        <div v-else class="text-center py-10 animacion-entrada">
          <div class="text-6xl mb-4">🏆</div>
          <h2 class="text-3xl font-black mb-4">¡Unidad Completada!</h2>
          <p class="text-xl mb-4">Puntaje Adivina: <span class="font-bold">{{ puntajeAdivina }} / 3</span></p>
          <p class="text-xl mb-4">Memorama: <span class="font-bold text-green-600">Completado</span></p>
          <p class="text-xl mb-8">Puntaje Velocidad: <span class="font-bold">{{ puntajeVelocidad }} / 3</span></p>
          
          <div class="flex justify-center gap-4">
            <button @click="reiniciarTodo" class="px-6 py-3 bg-white border-2 border-orange-200 text-[#8B4513] font-bold rounded-xl hover:bg-[#FDF8F1] transition-colors">
              Volver a jugar
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
import { ref, computed, onUnmounted } from 'vue'

// --- ESTADO GLOBAL DEL JUEGO ---
// fase 1: Adivina, fase 2: Memorama, fase 3: Velocidad, fase 4: Resultados
const faseActual = ref(1) 

// ==========================================
// LÓGICA FASE 1: ADIVINA EL ANIMAL
// ==========================================
const preguntasAdivina = ref([
  { animal: 'Conejo', imagen: '/animales/conejo.jpg', opciones: ['offa´', 'afo´', 'affe´'], respuestaCorrecta: 'afo´' },
  { animal: 'Caballo', imagen: '/animales/caballo.jpg', opciones: ['aylaw´', 'ayylaw´', 'aywala´'], respuestaCorrecta: 'aywala´' },
  { animal: 'Tortuga', imagen: '/animales/tortuga.jpg', opciones: ['apempe´', 'appmp´', 'pammpe´'], respuestaCorrecta: 'apempe´' }
])
const indiceAdivina = ref(0)
const puntajeAdivina = ref(0)
const mostrarFeedback = ref(false)
const respuestaSeleccionada = ref(null)

const preguntaAdivinaActual = computed(() => preguntasAdivina.value[indiceAdivina.value])

const verificarAdivina = (opcion) => {
  if (mostrarFeedback.value) return 
  respuestaSeleccionada.value = opcion
  mostrarFeedback.value = true

  if (opcion === preguntaAdivinaActual.value.respuestaCorrecta) puntajeAdivina.value++

  setTimeout(() => {
    if (indiceAdivina.value < preguntasAdivina.value.length - 1) {
      indiceAdivina.value++
      mostrarFeedback.value = false
      respuestaSeleccionada.value = null
    } else {
      // Pasar al memorama
      mostrarFeedback.value = false
      faseActual.value = 2 
    }
  }, 1500)
}

// ==========================================
// LÓGICA FASE 2: MEMORAMA (RELACIONAR)
// ==========================================
// Definimos los pares basados en tu documento
const datosMemorama = [
  { parId: 1, tipo: 'img', contenido: '/animales/pollito.jpg' },
  { parId: 1, tipo: 'txt', contenido: "aputyu'" },
  { parId: 2, tipo: 'img', contenido: '/animales/pescado.jpg' },
  { parId: 2, tipo: 'txt', contenido: "atyiu'" },
  { parId: 3, tipo: 'img', contenido: '/animales/caracol.jpg' },
  { parId: 3, tipo: 'txt', contenido: "alo'ke" }
]

// Función para barajar las tarjetas aleatoriamente
const barajarTarjetas = () => {
  return datosMemorama
    .map(t => ({ ...t, volteada: false, resuelta: false }))
    .sort(() => Math.random() - 0.5)
}

const tarjetasMemorama = ref(barajarTarjetas())
const tarjetasVolteadas = ref([])
const paresResueltos = ref(0)

const voltearTarjeta = (index) => {
  if (tarjetasVolteadas.value.length >= 2) return
  
  tarjetasMemorama.value[index].volteada = true
  tarjetasVolteadas.value.push(index)

  if (tarjetasVolteadas.value.length === 2) {
    const [idx1, idx2] = tarjetasVolteadas.value
    const t1 = tarjetasMemorama.value[idx1]
    const t2 = tarjetasMemorama.value[idx2]

    if (t1.parId === t2.parId) {
      // Es un par correcto
      setTimeout(() => {
        tarjetasMemorama.value[idx1].resuelta = true
        tarjetasMemorama.value[idx2].resuelta = true
        tarjetasVolteadas.value = []
        paresResueltos.value++
        
        // Si resolvió los 3 pares, pasa a la fase de Velocidad
        if (paresResueltos.value === 3) {
          setTimeout(() => { iniciarFaseVelocidad() }, 1000)
        }
      }, 500)
    } else {
      // No coinciden, se voltean de nuevo
      setTimeout(() => {
        tarjetasMemorama.value[idx1].volteada = false
        tarjetasMemorama.value[idx2].volteada = false
        tarjetasVolteadas.value = []
      }, 1200)
    }
  }
}

// ==========================================
// LÓGICA FASE 3: VELOCIDAD
// ==========================================
const preguntasVelocidad = ref([
  { animal: 'Gato', imagen: '/animales/gato.jpg', opciones: ["mixtyo'", "mish'", "mixu'"], respuestaCorrecta: "mixtyo'" },
  { animal: 'Tigre', imagen: '/animales/tigre.jpg', opciones: ["ipaj'awa'", "ajaw'", "ipaj'"], respuestaCorrecta: "ipaj'awa'" },
  { animal: 'Alacrán', imagen: '/animales/alacran.jpg', opciones: ["untyiaspo'", "tyias'", "untypo'"], respuestaCorrecta: "untyiaspo'" }
])
const indiceVelocidad = ref(0)
const puntajeVelocidad = ref(0)
const tiempoRestante = ref(5) // 5 segundos por pregunta
let temporizador = null

const preguntaVelocidadActual = computed(() => preguntasVelocidad.value[indiceVelocidad.value])

const iniciarFaseVelocidad = () => {
  faseActual.value = 3
  iniciarTemporizador()
}

const iniciarTemporizador = () => {
  tiempoRestante.value = 5
  clearInterval(temporizador)
  temporizador = setInterval(() => {
    tiempoRestante.value--
    if (tiempoRestante.value <= 0) {
      siguientePreguntaVelocidad(false) // Se acabó el tiempo = respuesta incorrecta
    }
  }, 1000)
}

const verificarVelocidad = (opcion) => {
  const correcto = opcion === preguntaVelocidadActual.value.respuestaCorrecta
  siguientePreguntaVelocidad(correcto)
}

const siguientePreguntaVelocidad = (fueCorrecto) => {
  clearInterval(temporizador)
  if (fueCorrecto) puntajeVelocidad.value++

  if (indiceVelocidad.value < preguntasVelocidad.value.length - 1) {
    indiceVelocidad.value++
    iniciarTemporizador()
  } else {
    // Fin del juego
    faseActual.value = 4
  }
}

// Limpiar temporizador si el usuario sale de la página
onUnmounted(() => {
  clearInterval(temporizador)
})

// ==========================================
// REINICIO GLOBAL
// ==========================================
const reiniciarTodo = () => {
  faseActual.value = 1
  indiceAdivina.value = 0
  puntajeAdivina.value = 0
  respuestaSeleccionada.value = null
  mostrarFeedback.value = false
  
  tarjetasMemorama.value = barajarTarjetas()
  tarjetasVolteadas.value = []
  paresResueltos.value = 0
  
  indiceVelocidad.value = 0
  puntajeVelocidad.value = 0
  clearInterval(temporizador)
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