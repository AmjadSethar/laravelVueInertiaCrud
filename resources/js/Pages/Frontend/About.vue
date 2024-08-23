<template>
    <FrontendLayout>
        <Head title="About Us" />

        <h1>Hello This is {{title}} Page</h1>
    </FrontendLayout>
</template>

<script setup>

import FrontendLayout from '@/Layouts/FrontendLayout.vue';
import { Head } from '@inertiajs/vue3';

 defineProps({
    title: String
});
</script>