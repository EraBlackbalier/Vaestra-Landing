<script setup lang="ts">
import { ref, onMounted } from 'vue'

// Tipos para las rutas de imágenes
type ImagePath = `/images/${string}`

const isVisible = ref(false)

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

// Logo path con type safety
const logoPath: ImagePath = '/images/logo.png'

onMounted(() => {
  setTimeout(() => {
    isVisible.value = true
  }, 100)
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

    <!-- Hero -->
    <section id="inicio" class="pt-16 bg-gradient-to-br from-blue-900 via-blue-700 to-red-700 text-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-24 text-center space-y-6" :class="{ 'animate-fade-in-up': isVisible }">
        <img :src="logoPath" alt="Logo Vaestra" class="mx-auto h-28 w-auto mb-6" />
        <h1 class="text-5xl md:text-6xl font-bold">
          SERVICIOS <span class="text-red-300">VAESTRA</span>
        </h1>
        <p class="text-xl md:text-2xl max-w-3xl mx-auto text-blue-100">
          Somos una empresa comercializadora de refacciones para la industria en general y prestadora de servicios metalmecánicos desde 2013.
        </p>
        <button @click="openWhatsApp" class="bg-green-500 hover:bg-green-600 text-white px-8 py-3 rounded-lg font-semibold transition transform hover:scale-105">
          Contactar por WhatsApp
        </button>
      </div>
    </section>

    <!-- Experiencia -->
    <section id="experiencia" class="py-24 bg-gray-100 text-center">
      <div class="max-w-4xl mx-auto px-4">
        <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-6">12 años de experiencia en el mercado</h2>
        <p class="text-lg text-gray-700">
          En Servicios Vaestra hemos consolidado nuestra presencia en la industria metalmecánica gracias a la confianza de nuestros clientes. 
          Nos especializamos en proveer refacciones y soluciones industriales de alta calidad, respaldados por equipos modernos y alianzas con marcas líderes. 
          Nuestro compromiso es seguir innovando para ofrecer a cada cliente la seguridad y eficiencia que necesita en sus procesos.
        </p>
      </div>
    </section>

    <!-- Clientes -->
    <section id="clientes" class="py-24 bg-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center overflow-hidden">
        <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-12">Nuestros Clientes</h2>
        <div class="relative w-full overflow-hidden">
          <div class="flex animate-scroll">
            <div
              v-for="(cliente, i) in [...clientes, ...clientes]"
              :key="i"
              class="flex-none w-1/3 p-6"
            >
              <div class="bg-white shadow rounded-lg flex items-center justify-center h-60">
                <img
                  :src="cliente"
                  alt="Cliente"
                  class="max-h-52 max-w-full object-contain"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Distribuidores -->
    <section id="distribuidores" class="py-24 bg-gradient-to-r from-blue-900 to-red-700 text-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center overflow-hidden">
        <h2 class="text-3xl md:text-4xl font-bold mb-12">Distribuidores Autorizados</h2>
        <div class="relative w-full overflow-hidden">
          <div class="flex animate-scroll">
            <div
              v-for="(dist, i) in [...distribuidores, ...distribuidores]"
              :key="i"
              class="flex-none w-1/3 p-6"
            >
              <div class="flex items-center justify-center h-32">
                <img
                  :src="dist"
                  alt="Distribuidor"
                  class="max-h-28 max-w-full object-contain"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Equipo -->
    <section id="equipo" class="py-24 bg-gray-100">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-8 text-center">Nuestro Equipo</h2>
        <ul class="grid md:grid-cols-2 gap-6 text-lg text-gray-700">
          <li>✔ Dobladora de lámina para calibre 3/16</li>
          <li>✔ Roladora de lámina 3/16</li>
          <li>✔ Dobladora de tubo</li>
          <li>✔ Torno convencional de 1 metro entre puntos</li>
          <li>✔ Fresadora</li>
          <li>✔ Rectificadora</li>
          <li>✔ Soldadura MIG, TIG y punteadora</li>
          <li>✔ Grabadora láser de fibra y UV</li>
          <li>✔ Impresora 3D</li>
        </ul>
      </div>
    </section>

    <!-- Contacto -->
    <section id="contacto" class="py-24 bg-gray-900 text-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 grid md:grid-cols-2 gap-12">
        <div>
          <h2 class="text-3xl md:text-4xl font-bold mb-6">Contáctanos</h2>
          <p class="mb-4">📧 sales@vaestra.solutions</p>
          <p class="mb-4">📞 442 239 5074</p>
        </div>
        <div class="bg-white text-gray-900 p-8 rounded-lg shadow">
          <h3 class="text-xl font-semibold mb-4">Mensaje Directo</h3>
          <button @click="openWhatsApp" class="bg-green-500 hover:bg-green-600 text-white px-6 py-3 rounded-lg font-semibold transition w-full">
            Escribir por WhatsApp
          </button>
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
@keyframes fade-in-up {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
.animate-fade-in-up {
  animation: fade-in-up 0.8s ease-out;
}

@keyframes scroll {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(-50%);
  }
}
.animate-scroll {
  display: flex;
  animation: scroll 20s linear infinite;
}
</style>
