<script setup>
import UserLayout from '@/layouts/UserLayout.vue';
import Close from '@/components/icons/Close.vue';

import { useCartStore } from '@/stores/user/cart';


const cartStore = useCartStore()

</script>

<template>
    <UserLayout>
        <h1>Shopping Cart</h1>
        <div class="flex">
            <div class="flex-auto w-64 bg-base-200 p-4 divide-y divide-slate-500">
                <div v-if="cartStore.items.length === 0" class="">
                    Cart is empty
                </div>
                <div v-else v-for="(item, index) in cartStore.items" class="flex gap-x-2 p-2">
                    <div class="flex-1">
                        <img class="w-full"
                            src="https://images.unsplash.com/photo-1596609548086-85bbf8ddb6b9?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
                            alt="">
                    </div>
                    <div class="flex-1">
                        <div class="flex flex-col justify-between h-full">
                            <div class="">
                                <div class="relative grid grid-cols-2">
                                    <div class="">
                                        <p class="font-bold">{{ item.name }}</p>
                                        <p>{{ item.about }}</p>
                                        <p>{{ item.price }}</p>
                                    </div>
                                    <div class="">
                                        <select v-model="item.quantity" class="w-1/2 p-1 rounded-md">
                                            <option v-for="quantity in [1, 2, 3, 4, 5]">{{ quantity }}</option>
                                        </select>
                                    </div>
                                    <div @click="cartStore.removeItemInCart(index)" class="w-3 absolute top-0 right-0">
                                        <Close></Close>
                                    </div>
                                </div>
                            </div>
                            <div class="">
                                <p class="font-bold">In stock</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>


            <div class="flex-auto w-32 bg-slate-200 p-4">
                <div class="">
                    <p>Order summary</p>
                    <div class="my-4 divide-y divide-slate-500">
                        <div class="flex justify-between">
                            <p>ราคาสินค้าทั้งหมด</p>
                            <p>100</p>
                        </div>
                        <div class="flex justify-between">
                            <p>ค่าส่ง</p>
                            <p>30</p>
                        </div>
                        <div class="flex justify-between">
                            <p>ราคาทั้งสิ้น</p>
                            <p>130</p>
                        </div>
                        <button class="w-full my-3 p-2 bg-[#000] text-white">ชำระเงิน</button>
                    </div>
                </div>
            </div>
        </div>
    </UserLayout>

</template>