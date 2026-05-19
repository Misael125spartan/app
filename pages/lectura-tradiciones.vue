<template>
  <div class="min-h-screen bg-[#FDF8F1] p-10">
    <div class="max-w-4xl mx-auto bg-white p-10 rounded-3xl border border-orange-100 shadow-xl">
      <NuxtLink to="/cultura" class="text-sm font-bold text-[#8B4513] mb-6 block">← Volver</NuxtLink>
      <h1 class="text-4xl font-black text-[#8B4513] mb-8">{{ obra.titulo }}</h1>
      <div class="prose prose-orange max-w-none text-lg text-[#5D2E17] leading-relaxed">
        <p v-for="(p, i) in obra.contenido" :key="i" class="mb-4">{{ p }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const obra = ref({ titulo: 'Cargando...', contenido: [] })

const biblioteca = {
  1: { titulo: 'Antecedentes Históricos', contenido: ["El pueblo de Huamelula...", "La danza de moros y cristianos..."] },
  2: { titulo: 'Festividad del Carnaval', contenido: ["El mito y la historia...", "La Iglesia se apoderó..."] },
  3: { titulo: 'Semana Santa', contenido: ["DOMINGO DE RAMOS...", "LA ÚLTIMA CENA..."] },
  4: { titulo: 'La Lagarta', contenido: ["La lagarta participa como emblema...", "La historia oral de los chontales..."] },
  5: { titulo: 'Las Mulatas', contenido: ["Las mulyatas se conducen...", "El objetivo es emparentar..."] },
  6: { titulo: 'Los Caballeros', contenido: ["Este grupo participa...", "Ellos entran en la animación..."] }
}

onMounted(() => {
  const id = route.query.id
  if (biblioteca[id]) obra.value = biblioteca[id]
})
</script>*