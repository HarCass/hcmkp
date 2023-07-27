<script setup lang="ts">
import { ref, Ref } from 'vue';
type Item = {
    itemName: string,
    details: string,
    image: string,
    price: number,
    category: string,
    itemId: number
}

const items: Ref<Item[]> = ref([]);
try {
    const res: Item[] = await (await fetch('http://192.168.1.14:8080/api/items')).json();
    items.value = res;
}
catch (err) {
    console.log(err);
}
</script>

<template>
    <h1>HC MarketPlace</h1>
    <ul>
        <li v-for="item in items" :key="item.itemId">
            <h2>{{ item.itemName }}</h2>
            <img :src="item.image">
            <p>{{ item.details }}</p>
        </li>
    </ul>
</template>