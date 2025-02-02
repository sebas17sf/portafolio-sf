<script setup>
const tools = [
    { name: "Visual Studio", image: "demo/images/Herramientas/visual.35_icon.svg.png" },
    { name: "Rider", image: "demo/images/Herramientas/rider.png" },
    { name: "IntelliJ IDEA", image: "demo/images/Herramientas/intelij.svg.png" },
    { name: "PHPStorm", image: "demo/images/Herramientas/php.png" },
    { name: "Docker", image: "demo/images/Herramientas/docker.png" },
    { name: "HeidiSQL", image: "demo/images/Herramientas/heidi.png" },
    { name: "Postman", image: "demo/images/Herramientas/postman.webp" },
    { name: "Android Studio", image: "demo/images/Herramientas/studio.png" },
    { name: "Insomnia", image: "demo/images/Herramientas/insomnia.svg" },
    { name: "Google Cloud", image: "demo/images/Herramientas/cloud.webp" }
];
</script>

<template>
    <div class="card p-6">
        <div class="mb-6 text-center">
            <h2 class="font-semibold text-2xl text-gray-800 dark:text-gray-200">Herramientas de Desarrollo</h2>
        </div>

        <!-- Grid de 3 columnas -->
        <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6">
            <div v-for="tool in tools" :key="tool.name" class="card border border-gray-300 dark:border-gray-700 p-4 rounded-md flex flex-col items-center">
                <img :src="tool.image" :alt="tool.name" class="w-32 h-32 object-contain mb-4">
                <span class="font-medium text-gray-900 dark:text-gray-100">{{ tool.name }}</span>
            </div>
        </div>
    </div>
</template>
