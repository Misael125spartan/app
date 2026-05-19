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
        <h1 class="text-3xl font-black uppercase tracking-tighter text-[#8B4513]">02. Sección de Leyendas</h1>
        <p class="text-xs text-[#8B4513]/70 font-bold uppercase tracking-widest mt-1">Mitos y crónicas locales de la región baja</p>
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
            <div v-if="obraSeleccionada.esPoema" class="whitespace-pre-line text-center italic text-xl">
              {{ obraSeleccionada.contenido[0] }}
            </div>
            <template v-else>
              <p v-for="(parrafo, i) in obraSeleccionada.contenido" :key="i" class="mb-6 indent-8 text-justify">
                {{ parrafo }}
              </p>
            </template>
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
    id: 1,
    titulo: 'El Boquerón (Cocógua)',
    tipo: 'Leyenda',
    autor: 'Jaime Zárate Escamilla',
    esPoema: false,
    contenido: [
      "En un lugar conocido como el Boquerón, que en la lengua chontal de la costa se dice cocógua (que significa 'donde sopla el viento'), hay una cueva situada casi justo en la franja divisoria en el territorio que pertenece al municipio de Huamelula, donde se dividen los terrenos de dos municipios importantes de la región chontal de la costa: Santiago Astata y San Pedro Huamelula; estos dos pueblos han compartido por muchos siglos sus lazos de amistad, sus creencias, su territorio, su historia y sus leyendas.",
      "La entrada a la caverna mide un metro de altura y ochenta centímetros de ancho, aproximadamente, aunque dicen que tiene una longitud de manyi miles de kilómetros y que sirve a los mentados (brujos) de Huamelula para viajar a otros pueblos o a otras ciudades, como a la capital del estado, y a otros les sirve para llegar al fondo de la tierra y platicar con los dioses del universo."
    ]
  },
  {
    id: 2,
    titulo: 'La Leyenda del Amigo',
    tipo: 'Leyenda',
    autor: 'Jaime Zárate Escamilla',
    esPoema: false,
    contenido: [
      "Cuenta esta leyenda que hace muchos años existió un hombre llamado Pedro. Era muy trabajador, un emprendedor incansable que por más que trabajaba no lograba atesorar riquezas, ya que en todo negocio que iniciaba le iba tan mal que terminaba abandonándolo; lo mismo pasaba con sus cosechas, que le costaban dinero, esfuerzo y mucho trabajo, pero todo lo perdía una y otra vez.",
      "Pedro había nacido en el seno de una familia humilde, como todos los que allí habitaban. Era de estatura baja, de cabello negro y encrespado. Tenía ojos azules, seguramente porque pertenecía a alguna estirpe extranjera, podríamos aventurar que española, pues muchos años atrás habitaron en este lugar personas de esta nacionalidad."
    ]
  },
  {
    id: 3,
    titulo: 'La Mesa',
    tipo: 'Narración Histórica',
    autor: 'Jaime Zárate Escamilla',
    esPoema: false,
    contenido: [
      "Desde tiempos inmemoriales hasta la actualidad, las raíces de Huamelula están asidas fuertemente como lazos irrompibles de ixtle que los antiguos sabios han legado a su viejo y hermoso pueblo a través de rituales sagrados, con la única intención de que sus herederos sigan paso a paso la herencia ancestral para la buena conducción de todos sus pueblos por el camino correcto que lleva a la gloria.",
      "A Huamelula le pertenece una vasta extensión territorial en el estado de Oaxaca, que forma una gran región a la que llaman región chontal baja o región de la costa. La palabra chontal en lengua náhuatl significa 'extranjero'."
    ]
  },
  {
    id: 4,
    titulo: 'Soy San Pedro Huamelula',
    tipo: 'Poema / Crónica',
    autor: 'Jaime Zárate Escamilla',
    esPoema: true,
    contenido: [
      `Soy por siglos ríos, lagunas, sierras, valles, mares, bosques,
      Llanuras, tierra fértil. Siempre esperándote
      A que llegaras a habitarme con fe y con verdadero amor,
      ¡¡Soy lo mejor!! Puedes mirarme mi faz o mi interior.

      Soy invencible guerrero de estos importantes lugares,
      Soporté desastres, sequías y recios vendavales,
      Cuando llegaste; te tuve en mi humilde regazo y
      Me ofreci a ti en ricas viandas y en ricos manantiales.`
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