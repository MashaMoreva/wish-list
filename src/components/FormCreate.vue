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
    border-radius: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    box-shadow: 0px 0px 20px 0px rgba(0, 0, 0, 0.10);
    padding: 30px;
    width: 400px;
    margin: 50px 0;
}

button {
    margin-top: 30px;
    background-color: rgba(204, 102, 51, 1);
}
</style>
