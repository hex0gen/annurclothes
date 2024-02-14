<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import Welcome from '@/Components/Welcome.vue';
</script>

<template>
    <AppLayout title="Корзина">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Dashboard
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg">
                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Numquam doloremque voluptas accusantium facilis vitae, aspernatur, corporis aperiam iusto accusamus dolorum quaerat. Voluptate quae ea tempore sequi officia doloribus libero omnis!
                </div>
            </div>
        </div>
    </AppLayout>
</template>
