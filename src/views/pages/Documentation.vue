<template>
    <div class="card">
        <!-- Encabezado con icono -->
        <div class="flex items-center space-x-3 mb-4">
            <div class="flex items-center justify-center bg-blue-100 dark:bg-blue-400/10 rounded-border"
                 style="width: 2.5rem; height: 2.5rem">
                <!-- Icono (puedes cambiarlo por un SVG o icono de FontAwesome si usas) -->
                📄
            </div>
            <div class="font-semibold text-2xl text-gray-900 dark:text-white">Hoja de Vida</div>
        </div>

        <!-- Contenedor del PDF -->
        <div class="video-container border rounded-lg shadow-md bg-gray-100 dark:bg-gray-700">
            <iframe :src="cvUrl" type="application/pdf"></iframe>
        </div>

        <!-- Botón para descargar -->
        <div class="mt-4 flex justify-center">
            <Button label="Descargar CV" severity="secondary" raised @click="downloadCV" />
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            cvUrl: "/cv.pdf", // Ruta del archivo PDF en la carpeta public
        };
    }
};
</script>

<style lang="scss" scoped>
.video-container {
    position: relative;
    width: 100%;
    height: 500px; /* Altura fija para la vista previa */

    iframe {
        width: 100%;
        height: 100%;
        border: none;
    }
}
</style>
