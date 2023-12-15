<template>
    <h2>Pедактирование желания</h2>
    <form class="form" @submit.prevent="saveCard">
        <label>
            <span>Название:</span>
            <input type="text" :value="card.title" @input="setTitle" />
        </label>
        <label>
            <span>Описание:</span>
            <input type="text" :value="card.description" @input="setDescription" />
        </label>
        <button type="submit">Сохранить</button>
    </form>
</template>

<script setup>
import { ref } from "vue";

const props = defineProps({
    card: {
        type: Object
    }
})
const emit = defineEmits(['set-card', 'save-card'])

const setTitle = (evt) => {
    const data = Object.assign({}, props.card)
    data.title = evt.target.value
    emit('set-card', data)
}

const setDescription = (evt) => {
    const data = Object.assign({}, props.card)
    data.description = evt.target.value
    emit('set-card', data)
}

const saveCard = () => {
    emit('save-card')
}
</script>

<style scoped>
.form {
    margin-bottom: 12px;
}

input {
    margin-left: 4px;
    margin-bottom: 8px;
}
</style>
