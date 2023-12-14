<template>
    <div class="card">
        <div class="card-title">{{ card.title }}</div>
        <div class="card-description">{{ card.description }}</div>
        <div class="card-com">
            <div :class="{
                'card-is-completed': card.completed,
                'card-is-not-completed': !card.completed,
            }">
                {{ card.completed ? "Исполнено" : "Не исполнено" }}
            </div>
        </div>
    </div>
</template>

<script setup>

const props = defineProps({
    index: {
        type: Number
    },
    card: {
        type: Object
    },
})
</script>

<style scoped>
.card {
    width: 300px;
    padding: 24px 24px 16px;
    background-color: #fff;
    border-radius: 16px;
    margin-bottom: 16px;
}

.card-title {
    font-size: 18px;
    font-weight: 600;
    margin-bottom: 8px;
}

.card-description {
    color: rgb(106, 109, 114);
    margin-bottom: 16px;
}

.card-completed {
    display: flex;
    align-items: center;
    gap: 4px;
}

.card-is-completed {
    padding: 0 6px;
    border: 1px solid rgb(42, 182, 231);
    color: rgb(42, 182, 231);
    border-radius: 4px;
}
</style>