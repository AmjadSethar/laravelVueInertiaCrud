<template>
    <Head title="Create Product" />
    <FrontendLayout>
        
        <div class="mt-4 mx-4">
            <div class="flex justify-between">
                <h5>Create Product</h5>
                <Link class="bg-red-500 text-white py-2 px-5 inline-block rounded mb-4 btn-sm" :href="route('products.index')">Back</Link>
            </div>
            <form @submit.prevent="saveProduct()">
                <div class="grid grid-col-12 gap-4">
                    <div class="col-span-6">
                        <div class="mb-3">
                            <label>Product Name</label>
                            <input type="text" v-model="form.name" class="py-1 w-full" />
                            <span class="text-red-500" v-if="errors.name" >{{ errors.name }}</span>
                        </div>
                        <div class="mb-3">
                            <label>Product Price</label>
                            <input type="text" v-model="form.price" class="py-1 w-full" />
                            <span class="text-red-500" v-if="errors.price" >{{ errors.price }}</span>

                        </div>
                        <div class="mb-3">
                            <Link class="bg-red-500 text-white py-2 px-5 rounded mb-4 inline-block" :href="route('products.index')">Back</Link>
                            <button
                            :disabled="form.processing"
                            type="submit"
                            class="bg-blue-500 text-white py-2 px-5 rounded mb-4 me-4"
                            >
                            <span v-if="form.processing">Submitting...</span>
                            
                            <span v-else>Submit</span>
                            </button>
                        </div>
                    </div>

                </div>
            </form>
        </div>

    </FrontendLayout>
</template>

<script setup>
import FrontendLayout from '@/Layouts/FrontendLayout.vue';

import { Head,Link,useForm } from "@inertiajs/vue3";
defineProps({
    errors:Object
})
const form = useForm({
    name: '',
    price: '',
});

const saveProduct = () =>{
    const res = form.post(route('products.store'))
    if(res){
        form.reset
    }
}

</script>