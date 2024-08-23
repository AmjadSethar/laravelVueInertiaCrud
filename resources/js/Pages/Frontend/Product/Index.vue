<template>
    <Head title="Products" />
    <FrontendLayout>
        <div v-if="$page.props.flash.message" class="alert bg-green-200 mt-4 mx-5 px-4 py-2">
            {{ $page.props.flash.message }}
        </div>
        <div class="mt-4 mx-4">
            <div class="flex justify-between">
                <h5>Products List</h5>
                <Link class="bg-blue-500 text-white p-3 rounded mb-4" :href="route('products.create')">Add product</Link>
            </div>
            <table class="w-full bg-white border border-gray-200 shadow">
                <thead>
                    <tr>
                        <th class="py-2 px-4 text-left border">Id</th>
                        <th class="py-2 px-4 text-left border">Name</th>
                        <th class="py-2 px-4 text-left border">Price</th>
                        <th class="py-2 px-4 text-left border">Action</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(item, index) in products" :key="index">
                        <td class="py-2 px-4 border">{{ item.id }}</td>
                        <td class="py-2 px-4 border">{{ item.name }}</td>
                        <td class="py-2 px-4 border">{{ item.price }}</td>
                        <td class="py-2 px-4 border">
                            <Link :href="route('products.show', item.id)" 
                                  class="px-2 py-1 text-sm bg-blue-300 text-dark me-2 rounded inline-block">
                                Show
                            </Link>

                            <Link :href="route('products.edit', item.id)"
                                  class="px-2 py-1 text-sm bg-green-300 text-dark me-2 rounded inline-block">
                                Edit
                            </Link>

                            <button @click="deleteProduct(item.id)"
                                    class="px-2 py-1 text-sm bg-red-600 text-white me-2 rounded inline-block">
                                Delete
                            </button>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </FrontendLayout>
</template>

<script setup>

import FrontendLayout from '@/Layouts/FrontendLayout.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

const props = defineProps({
    products: Array
});

const form = useForm({});

const deleteProduct = (productId) => {
    if (confirm('Are you sure you want to delete this product?')) {
        form.delete(route('products.destroy', productId), {
        });
    }
};
</script>
