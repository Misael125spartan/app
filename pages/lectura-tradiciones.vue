<template>
  <div class="min-h-screen bg-[#FDF8F1] text-[#5D2E17] font-sans pb-10">
    <header class="border-b border-orange-200/50 bg-[#8B4513] sticky top-0 z-50 shadow-md">
      <div class="container mx-auto px-6 py-4 flex justify-between items-center">
        <NuxtLink to="/cultura" class="px-5 py-2 bg-[#FDF8F1] text-[#8B4513] text-xs font-bold rounded-xl hover:bg-orange-100">Volver a Cultura</NuxtLink>
      </div>
    </header>

    <main class="container mx-auto px-6 py-10">
      <div class="flex flex-col lg:flex-row gap-8">
        <div class="lg:w-1/3 flex flex-col gap-4">
          <button v-for="obra in biblioteca" :key="obra.id" @click="seleccionarObra(obra)"
            class="text-left p-5 rounded-2xl border-2 transition-all shadow-sm"
            :class="obraSeleccionada.id === obra.id ? 'bg-[#8B4513] text-white' : 'bg-white border-orange-100'">
            <h3 class="text-lg font-black">{{ obra.titulo }}</h3>
          </button>
        </div>

        <div class="lg:w-2/3 bg-white p-12 rounded-3xl border border-orange-100 shadow-xl">
          <h2 class="text-4xl font-black text-[#8B4513] mb-8">{{ obraSeleccionada.titulo }}</h2>
          <div class="prose prose-orange max-w-none text-lg leading-relaxed font-serif">
            <p v-for="(p, i) in obraSeleccionada.contenido" :key="i" class="mb-6 indent-8 text-justify">{{ p }}</p>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const obraSeleccionada = ref({ titulo: 'Cargando...', contenido: [] })

const biblioteca = [
  {
    id: 1,
    titulo: 'Antecedentes Históricos',
    contenido: [
      "El pueblo de Huamelula y sus antecedentes históricos. El principal objetivo para el clero era la participación de los habitantes, así era más fácil la conquista de almas; al tener cerca al pueblo sin distinción de edades, a todos les daban un papel que pareciera importante, tanto a viejos como a jóvenes, niños, hombres y mujeres e incluso a los animales que los frailes consideraban símbolos.",
      "La danza de moros y cristianos es de origen europeo, y llegó a nosotros por los conquistadores españoles, que resultó ser la conjugación del arte juglar, épico, popular, del teatro de masas y de procesiones religiosas. De ahí que la danza de moros y cristianos que se celebra en San Pedro Huamelula resulta ser siempre chusca y divertida; es muy interesante cuando todo el público participa.",
      "Los frailes elaboraron casi todos los instrumentos que necesitaron y que ellos mismos pudieron fabricar, tales como adornos o decoraciones de papel, máscaras de madera, carretas, vestiduras, tintes con caracol, redes o atarrayas, flautas, tambores, imágenes de madera, campanas de bronce, y la construcción y reparación de la iglesia."
    ]
  },
  {
    id: 2,
    titulo: 'Festividad del Carnaval',
    contenido: [
      "Desde el inicio hicimos la observación de que el mito y la historia van por rumbos diferentes y es sumamente difícil relacionarlos, sobre todo en lo que se refiere a las fiestas del carnaval de Huamelula.",
      "La etimología de la palabra carnaval proviene del latín carnem levare, que literalmente significa carne levantar. Por un lado se queman las velas y por otro la palma en un verdadero ritual.",
      "Al compás de la danza, los mayordomos regalan atole de diferentes sabores, de Perú, ajonjolí, maíz con piloncillo, etcétera, y con la danza trasladan la ceniza de la palma a la iglesia de San Pedro para que sea utilizada al día siguiente.",
      "La Iglesia se apoderó de la danza, de la gente, de la tradición, de las formas, de los tiempos, del control, de casi todo. Así termina el carnaval en Huamelula, entre danzas y cascarones con fushina."
    ]
  },
  {
    id: 3,
    titulo: 'Semana Santa',
    contenido: [
      "DOMINGO DE RAMOS. Casi toda la población acude al templo de San Pedro Apóstol para estar presente a la hora de la bendición de las palmas, llevando entre sus brazos flores de la temporada que despiden aromas agradables, como las de corpus, cordoncillo y albahaca; se organiza una procesión alrededor de la iglesia de San Pedro.",
      "LA ÚLTIMA CENA. El presidente nombra, antes de la fiesta, a tres personas... Durante el final de la semana mayor, las dos procesiones se detienen frente a frente; los músicos y los cantores se hacen a un lado para dar paso a los que llevan los ciriales, esparcen flores de mayo a los santos, dejando el suelo tapizado de ellas, hasta regresar a sus capillas donde se oficia 'La Misa de Resurrección'."
    ]
  },
  {
    id: 4,
    titulo: 'La Lagarta',
    contenido: [
      "Si vemos que en esta celebración participan los huapis con un lagarto, tal vez no podamos entender qué hace ahí el reptil. Los sabios que pusieron la coreografía, el vestuario, los ritmos de las danzas y los instrumentos, fueron cuidadosos al poner el tema o la trama.",
      "La lagarta participa como emblema de la madre tierra que conoce dos tipos de vida, dentro del agua y fuera de ella. La historia oral de los chontales no es ajena a este complejo mitológico que conecta reptiles con fuerzas y parajes acuáticos, donde el cocodrilo está asociado con la tierra, el agua que la hace fértil y la fecundidad."
    ]
  },
  {
    id: 5,
    titulo: 'Las Mulatas (Lan Mulyatas)',
    contenido: [
      "Otro de los grupos que anima la fiesta con su participación es el de las mulatas o mulyatas. Ellas se conducen con liberalidad y toman la iniciativa al elegir entre los jóvenes a su pareja para bailar con él, abrazarlo y finalmente proponerle matrimonio.",
      "En realidad, estas féminas son hombres vestidos a la usanza de las mujeres istmeñas. Se cubren el rostro para conservar el anonimato. El objetivo de las mulyatas es emparentar con los dueños del territorio, bailando un son tradicional del istmo llamado El Guashi, que significa unión."
    ]
  },
  {
    id: 6,
    titulo: 'Los Caballeros',
    contenido: [
      "Este grupo participa en la representación teatral haciendo el papel de los rancheros que viven fuera del pueblo, que son los que cuidan el ganado y se mantienen vigilantes de la seguridad de la población.",
      "En esta festividad reclaman y negocian el territorio huamelulense, el cual les pertenece. Ellos entran en la animación de la fiesta el último día, el 30 de junio, teniendo como símbolo a San Martín Caballero. Representan el papel que desempeñan en la vida cotidiana conservando la tradición que dejaron sus antecesores."
    ]
  }
]

const seleccionarObra = (obra) => { 
  obraSeleccionada.value = obra 
  window.scrollTo({ top: 0, behavior: 'smooth' })
}

onMounted(() => {
  const id = Number(route.query.id)
  if (id) {
    const found = biblioteca.find(item => item.id === id)
    if (found) obraSeleccionada.value = found
  } else {
    obraSeleccionada.value = biblioteca[0]
  }
})
</script>