<script setup>

import { ref, onMounted, computed, watch } from 'vue';
import { useRoute } from 'vue-router';

import UserLayout from '@/layouts/UserLayout.vue';

import { useProductStore } from '@/stores/user/product';
import Product from '@/components/Product.vue';


const productStore = useProductStore()

const route = useRoute()
const searchText =ref('')


// onMounted(() => {
//     if(route.query.q) {
//         searchText.value = route.query.q
//     }
// })

watch(() => route.query.q, (newSearchText) => {
    searchText.value = newSearchText
}, {immediate: true})


const filterProducts = computed(() => {
    return productStore.filterProducts(searchText.value)
})

</script>

<template>
    <UserLayout>
        <div class="">
            <span class="font-bold">Search results :</span>
            <span class="ms-2 italic">{{ searchText }}</span>
        </div>
        <Product :products="filterProducts"></Product>
    </UserLayout>
    
</template>