<script setup>
import { ref } from 'vue';

import AppMenuItem from './AppMenuItem.vue';

const model = ref([
    {
        label: 'Home',
        items: [
            { label: 'Desarrollador', icon: 'pi pi-fw pi-user', to: '/' },
            { label: 'Tecnologias', icon: 'pi pi-fw pi-cog', to: '/inicio' },
         ]
    },

    {
        label: 'Cursos',
        icon: 'pi pi-fw pi-book',
        items: [
            { label: 'Incripciones', icon: 'pi pi-fw pi-id-card', to: '/cursos/lista' },
        ]
    },

    {
        label: 'Informacion',
        items: [
            {
                label: 'CV',
                icon: 'pi pi-fw pi-book',
                to: '/documentation'
            },
            {
                label: 'Repositorio',
                icon: 'pi pi-fw pi-github',
                url: 'https://github.com/sebas17sf?tab=repositories',
                target: '_blank'
            }
        ]
    }
]);
</script>

<template>
    <ul class="layout-menu">
        <template v-for="(item, i) in model" :key="item">
            <app-menu-item v-if="!item.separator" :item="item" :index="i"></app-menu-item>
            <li v-if="item.separator" class="menu-separator"></li>
        </template>
    </ul>
</template>

<style lang="scss" scoped></style>
