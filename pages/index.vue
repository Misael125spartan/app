<template>
  <div class="min-h-screen bg-[#FDF8F1] text-[#5D2E17]">
    <header
      class="border-b border-orange-200/50 bg-[#8B4513] sticky top-0 z-50 shadow-md"
    >
      <div
        class="container mx-auto px-6 py-4 flex justify-between items-center"
      >
        <div class="flex items-center gap-3">
          <div
            class="h-10 w-10 bg-[#E67E22] rounded-xl flex items-center justify-center font-black text-white shadow-sm"
          >
            H
          </div>
          <div>
            <span class="text-xl font-black uppercase tracking-tight text-white"
              >Huamelollan</span
            >
            <p class="text-[9px] text-orange-200/70 font-mono tracking-widest">
              ITGAM - TECNM
            </p>
          </div>
        </div>
        <nav
          class="hidden md:flex items-center gap-8 text-sm font-semibold text-orange-100/80"
        >
          <a href="#cultura" class="hover:text-white transition-colors duration-200">1. Cultura</a>
          <a href="#historias" class="hover:text-white transition-colors duration-200">2. Historias</a>
          <a href="#aprender" class="hover:text-white transition-colors duration-200">3. Aprender</a>
          <a href="#perfil" class="hover:text-white transition-colors duration-200">4. Perfil</a>
        </nav>
        <span
          class="text-xs text-[#E67E22] bg-white/10 px-3 py-1 rounded-full font-mono uppercase tracking-widest hidden sm:block"
        >
          Halcón Peregrino v2.6
        </span>
      </div>
    </header>

    <main
      class="container mx-auto px-6 py-12 grid grid-cols-1 lg:grid-cols-12 gap-12"
    >
      <div class="lg:col-span-6 flex flex-col justify-center">
        <span
          class="text-[#E67E22] text-xs font-bold tracking-widest uppercase mb-3"
          >Proyecto Académico - 9° Semestre</span
        >
        <h1
          class="text-5xl md:text-6xl font-black uppercase tracking-tighter leading-none mb-6 text-[#5D2E17]"
        >
          Plataforma <br /><span class="text-[#E67E22]">Huamelollan</span>
        </h1>
        <p class="text-[#8B4513]/80 text-base leading-relaxed max-w-lg mb-8">
          Sistema interactivo de preservación y aprendizaje cultural diseñado en
          el Instituto Tecnológico de la Gustavo A. Madero.
        </p>

        <div class="grid grid-cols-2 gap-4 max-w-sm">
          <a
            href="#cultura"
            class="p-4 bg-white border border-orange-100 rounded-2xl hover:border-[#E67E22] shadow-sm transition-all group"
          >
            <div
              class="text-[#E67E22] font-bold text-base mb-1 group-hover:translate-x-1 transition-transform"
            >
              01 / Cultura 🥘
            </div>
            <p class="text-[10px] text-[#8B4513]/60 font-semibold">Tradiciones y Danzas</p>
          </a>
          <a
            href="#historias"
            class="p-4 bg-white border border-orange-100 rounded-2xl hover:border-[#8B4513] shadow-sm transition-all group"
          >
            <div
              class="text-[#8B4513] font-bold text-base mb-1 group-hover:translate-x-1 transition-transform"
            >
              02 / Historias 📖
            </div>
            <p class="text-[10px] text-[#8B4513]/60 font-semibold">Leyendas y Cuentos</p>
          </a>
        </div>
      </div>

      <div class="lg:col-span-6 flex flex-col justify-center">
        <div
          class="bg-white border border-orange-100 p-8 rounded-[2.5rem] shadow-xl"
        >
          <div class="flex items-center justify-between mb-8">
            <h2 class="text-2xl font-black uppercase tracking-tight text-[#5D2E17]">
              Menú de Navegación
            </h2>
            <span
              class="px-3 py-1 bg-[#E67E22] text-white text-[10px] font-bold tracking-widest rounded-lg uppercase shadow-sm"
            >
              Activo
            </span>
          </div>

          <div class="space-y-5">
            <NuxtLink
              to="/cultura"
              class="w-full p-4 bg-[#FDF8F1] hover:bg-white border border-transparent hover:border-orange-200 rounded-2xl flex items-center justify-between transition-all group shadow-sm"
            >
              <div class="flex items-center gap-4">
                <div
                  class="h-12 w-12 bg-white rounded-xl flex items-center justify-center text-xl shadow-sm border border-orange-50"
                >
                  🥘
                </div>
                <div>
                  <div class="font-bold text-[#5D2E17] group-hover:text-[#E67E22] transition-colors">
                    Sección Cultural
                  </div>
                  <div class="text-[10px] text-[#8B4513]/60 font-medium">
                    Gastronomía, Vestimenta y Tradiciones
                  </div>
                </div>
              </div>
              <span class="text-[#E67E22] font-bold group-hover:translate-x-1 transition-transform">&rarr;</span>
            </NuxtLink>

            <NuxtLink
              to="/historias"
              class="w-full p-4 bg-[#FDF8F1] hover:bg-white border border-transparent hover:border-orange-200 rounded-2xl flex items-center justify-between transition-all group shadow-sm"
            >
              <div class="flex items-center gap-4">
                <div
                  class="h-12 w-12 bg-white rounded-xl flex items-center justify-center text-xl shadow-sm border border-orange-50"
                >
                  📖
                </div>
                <div>
                  <div class="font-bold text-[#5D2E17] group-hover:text-[#8B4513] transition-colors">
                    Módulo de Historias
                  </div>
                  <div class="text-[10px] text-[#8B4513]/60 font-medium">
                    Cuentos, Leyendas y Poemas
                  </div>
                </div>
              </div>
              <span class="text-[#8B4513] font-bold group-hover:translate-x-1 transition-transform">&rarr;</span>
            </NuxtLink>

            <NuxtLink
              to="/aprender"
              class="w-full p-4 bg-[#FDF8F1] hover:bg-white border border-transparent hover:border-orange-200 rounded-2xl flex items-center justify-between transition-all group shadow-sm"
            >
              <div class="flex items-center gap-4">
                <div
                  class="h-12 w-12 bg-white rounded-xl flex items-center justify-center text-xl shadow-sm border border-orange-50"
                >
                  🏫
                </div>
                <div>
                  <div class="font-bold text-[#5D2E17] group-hover:text-green-700 transition-colors">
                    Nivel de Aprendizaje
                  </div>
                  <div class="text-[10px] text-[#8B4513]/60 font-medium">
                    Unidades, Actividades y Evaluaciones
                  </div>
                </div>
              </div>
              <span class="text-green-600 font-bold group-hover:translate-x-1 transition-transform">&rarr;</span>
            </NuxtLink>

            <NuxtLink
              to="/perfil"
              class="w-full p-4 bg-[#FDF8F1] hover:bg-white border border-transparent hover:border-orange-200 rounded-2xl flex items-center justify-between transition-all group shadow-sm"
            >
              <div class="flex items-center gap-4">
                <div
                  class="h-12 w-12 bg-white rounded-xl flex items-center justify-center text-xl shadow-sm border border-orange-50"
                >
                  🏆
                </div>
                <div>
                  <div class="font-bold text-[#5D2E17] group-hover:text-amber-600 transition-colors">
                    Perfil y Logros
                  </div>
                  <div class="text-[10px] text-[#8B4513]/60 font-medium">
                    Progreso general y puntajes obtenidos
                  </div>
                </div>
              </div>
              <span class="text-amber-500 font-bold group-hover:translate-x-1 transition-transform">&rarr;</span>
            </NuxtLink>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>