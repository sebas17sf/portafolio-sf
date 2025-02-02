<script setup>
import BestSellingWidget from '@/components/dashboard/BestSellingWidget.vue';
import NotificationsWidget from '@/components/dashboard/NotificationsWidget.vue';
////import RecentSalesWidget from '@/components/dashboard/RecentSalesWidget.vue';
/////import RevenueStreamWidget from '@/components/dashboard/RevenueStreamWidget.vue';
import StatsWidget from '@/components/dashboard/StatsWidget.vue';
import ToolsDeveloped from '@/components/dashboard/ToolsDeveloped.vue';
</script>

<template>
    <div class="grid grid-cols-12 gap-8">
        <StatsWidget />

        <div class="col-span-12">
            <BestSellingWidget />
        </div>
        <div class="col-span-12 md:col-span-6">
            <ToolsDeveloped />
        </div>
        <div class="col-span-12 md:col-span-6">
            <NotificationsWidget />
        </div>
    </div>
</template>
