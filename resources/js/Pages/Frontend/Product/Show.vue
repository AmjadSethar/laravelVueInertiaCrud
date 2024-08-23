<template>
    <Head title="Show Product" />
    <FrontendLayout>
        
        <div class="mt-4 mx-4">
            <div class="flex justify-between">
                <h5>Show Product</h5>
                <Link class="bg-red-500 text-white py-2 px-5 inline-block rounded mb-4 btn-sm" :href="route('products.index')">Back</Link>
            </div>
                <div class="grid grid-col-12 gap-4">
                    <div class="col-span-6">
                        <div class="mb-3">
                            <label>Product Name</label>
                           <p>
                            {{ product.name }}
                           </p>
                        </div>
                        <div class="mb-3">
                            <label>Product Price</label>
                            <p>
                            {{ product.price }}
                           </p>

                        </div>
                    </div>
                </div>
        </div>

    </FrontendLayout>
</template>

<script setup>
import FrontendLayout from '@/Layouts/FrontendLayout.vue';

import { Head,Link,useForm } from "@inertiajs/vue3";
defineProps({
    errors:Object,
    product:Object
})

</script>