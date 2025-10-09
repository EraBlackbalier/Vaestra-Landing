<script setup lang="ts">
import { ref, onMounted } from 'vue'

// Tipos para las rutas de imágenes
type ImagePath = `/images/${string}`

const isVisible = ref(false)
const currentHeroImage = ref(0)

// Definición de rutas de imágenes con type safety
const clientes: ImagePath[] = [
  '/images/clientes1.jpg',
  '/images/clientes2.png',
  '/images/clientes3.jpg',
  '/images/clientes4.png',
  '/images/clientes5.jpg'
]

const distribuidores: ImagePath[] = [
  '/images/parker.jpg',
  '/images/beta.png',
  '/images/aircare.png'
]

// Imágenes para el hero carousel
const heroImages: ImagePath[] = [
  '/images/carrusel1.jpg',
  '/images/carrusel2.jpg',
  '/images/carrusel3.jpg',
  '/images/carrusel4.jpg',
  
]

// Logo path con type safety
const logoPath: ImagePath = '/images/logo.png'

onMounted(() => {
  setTimeout(() => {
    isVisible.value = true
  }, 100)
  
  // Auto-rotate hero carousel
  setInterval(() => {
    currentHeroImage.value = (currentHeroImage.value + 1) % heroImages.length
  }, 3500)
})

const scrollToSection = (sectionId: string) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

const openWhatsApp = () => {
  const phoneNumber = '5214422395074'
  const message = encodeURIComponent('Hola, me interesa conocer más sobre los servicios de Vaestra.')
  window.open(`https://wa.me/${phoneNumber}?text=${message}`, '_blank')
}
</script>

<template>
  <div class="min-h-screen bg-white font-sans">
    <!-- Navigation -->
    <nav class="fixed top-0 w-full bg-white/95 backdrop-blur-sm shadow z-50">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex justify-between items-center h-16">
          <div class="flex items-center space-x-3">
            <img :src="logoPath" alt="Vaestra Logo" class="h-10 w-auto" />
            <span class="text-2xl font-bold text-red-600">Vaestra</span>
          </div>

          <div class="hidden md:block">
            <div class="ml-10 flex items-baseline space-x-4">
              <button @click="scrollToSection('inicio')" class="text-gray-700 hover:text-blue-600 px-3 py-2 text-sm font-medium">Inicio</button>
              <button @click="scrollToSection('clientes')" class="text-gray-700 hover:text-blue-600 px-3 py-2 text-sm font-medium">Clientes</button>
              <button @click="scrollToSection('distribuidores')" class="text-gray-700 hover:text-blue-600 px-3 py-2 text-sm font-medium">Distribuidores</button>
              <button @click="scrollToSection('equipo')" class="text-gray-700 hover:text-blue-600 px-3 py-2 text-sm font-medium">Equipo</button>
              <button @click="scrollToSection('contacto')" class="bg-red-600 text-white px-4 py-2 rounded-md text-sm font-medium hover:bg-red-700 transition">Contacto</button>
            </div>
          </div>
        </div>
      </div>
    </nav>

    <!-- Hero with Diagonal Split -->
    <section id="inicio" class="relative pt-16 min-h-screen overflow-hidden">
      <div class="relative h-[calc(100vh-4rem)] flex">
        <!-- Left side - Logo and Content with Red Background -->
        <div class="relative z-10 w-full lg:w-1/2 flex items-center justify-center p-8 diagonal-red-bg">
          <div class="max-w-xl space-y-8 text-white" :class="{ 'animate-slide-in-left': isVisible }">
            <img :src="logoPath" alt="Logo Vaestra" class="h-32 w-auto mb-6 animate-float" />
            <h1 class="text-5xl md:text-7xl font-extrabold leading-tight drop-shadow-2xl">
              SERVICIOS<br>
              <span class="text-white animate-text-glow">VAESTRA</span>
            </h1>
            <p class="text-xl md:text-2xl text-red-50 leading-relaxed drop-shadow-lg">
              Soluciones industriales y refacciones de alta calidad desde <span class="font-bold text-white">2013</span>
            </p>
            <button 
              @click="openWhatsApp" 
              class="group relative inline-flex items-center gap-3 bg-gradient-to-r from-green-500 to-green-600 hover:from-green-600 hover:to-green-700 text-white px-8 py-4 rounded-full font-bold text-lg transition-all duration-300 transform hover:scale-105 hover:shadow-2xl hover:shadow-green-500/50"
            >
              <svg class="w-6 h-6 animate-pulse" fill="currentColor" viewBox="0 0 24 24">
                <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/>
              </svg>
              Contactar por WhatsApp
            </button>
          </div>
        </div>

        <!-- Right side - Image Carousel with Diagonal Clip -->
        <div class="hidden lg:block absolute right-0 top-0 bottom-0 w-1/2 overflow-hidden diagonal-clip">
          <div class="relative h-full">
            <TransitionGroup name="hero-carousel">
              <div
                v-for="(img, index) in heroImages"
                v-show="index === currentHeroImage"
                :key="img"
                class="absolute inset-0"
              >
                <img
                  :src="img"
                  alt="Hero Image"
                  class="w-full h-full object-cover animate-ken-burns"
                />
              </div>
            </TransitionGroup>

            <!-- Gradient overlay -->
            <div class="absolute inset-0 bg-gradient-to-br from-black/20 to-transparent z-10"></div>
            
            <!-- Carousel indicators -->
            <div class="absolute bottom-8 right-8 flex gap-2 z-20">
              <button
                v-for="(_, index) in heroImages"
                :key="index"
                @click="currentHeroImage = index"
                class="w-3 h-3 rounded-full transition-all duration-300"
                :class="index === currentHeroImage ? 'bg-white scale-125' : 'bg-white/50 hover:bg-white/75'"
              ></button>
            </div>
          </div>
        </div>
      </div>

      <!-- Scroll indicator -->
      <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2 z-20 animate-bounce">
        <svg class="w-8 h-8 text-white/90" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path>
        </svg>
      </div>
    </section>

    <!-- Experiencia -->
    <section id="experiencia" class="relative py-32 overflow-hidden">
      <!-- Animated background -->
      <div class="absolute inset-0 bg-gradient-to-br from-slate-50 via-blue-50 to-slate-100"></div>
      <div class="absolute inset-0 opacity-5">
        <div class="absolute top-1/4 left-1/4 w-96 h-96 bg-blue-500 rounded-full blur-3xl animate-blob"></div>
        <div class="absolute top-1/3 right-1/4 w-96 h-96 bg-red-500 rounded-full blur-3xl animate-blob animation-delay-2000"></div>
        <div class="absolute bottom-1/4 left-1/3 w-96 h-96 bg-purple-500 rounded-full blur-3xl animate-blob animation-delay-4000"></div>
      </div>
      
      <div class="relative max-w-5xl mx-auto px-4 text-center">
        <div class="inline-block mb-6">
          <span class="px-6 py-2 bg-gradient-to-r from-blue-600 to-red-600 text-white rounded-full text-sm font-bold uppercase tracking-wider shadow-lg animate-pulse-slow">
            Trayectoria
          </span>
        </div>
        <h2 class="text-4xl md:text-6xl font-black text-transparent bg-clip-text bg-gradient-to-r from-blue-900 via-blue-700 to-red-700 mb-8 animate-fade-in">
          12 años de experiencia<br>en el mercado
        </h2>
        <p class="text-xl md:text-2xl text-gray-700 leading-relaxed max-w-4xl mx-auto">
          En <span class="font-bold text-blue-900">Servicios Vaestra</span> hemos consolidado nuestra presencia en la industria metalmecánica gracias a la confianza de nuestros clientes. 
          Nos especializamos en proveer <span class="font-bold text-red-700">refacciones y soluciones industriales de alta calidad</span>, respaldados por equipos modernos y alianzas con marcas líderes. 
          Nuestro compromiso es seguir innovando para ofrecer a cada cliente la seguridad y eficiencia que necesita en sus procesos.
        </p>
        
        <!-- Stats -->
        <div class="mt-16 grid grid-cols-1 md:grid-cols-3 gap-8">
          <div class="group p-8 bg-white/80 backdrop-blur-sm rounded-2xl shadow-xl hover:shadow-2xl transition-all duration-300 hover:scale-105 border border-blue-100">
            <div class="text-5xl font-black text-transparent bg-clip-text bg-gradient-to-br from-blue-600 to-blue-800 mb-2">12+</div>
            <div class="text-gray-700 font-semibold text-lg">Años de Experiencia</div>
          </div>
          <div class="group p-8 bg-white/80 backdrop-blur-sm rounded-2xl shadow-xl hover:shadow-2xl transition-all duration-300 hover:scale-105 border border-red-100">
            <div class="text-5xl font-black text-transparent bg-clip-text bg-gradient-to-br from-red-600 to-red-800 mb-2">100+</div>
            <div class="text-gray-700 font-semibold text-lg">Clientes Satisfechos</div>
          </div>
          <div class="group p-8 bg-white/80 backdrop-blur-sm rounded-2xl shadow-xl hover:shadow-2xl transition-all duration-300 hover:scale-105 border border-purple-100">
            <div class="text-5xl font-black text-transparent bg-clip-text bg-gradient-to-br from-purple-600 to-purple-800 mb-2">24/7</div>
            <div class="text-gray-700 font-semibold text-lg">Soporte Disponible</div>
          </div>
        </div>
      </div>
    </section>

    <!-- Clientes -->
    <section id="clientes" class="relative py-32 bg-gradient-to-br from-white via-gray-50 to-white overflow-hidden">
      <div class="absolute inset-0 opacity-5">
        <div class="absolute top-0 left-0 w-full h-1 bg-gradient-to-r from-transparent via-blue-500 to-transparent animate-slide-horizontal"></div>
      </div>
      
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <div class="inline-block mb-6">
          <span class="px-6 py-2 bg-gradient-to-r from-blue-600 to-purple-600 text-white rounded-full text-sm font-bold uppercase tracking-wider shadow-lg">
            Confianza
          </span>
        </div>
        <h2 class="text-4xl md:text-6xl font-black text-transparent bg-clip-text bg-gradient-to-r from-gray-900 via-blue-800 to-gray-900 mb-6">
          Nuestros Clientes
        </h2>
        <p class="text-lg text-gray-600 mb-16 max-w-2xl mx-auto">
          Empresas líderes que confían en nuestras soluciones industriales
        </p>
        
        <div class="relative w-full overflow-hidden py-8">
          <!-- Gradient overlays -->
          <div class="absolute left-0 top-0 bottom-0 w-32 bg-gradient-to-r from-white to-transparent z-10"></div>
          <div class="absolute right-0 top-0 bottom-0 w-32 bg-gradient-to-l from-white to-transparent z-10"></div>
          
          <div class="flex animate-scroll-fast">
            <div
              v-for="(cliente, i) in [...clientes, ...clientes, ...clientes]"
              :key="i"
              class="flex-none w-80 px-4"
            >
              <div class="group bg-white shadow-lg hover:shadow-2xl rounded-2xl p-8 flex items-center justify-center h-64 transition-all duration-300 hover:scale-105 border-2 border-transparent hover:border-blue-200">
                <img
                  :src="cliente"
                  alt="Cliente"
                  class="max-h-48 max-w-full object-contain transition-transform duration-300 group-hover:scale-110 filter grayscale group-hover:grayscale-0"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Distribuidores -->
    <section id="distribuidores" class="relative py-32 overflow-hidden">
      <!-- Animated gradient background -->
      <div class="absolute inset-0 bg-gradient-to-br from-blue-950 via-purple-900 to-red-900 animate-gradient-shift"></div>
      <div class="absolute inset-0 opacity-20">
        <div class="absolute top-0 right-0 w-96 h-96 bg-pink-500 rounded-full blur-3xl animate-blob"></div>
        <div class="absolute bottom-0 left-0 w-96 h-96 bg-blue-500 rounded-full blur-3xl animate-blob animation-delay-2000"></div>
      </div>
      
      <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <div class="inline-block mb-6">
          <span class="px-6 py-2 bg-white/20 backdrop-blur-md text-white rounded-full text-sm font-bold uppercase tracking-wider shadow-lg border border-white/30">
            Alianzas
          </span>
        </div>
        <h2 class="text-4xl md:text-6xl font-black text-white mb-6 drop-shadow-2xl">
          Distribuidores Autorizados
        </h2>
        <p class="text-lg text-blue-100 mb-16 max-w-2xl mx-auto">
          Respaldados por las marcas más confiables de la industria
        </p>
        
        <div class="relative w-full overflow-hidden py-12">
          <!-- Gradient overlays -->
          <div class="absolute left-0 top-0 bottom-0 w-32 bg-gradient-to-r from-blue-950 to-transparent z-10"></div>
          <div class="absolute right-0 top-0 bottom-0 w-32 bg-gradient-to-l from-red-900 to-transparent z-10"></div>
          
          <div class="flex animate-scroll-medium">
            <div
              v-for="(dist, i) in [...distribuidores, ...distribuidores, ...distribuidores]"
              :key="i"
              class="flex-none w-96 px-6"
            >
              <div class="group bg-white/10 backdrop-blur-md hover:bg-white/20 rounded-2xl p-10 flex items-center justify-center h-48 transition-all duration-300 hover:scale-110 hover:shadow-2xl hover:shadow-white/20 border border-white/20">
                <img
                  :src="dist"
                  alt="Distribuidor"
                  class="max-h-32 max-w-full object-contain transition-all duration-300 group-hover:scale-110 brightness-0 invert"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Equipo -->
    <section id="equipo" class="relative py-32 bg-gradient-to-br from-slate-900 via-gray-900 to-slate-800 overflow-hidden">
      <div class="absolute inset-0 opacity-10">
        <div class="absolute top-1/4 right-1/4 w-96 h-96 bg-blue-500 rounded-full blur-3xl animate-blob"></div>
        <div class="absolute bottom-1/4 left-1/4 w-96 h-96 bg-red-500 rounded-full blur-3xl animate-blob animation-delay-2000"></div>
      </div>
      
      <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <div class="inline-block mb-6">
            <span class="px-6 py-2 bg-gradient-to-r from-red-600 to-orange-600 text-white rounded-full text-sm font-bold uppercase tracking-wider shadow-lg">
              Tecnología
            </span>
          </div>
          <h2 class="text-4xl md:text-6xl font-black text-white mb-6 drop-shadow-2xl">
            Nuestro Equipo Industrial
          </h2>
          <p class="text-lg text-gray-300 max-w-2xl mx-auto">
            Maquinaria de última generación para garantizar la máxima calidad y precisión
          </p>
        </div>
        
        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
          <div class="group bg-white/5 backdrop-blur-sm hover:bg-white/10 rounded-2xl p-6 transition-all duration-300 hover:scale-105 hover:shadow-2xl border border-white/10">
            <div class="text-4xl mb-4">🔧</div>
            <h3 class="text-xl font-bold text-white mb-2">Dobladora de lámina</h3>
            <p class="text-gray-400">Para calibre 3/16</p>
          </div>
          
          <div class="group bg-white/5 backdrop-blur-sm hover:bg-white/10 rounded-2xl p-6 transition-all duration-300 hover:scale-105 hover:shadow-2xl border border-white/10">
            <div class="text-4xl mb-4">⚙️</div>
            <h3 class="text-xl font-bold text-white mb-2">Roladora de lámina</h3>
            <p class="text-gray-400">Calibre 3/16</p>
          </div>
          
          <div class="group bg-white/5 backdrop-blur-sm hover:bg-white/10 rounded-2xl p-6 transition-all duration-300 hover:scale-105 hover:shadow-2xl border border-white/10">
            <div class="text-4xl mb-4">🔩</div>
            <h3 class="text-xl font-bold text-white mb-2">Dobladora de tubo</h3>
            <p class="text-gray-400">Alta precisión</p>
          </div>
          
          <div class="group bg-white/5 backdrop-blur-sm hover:bg-white/10 rounded-2xl p-6 transition-all duration-300 hover:scale-105 hover:shadow-2xl border border-white/10">
            <div class="text-4xl mb-4">🛠️</div>
            <h3 class="text-xl font-bold text-white mb-2">Torno convencional</h3>
            <p class="text-gray-400">1 metro entre puntos</p>
          </div>
          
          <div class="group bg-white/5 backdrop-blur-sm hover:bg-white/10 rounded-2xl p-6 transition-all duration-300 hover:scale-105 hover:shadow-2xl border border-white/10">
            <div class="text-4xl mb-4">⚡</div>
            <h3 class="text-xl font-bold text-white mb-2">Fresadora</h3>
            <p class="text-gray-400">Mecanizado de precisión</p>
          </div>
          
          <div class="group bg-white/5 backdrop-blur-sm hover:bg-white/10 rounded-2xl p-6 transition-all duration-300 hover:scale-105 hover:shadow-2xl border border-white/10">
            <div class="text-4xl mb-4">💎</div>
            <h3 class="text-xl font-bold text-white mb-2">Rectificadora</h3>
            <p class="text-gray-400">Acabado perfecto</p>
          </div>
          
          <div class="group bg-white/5 backdrop-blur-sm hover:bg-white/10 rounded-2xl p-6 transition-all duration-300 hover:scale-105 hover:shadow-2xl border border-white/10">
            <div class="text-4xl mb-4">🔥</div>
            <h3 class="text-xl font-bold text-white mb-2">Soldadura</h3>
            <p class="text-gray-400">MIG, TIG y punteadora</p>
          </div>
          
          <div class="group bg-white/5 backdrop-blur-sm hover:bg-white/10 rounded-2xl p-6 transition-all duration-300 hover:scale-105 hover:shadow-2xl border border-white/10">
            <div class="text-4xl mb-4">✨</div>
            <h3 class="text-xl font-bold text-white mb-2">Grabadora láser</h3>
            <p class="text-gray-400">Fibra y UV</p>
          </div>
          
          <div class="group bg-white/5 backdrop-blur-sm hover:bg-white/10 rounded-2xl p-6 transition-all duration-300 hover:scale-105 hover:shadow-2xl border border-white/10">
            <div class="text-4xl mb-4">🖨️</div>
            <h3 class="text-xl font-bold text-white mb-2">Impresora 3D</h3>
            <p class="text-gray-400">Prototipado rápido</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Contacto -->
    <section id="contacto" class="relative py-32 overflow-hidden">
      <div class="absolute inset-0 bg-gradient-to-br from-gray-950 via-blue-950 to-gray-900"></div>
      <div class="absolute inset-0 opacity-20">
        <div class="absolute top-1/2 left-1/2 w-96 h-96 bg-blue-500 rounded-full blur-3xl animate-blob"></div>
      </div>
      
      <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <div class="inline-block mb-6">
            <span class="px-6 py-2 bg-gradient-to-r from-green-600 to-emerald-600 text-white rounded-full text-sm font-bold uppercase tracking-wider shadow-lg">
              Conecta con nosotros
            </span>
          </div>
          <h2 class="text-4xl md:text-6xl font-black text-white mb-6 drop-shadow-2xl">
            Contáctanos
          </h2>
          <p class="text-lg text-gray-300 max-w-2xl mx-auto">
            Estamos listos para ayudarte con tus proyectos industriales
          </p>
        </div>
        
        <div class="grid md:grid-cols-2 gap-12 max-w-5xl mx-auto">
          <div class="space-y-8">
            <div class="group flex items-start gap-4 p-6 bg-white/5 backdrop-blur-sm rounded-2xl hover:bg-white/10 transition-all duration-300 border border-white/10">
              <div class="flex-shrink-0 w-12 h-12 bg-gradient-to-br from-blue-500 to-blue-600 rounded-full flex items-center justify-center text-2xl">
                📧
              </div>
              <div>
                <h3 class="text-xl font-bold text-white mb-2">Email</h3>
                <a href="mailto:sales@vaestra.solutions" class="text-blue-300 hover:text-blue-200 transition">
                  sales@vaestra.solutions
                </a>
              </div>
            </div>
            
            <div class="group flex items-start gap-4 p-6 bg-white/5 backdrop-blur-sm rounded-2xl hover:bg-white/10 transition-all duration-300 border border-white/10">
              <div class="flex-shrink-0 w-12 h-12 bg-gradient-to-br from-green-500 to-green-600 rounded-full flex items-center justify-center text-2xl">
                📞
              </div>
              <div>
                <h3 class="text-xl font-bold text-white mb-2">Teléfono</h3>
                <a href="tel:4422395074" class="text-green-300 hover:text-green-200 transition">
                  442 239 5074
                </a>
              </div>
            </div>
            
            <div class="group flex items-start gap-4 p-6 bg-white/5 backdrop-blur-sm rounded-2xl hover:bg-white/10 transition-all duration-300 border border-white/10">
              <div class="flex-shrink-0 w-12 h-12 bg-gradient-to-br from-red-500 to-red-600 rounded-full flex items-center justify-center text-2xl">
                📍
              </div>
              <div>
                <h3 class="text-xl font-bold text-white mb-2">Ubicación</h3>
                <p class="text-gray-300">Querétaro, México</p>
              </div>
            </div>
          </div>
          
          <div class="bg-gradient-to-br from-white/10 to-white/5 backdrop-blur-md p-10 rounded-3xl shadow-2xl border border-white/20">
            <h3 class="text-2xl font-bold text-white mb-6">Mensaje Directo</h3>
            <p class="text-gray-300 mb-8">
              Contáctanos directamente por WhatsApp para una respuesta inmediata
            </p>
            <button 
              @click="openWhatsApp" 
              class="group relative w-full inline-flex items-center justify-center gap-3 bg-gradient-to-r from-green-500 to-green-600 hover:from-green-600 hover:to-green-700 text-white px-8 py-5 rounded-full font-bold text-lg transition-all duration-300 transform hover:scale-105 hover:shadow-2xl hover:shadow-green-500/50"
            >
              <svg class="w-7 h-7" fill="currentColor" viewBox="0 0 24 24">
                <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/>
              </svg>
              Escribir por WhatsApp
            </button>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="bg-gray-950 text-white py-8 text-center">
      <p class="text-gray-400">&copy; 2025 Servicios Vaestra. Todos los derechos reservados.</p>
    </footer>
  </div>
</template>

<style scoped>
/* Diagonal Red Background for Left Section */
.diagonal-red-bg {
  background: linear-gradient(135deg, #dc2626 0%, #b91c1c 50%, #991b1b 100%);
  position: relative;
}

.diagonal-red-bg::after {
  content: '';
  position: absolute;
  top: 0;
  right: -50px;
  bottom: 0;
  width: 100px;
  background: linear-gradient(135deg, #dc2626 0%, #b91c1c 50%, #991b1b 100%);
  transform: skewX(-3deg);
  z-index: -1;
}

/* Diagonal Clip for Right Section */
.diagonal-clip {
  clip-path: polygon(5% 0, 100% 0, 100% 100%, 0 100%);
}

/* Text glow animation */
@keyframes text-glow {
  0%, 100% {
    text-shadow: 0 0 20px rgba(255, 255, 255, 0.5), 0 0 30px rgba(255, 255, 255, 0.3);
  }
  50% {
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.8), 0 0 40px rgba(255, 255, 255, 0.5);
  }
}
.animate-text-glow {
  animation: text-glow 3s ease-in-out infinite;
}

/* Hero Carousel Transitions */
.hero-carousel-enter-active {
  transition: all 0.8s ease;
}
.hero-carousel-leave-active {
  transition: all 0.8s ease;
}
.hero-carousel-enter-from {
  opacity: 0;
  transform: scale(1.1);
}
.hero-carousel-leave-to {
  opacity: 0;
  transform: scale(0.95);
}

/* Slide in from left */
@keyframes slide-in-left {
  from {
    opacity: 0;
    transform: translateX(-50px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}
.animate-slide-in-left {
  animation: slide-in-left 0.8s ease-out;
}

/* Floating animation for logo */
@keyframes float {
  0%, 100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-10px);
  }
}
.animate-float {
  animation: float 3s ease-in-out infinite;
}

/* Gradient text animation */
@keyframes gradient {
  0%, 100% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
}
.animate-gradient {
  background-size: 200% auto;
  animation: gradient 3s ease infinite;
}

/* Ken Burns effect for images */
@keyframes ken-burns {
  0% {
    transform: scale(1);
  }
  100% {
    transform: scale(1.1);
  }
}
.animate-ken-burns {
  animation: ken-burns 20s ease-in-out infinite alternate;
}

/* Pulse slow */
@keyframes pulse-slow {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: 0.7;
  }
}
.animate-pulse-slow {
  animation: pulse-slow 3s ease-in-out infinite;
}

/* Vertical slide animation */
@keyframes slide-vertical {
  0% {
    transform: translateY(-100%);
  }
  100% {
    transform: translateY(100%);
  }
}
.animate-slide-vertical {
  animation: slide-vertical 3s ease-in-out infinite;
}

/* Blob animation */
@keyframes blob {
  0%, 100% {
    transform: translate(0, 0) scale(1);
  }
  25% {
    transform: translate(20px, -20px) scale(1.1);
  }
  50% {
    transform: translate(-20px, 20px) scale(0.9);
  }
  75% {
    transform: translate(20px, 20px) scale(1.05);
  }
}
.animate-blob {
  animation: blob 10s ease-in-out infinite;
}
.animation-delay-2000 {
  animation-delay: 2s;
}
.animation-delay-4000 {
  animation-delay: 4s;
}

/* Fade in */
@keyframes fade-in {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
.animate-fade-in {
  animation: fade-in 1s ease-out;
}

/* Horizontal slide */
@keyframes slide-horizontal {
  0% {
    transform: translateX(-100%);
  }
  100% {
    transform: translateX(100%);
  }
}
.animate-slide-horizontal {
  animation: slide-horizontal 3s ease-in-out infinite;
}

/* Fast carousel scroll */
@keyframes scroll-fast {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(-33.333%);
  }
}
.animate-scroll-fast {
  display: flex;
  animation: scroll-fast 15s linear infinite;
}

/* Medium carousel scroll */
@keyframes scroll-medium {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(-33.333%);
  }
}
.animate-scroll-medium {
  display: flex;
  animation: scroll-medium 20s linear infinite;
}

/* Gradient shift background */
@keyframes gradient-shift {
  0%, 100% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
}
.animate-gradient-shift {
  background-size: 200% 200%;
  animation: gradient-shift 15s ease infinite;
}

/* Smooth scrolling */
html {
  scroll-behavior: smooth;
}

/* Custom scrollbar */
::-webkit-scrollbar {
  width: 10px;
}
::-webkit-scrollbar-track {
  background: #1a1a1a;
}
::-webkit-scrollbar-thumb {
  background: linear-gradient(to bottom, #3b82f6, #ef4444);
  border-radius: 5px;
}
::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(to bottom, #2563eb, #dc2626);
}
</style>
