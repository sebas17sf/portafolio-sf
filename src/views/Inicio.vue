<script setup>
import { ref, onMounted } from 'vue';
import TimelineDoc from '@/views/uikit/TimelineDoc.vue';

const profile = {
    name: "Sebastian Jair Flores Cando",
    title: "Ingeniero en Tecnologías de la Información",
    image: "demo/images/Users/yo.jpg"
};

// Estado reactivo para controlar la visibilidad de los elementos
const visibleItems = ref({});

onMounted(() => {
    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                visibleItems.value[entry.target.dataset.name] = true;
            }
        });
    }, { threshold: 0.3 });

    document.querySelectorAll('.fade-in-section').forEach(el => {
        observer.observe(el);
    });
});
</script>

<template>
    <div class="card p-6 fade-in-section"
         data-name="profile-card"
         :class="{ 'opacity-0 translate-y-4': !visibleItems['profile-card'], 'transition-all duration-700 ease-in-out': true }">

        <!-- Tarjeta con estilos refinados -->
        <div class="col-span-12 md:col-span-8 lg:col-span-6 card shadow-lg rounded-lg border border-gray-300 dark:border-gray-700 overflow-hidden hover:shadow-2xl transition-all duration-500 text-gray-700 dark:text-gray-300">

            <!-- Contenido dividido en dos columnas en pantallas grandes, pero en móviles imagen primero -->
            <div class="flex flex-col-reverse md:grid md:grid-cols-2 gap-6 p-6 lg:p-12">

                <!-- Columna de imagen alineada a la derecha (pero primera en móviles) -->
                <div class="flex justify-center items-center fade-in-section"
                     data-name="profile-image"
                     :class="{ 'opacity-0 scale-90': !visibleItems['profile-image'], 'transition-all duration-700 ease-in-out': true }">
                    <img
                        :src="profile.image"
                        alt="Foto de perfil"
                        class="w-64 h-64 md:w-72 md:h-72 rounded-full object-cover border-4 border-gray-300 dark:border-gray-500 shadow-lg transform hover:scale-105 transition-all duration-300"
                    >
                </div>

                <!-- Columna de texto alineada a la izquierda -->
                <div class="self-center fade-in-section"
                     data-name="profile-text"
                     :class="{ 'opacity-0 translate-y-4': !visibleItems['profile-text'], 'transition-all duration-700 ease-in-out': true }">
                    <h1 class="text-primary font-medium text-4xl">¡Buen Día!</h1>
                    <p class="text-2xl font-semibold mb-2">
                        Te saluda <span class="text-primary font-medium">{{ profile.name }}</span>
                    </p>
                    <p class="text-primary font-medium">
                        {{ profile.title }}
                    </p>
                    <p class="text-lg leading-relaxed mt-4 text-justify">
                        Apasionado por la tecnología, la innovación y la resolución de problemas a través del desarrollo de software. Siempre buscando aprender y compartir conocimientos con la comunidad tecnológica.
                    </p>
                </div>

            </div>
        </div>
    </div>

    <!-- Sección de la Línea de Tiempo -->
    <div class="card p-6 fade-in-section">
        <TimelineDoc />
    </div>
</template>

<style lang="scss" scoped>
.fade-in-section {
    opacity: 1;
    transform: translateY(0);
}

.opacity-0 {
    opacity: 0;
}

.translate-y-4 {
    transform: translateY(1rem);
}

.scale-90 {
    transform: scale(0.9);
}

.transition-all {
    transition-property: opacity, transform;
}
</style>
