<script setup>
import UserLayout from '@/layouts/UserLayout.vue';

import { useProductStore } from '@/stores/user/product';

import Product from '@/components/Product.vue';


const productStore = useProductStore()
</script>

<template>
    <UserLayout>
        <div class="hero bg-base-200 h-96">
            <div class="hero-content text-center">
                <div class="max-w-md">
                    <h1 class="text-5xl font-bold">Hello to Meow</h1>
                    
                </div>
            </div>
        </div>
        <Product :products="productStore.list">
            
        </Product>
        
    </UserLayout>

</template>