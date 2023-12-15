<template>
    <form class="form" @submit.prevent="addCard">
        <h2>Форма создания</h2>
        <label>
            <span>Название:</span>
            <input type="text" v-model="newCard.title" />
        </label>
        <label>
            <span>Описание:</span>
            <input type="text" v-model="newCard.description" />
        </label>
        <button type="submit">Добавить</button>
    </form>
</template>

<script setup>
import { ref } from "vue";

const emit = defineEmits(['set-card'])
const newCard = ref({
    id: 0,
    title: "",
    description: "",
    completed: false,
});

const addCard = () => {
    emit('set-card', newCard.value)
}

</script>

<style scoped>
.form {
    display: flex;
    align-items: center;
    flex-direction: column;
}

input {
    margin-left: 4px;
    margin-bottom: 24px;
}
</style>
