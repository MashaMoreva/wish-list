<template>
    <h1>Wish list</h1>
    <div class="card-list">
        <AppCard v-for="(item, index) in cards" :card="item" :index="index" :key="item.id"
            @click="emit('click-by-card', item)" />
    </div>
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

<style scoped>
.card-list {
    display: flex;
    width: 1024px;
    flex-wrap: wrap;
    gap: 24px;
}
</style>
