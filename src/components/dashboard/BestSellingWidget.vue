<script setup>
import { ref, onMounted } from 'vue';


const technologies = ref([
    { category: 'Backend', name: 'Laravel', percentage: 100, color: 'bg-red-500', icon: 'pi pi-server', image: 'demo/images/Tecnologias/laravel.png' },
    { category: 'Backend', name: 'Java Spring Boot', percentage: 80, color: 'bg-blue-500', icon: 'pi pi-server', image: 'demo/images/Tecnologias/java.png' },
    { category: 'Backend', name: '.Net Core', percentage: 80, color: 'bg-purple-500', icon: 'pi pi-server', image: 'demo/images/Tecnologias/net.png'},
    { category: 'Backend', name: 'Python', percentage: 80, color: 'bg-yellow-500', icon: 'pi pi-server', image: 'demo/images/Tecnologias/python.svg'},
    { category: 'Frontend', name: 'Next.js', percentage: 75, color: 'bg-gray-500', icon: 'pi pi-desktop', image: 'demo/images/Tecnologias/next.png'} ,
    { category: 'Frontend', name: 'Vue', percentage: 90, color: 'bg-green-500', icon: 'pi pi-desktop', image: 'demo/images/Tecnologias/vue.png'} ,
    { category: 'Frontend', name: 'Angular', percentage: 75, color: 'bg-red-600', icon: 'pi pi-desktop', image: 'demo/images/Tecnologias/angular.png'} ,
    { category: 'Frontend', name: 'Blade', percentage: 90, color: 'bg-blue-600', icon: 'pi pi-desktop', image: 'demo/images/Tecnologias/blade.jpg'} ,
    { category: 'Frontend', name: 'Svelte', percentage: 90, color: 'bg-orange-500', icon: 'pi pi-desktop', image: 'demo/images/Tecnologias/svelte.png'} ,
    { category: 'Base de Datos', name: 'MySQL', percentage: 100, color: 'bg-blue-700', icon: 'pi pi-database', image: 'demo/images/Tecnologias/mysql.svg'} ,
    { category: 'Base de Datos', name: 'PostgreSQL', percentage: 100, color: 'bg-indigo-500', icon: 'pi pi-database', image: 'demo/images/Tecnologias/postgres.png'} ,
    { category: 'Base de Datos', name: 'MongoDB', percentage: 80, color: 'bg-green-700', icon: 'pi pi-database', image: 'demo/images/Tecnologias/mongo.png'} ,
    { category: 'Base de Datos', name: 'Firebase', percentage: 90, color: 'bg-yellow-600', icon: 'pi pi-database', image: 'demo/images/Tecnologias/firebase.webp'} ,
    { category: 'Cloud', name: 'AWS', percentage: 90, color: 'bg-orange-600', icon: 'pi pi-cloud', image: 'demo/images/Tecnologias/aws.webp'} ,
    { category: 'Cloud', name: 'Google Cloud', percentage: 75, color: 'bg-blue-400', icon: 'pi pi-cloud', image: 'demo/images/Tecnologias/cloud.png'} ,
    { category: 'Virtualización', name: 'VMWare', percentage: 90, color: 'bg-gray-700', icon: 'pi pi-box', image: 'demo/images/Tecnologias/vmware.svg.png'} ,
    { category: 'Virtualización', name: 'Virtual Box', percentage: 90, color: 'bg-blue-900', icon: 'pi pi-box', image: 'demo/images/Tecnologias/virtualbox.png'} ,
    { category: 'Virtualización', name: 'Vagrant', percentage: 80, color: 'bg-purple-700', icon: 'pi pi-box', image: 'demo/images/Tecnologias/vagrant.png'} ,
    { category: 'Redes', name: 'Cisco', percentage: 90, color: 'bg-red-500', icon: 'pi pi-sitemap', image: 'demo/images/Tecnologias/cisco.png'} ,
    { category: 'Redes', name: 'GNS3', percentage: 90, color: 'bg-green-500', icon: 'pi pi-sitemap', image: 'demo/images/Tecnologias/gns3.jpg'} ,
]);
const visibleTechs = ref({});

onMounted(() => {
    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                visibleTechs.value[entry.target.dataset.name] = true;
            }
        });
    }, { threshold: 0.3 });

    document.querySelectorAll('.progress-bar').forEach(el => {
        observer.observe(el);
    });
});
</script>

<template>
    <div class="card">
        <div class="flex items-center justify-between mb-6">
            <div class="font-semibold text-xl">Dominio de Tecnologías</div>

        </div>

        <!-- Grid de dos columnas -->
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
            <div v-for="(group, index) in [...new Set(technologies.map(t => t.category))]" :key="index" class="card border border-gray-300 dark:border-gray-700 p-4 rounded-md">
                <h2 class="text-xl font-bold text-gray-900 dark:text-gray-200 mb-4">{{ group }}</h2>
                <ul class="list-none p-0 m-0">
                    <li v-for="tech in technologies.filter(t => t.category === group)" :key="tech.name"
                        class="flex flex-col md:flex-row md:items-center md:justify-between mb-4">
                        <div class="flex items-center">
                            <img v-if="tech.image" :src="tech.image" alt="logo"
                                 class="w-8 h-8 mr-3 rounded-md object-contain">
                            <span class="text-gray-900 dark:text-gray-100 font-medium">{{ tech.name }}</span>
                        </div>
                        <div class="mt-2 md:mt-0 flex items-center w-full md:w-auto">
                            <div class="relative w-full md:w-48 h-3 bg-gray-300 dark:bg-gray-600 rounded-lg overflow-hidden">
                                <div
                                    class="progress-bar h-full transition-all duration-1000 ease-in-out"
                                    :class="[tech.color]"
                                    :style="{ width: visibleTechs[tech.name] ? tech.percentage + '%' : '0%' }"
                                    :data-name="tech.name">
                                </div>
                            </div>
                            <span class="ml-4 font-medium text-gray-700 dark:text-gray-300">{{ tech.percentage }}%</span>
                        </div>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>
