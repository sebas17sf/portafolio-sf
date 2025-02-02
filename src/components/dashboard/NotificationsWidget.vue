<script setup>
import { ref } from 'vue';



</script>

<template>
    <div class="card">
        <div class="flex items-center justify-between mb-6">
            <div class="font-semibold text-xl">Actividades recientes</div>

        </div>

        <span class="block text-muted-color font-medium mb-4">HACE 1 AÑO</span>
        <ul class="p-0 mx-0 mt-0 mb-6 list-none">
            <li class="flex items-center py-2 border-b border-surface">
                <div class="w-12 h-12 flex items-center justify-center bg-blue-100 dark:bg-blue-400/10 rounded-full mr-4 shrink-0">
                    <i class="pi pi-code !text-xl text-blue-500"></i>
                </div>
                <span class="text-surface-900 dark:text-surface-0 leading-normal">
                    Hace 1 año culminó sus estudios profesionales.
                </span>
            </li>
        </ul>

        <span class="block text-muted-color font-medium mb-4">HACE 4 MESES</span>
        <ul class="p-0 m-0 list-none mb-6">
            <li class="flex items-center py-2 border-b border-surface">
                <div class="w-12 h-12 flex items-center justify-center bg-orange-100 dark:bg-orange-400/10 rounded-full mr-4 shrink-0">
                    <i class="pi pi-github !text-xl text-orange-500"></i>
                </div>
                <span class="text-surface-700 dark:text-surface-100 leading-normal">
                    Hace 4 meses actualizó su GitHub.
                </span>
            </li>
        </ul>

        <span class="block text-muted-color font-medium mb-4">HACE 2 SEMANAS</span>
        <ul class="p-0 m-0 list-none mb-6">
            <li class="flex items-center py-2 border-b border-surface">
                <div class="w-12 h-12 flex items-center justify-center bg-green-100 dark:bg-green-400/10 rounded-full mr-4 shrink-0">
                    <i class="pi pi-check !text-xl text-green-500"></i>
                </div>
                <span class="text-surface-900 dark:text-surface-0 leading-normal">
                    Hace 2 semanas entregó todos los proyectos que ayudaron a su universidad internamente.
                </span>
            </li>
        </ul>

        <span class="block text-muted-color font-medium mb-4">HACE 1 MES</span>
        <ul class="p-0 m-0 list-none mb-6">
            <li class="flex items-center py-2 border-b border-surface">
                <div class="w-12 h-12 flex items-center justify-center bg-purple-100 dark:bg-purple-400/10 rounded-full mr-4 shrink-0">
                    <i class="pi pi-star !text-xl text-purple-500"></i>
                </div>
                <span class="text-surface-900 dark:text-surface-0 leading-normal">
                    Hace 1 mes su artículo científico de Cloud personal está siendo revisado.
                </span>
            </li>
        </ul>

        <span class="block text-muted-color font-medium mb-4">LA SEMANA PASADA</span>
        <ul class="p-0 m-0 list-none">
            <li class="flex items-center py-2 border-b border-surface">
                <div class="w-12 h-12 flex items-center justify-center bg-red-100 dark:bg-red-400/10 rounded-full mr-4 shrink-0">
                    <i class="pi pi-users !text-xl text-red-500"></i>
                </div>
                <span class="text-surface-900 dark:text-surface-0 leading-normal">
                    Se planteó la idea de cursos gratuitos.
                </span>
            </li>
        </ul>
    </div>
</template>

