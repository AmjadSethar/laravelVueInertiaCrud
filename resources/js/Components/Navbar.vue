<template>
    <nav class="flex justify-between p-4 bg-gray-200">
        <div class="text-lg">
           <Link :href="route('home')" >Navbar</Link>
        </div>
        <div class="">
            <ul class="flex gap-x-4 me-auto mb-2 mb-lg-0">
                <li class="nav-item">
                    <Link class="text-dark" :href="route('home')">Home</Link>
                </li>
                <li class="nav-item">
                    <Link class="text-dark" :href="route('about')">About Us</Link>
                </li>
                <li class="nav-item">
                    <Link class="text-dark" :href="route('contact')">Contact Us</Link>
                </li>
                <!-- <li class="nav-item">
                    <Link class="text-dark" :href="route('products.index')">Products</Link>
                </li> -->
            </ul>
        </div>
    </nav>
</template>

<script setup>
import { Link } from "@inertiajs/vue3";
</script>