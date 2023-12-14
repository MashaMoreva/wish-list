<template>
    <h1>Wish list</h1>
    <AppCard v-for="(item, index) in cards" :card="item" :index="index" :key="item.id"
        @click="emit('click-by-card', item)" />
</template>

<script setup>
import AppCard from "./AppCard.vue";

const props = defineProps({
    cards: {
        type: Array,
    },
});

const emit = defineEmits(["click-by-card"]);
</script>

<style scoped></style>
