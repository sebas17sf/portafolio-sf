<script setup>
import { ref, onMounted } from 'vue';

const education = ref([
    {
        institution: 'Unidad Educativa Fe y Alegría',
        date: '2007 - 2011',
        icon: 'pi pi-book',
        color: '#007BFF',
        description: 'Educación primaria en la Unidad Educativa Fe y Alegría, una institución comprometida con la formación de valores y educación de calidad.',
    },
    {
        institution: 'Unidad Educativa Santo Domingo',
        date: '2012 - 2018',
        icon: 'pi pi-graduation-cap',
        color: '#673AB7',
        description: 'Educación secundaria en la Unidad Educativa Santo Domingo, destacando en ciencias y tecnología.',
    },
    {
        institution: 'Universidad de las Fuerzas Armadas ESPE',
        date: '2020 - 2024',
        icon: 'pi pi-globe',
        color: '#FF9800',
        description: 'Ingeniería en Tecnologías de la Información en la Universidad de las Fuerzas Armadas ESPE, con enfoque en innovación y desarrollo tecnológico.',
    }
]);

const workExperience = ref([
    {
        company: 'CY Distribuidora Nacional',
        date: '2020 - 2022',
        icon: 'pi pi-database',
        color: '#4CAF50',
        description: 'Administración y mantenimiento de bases de datos relacionales para el sistema de inventario de medicamentos, optimización de consultas SQL y mejora de la seguridad en los accesos a la información.',
    },
    {
        company: 'New Plast - Sistema de reciclaje de plástico bello',
        date: '2021 - 2022',
        icon: 'pi pi-shield',
        color: '#FF9800',
        description: 'Desarrollo e implementación de un sistema automatizado para el reciclaje de botellas plásticas. Integración con hardware IoT para la recolección de datos y generación de filamento para impresoras 3D.',
    },
    {
        company: 'Sistem Seguridad ESPE',
        date: '2022 - 2023',
        icon: 'pi pi-shield',
        color: '#673AB7',
        description: 'Mantenimiento y optimización del sistema de gestión de seguridad barrial, implementando algoritmos de detección de incidentes y monitoreo en tiempo real en Luz de América y la ESPE.',
    },
    {
        company: 'Anfibius Sistema Contable',
        date: '2022 - 2023',
        icon: 'pi pi-wallet',
        color: '#03A9F4',
        description: 'Desarrollo del módulo de gestión de restaurantes dentro del sistema contable, implementando manipulación avanzada de servicios REST API para la integración con puntos de venta (POS) y gestión de inventarios.',
    },
    {
        company: 'PERSEO SOFT',
        date: '2024 - 2025',
        icon: 'pi pi-code',
        color: '#E91E63',
        description: 'Diseño y desarrollo de un nuevo sistema contable basado en tecnologías modernas como Vue.js, Node.js y bases de datos NoSQL. Implementación de microservicios y despliegue en entornos de nube escalables.',
    },
]);

// Estado para controlar la visibilidad de los elementos
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
    <div class="grid grid-cols-12 gap-8">
        <!-- Sección de Educación -->
        <div class="col-span-full">
            <div class="card">
                <div class="text-primary font-medium text-3xl fade-in-section"
                     data-name="education-title"
                     :class="{ 'opacity-0 translate-y-4': !visibleItems['education-title'], 'transition-all duration-700 ease-in-out': true }">
                    Educación
                </div>
                <Timeline :value="education" align="alternate" class="customized-timeline">
                    <template #marker="slotProps">
                        <span class="flex w-8 h-8 items-center justify-center text-white rounded-full z-10 shadow-sm"
                              :style="{ backgroundColor: slotProps.item.color }">
                            <i :class="slotProps.item.icon"></i>
                        </span>
                    </template>
                    <template #content="slotProps">
                        <Card class="mt-4 fade-in-section"
                              :data-name="slotProps.item.institution"
                              :class="{ 'opacity-0 translate-y-4': !visibleItems[slotProps.item.institution], 'transition-all duration-700 ease-in-out': true }">
                            <template #title>
                                {{ slotProps.item.institution }}
                            </template>
                            <template #subtitle>
                                {{ slotProps.item.date }}
                            </template>
                            <template #content>
                                <p>{{ slotProps.item.description }}</p>
                            </template>
                        </Card>
                    </template>
                </Timeline>
            </div>
        </div>

        <!-- Sección de Experiencia Laboral -->
        <div class="col-span-full">
            <div class="card">
                <div class="text-primary font-medium text-3xl fade-in-section"
                     data-name="work-title"
                     :class="{ 'opacity-0 translate-y-4': !visibleItems['work-title'], 'transition-all duration-700 ease-in-out': true }">
                    Experiencia Laboral
                </div>
                <Timeline :value="workExperience" align="alternate" class="customized-timeline">
                    <template #marker="slotProps">
                        <span class="flex w-8 h-8 items-center justify-center text-white rounded-full z-10 shadow-sm"
                              :style="{ backgroundColor: slotProps.item.color }">
                            <i :class="slotProps.item.icon"></i>
                        </span>
                    </template>
                    <template #content="slotProps">
                        <Card class="mt-4 fade-in-section"
                              :data-name="slotProps.item.company"
                              :class="{ 'opacity-0 translate-y-4': !visibleItems[slotProps.item.company], 'transition-all duration-700 ease-in-out': true }">
                            <template #title>
                                {{ slotProps.item.company }}
                            </template>
                            <template #subtitle>
                                {{ slotProps.item.date }}
                            </template>
                            <template #content>
                                <p>{{ slotProps.item.description }}</p>
                            </template>
                        </Card>
                    </template>
                </Timeline>
            </div>
        </div>
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

.transition-all {
    transition-property: opacity, transform;
}
</style>
