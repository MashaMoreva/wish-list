<template>
    <app-modal :model-value="isOpen" @update:model-value="emit('update:isOpen', $event)">
        <div class="modal-wrapper">
            <h2>Редактирование желания</h2>
            <form class="form" @submit.prevent="saveCard">
                <label>
                    <div>Название:</div>
                    <input type="text" :value="card.title" @input="setTitle">
                </label>
                <label>
                    <div>Описание:</div>
                    <input type="text" :value="card.description" @input="setDescription">
                </label>

                <div class="actions">
                    <button type="submit" class="save-button">Сохранить</button>
                    <button @click="cancelEdit">Отменить</button>
                </div>
            </form>
        </div>
    </app-modal>
</template>

<script setup>
import AppModal from "@/components/AppModal.vue";

const props = defineProps({
    isOpen: {
        type: Boolean,
    },
    card: {
        type: Object,
    },
})
const emit = defineEmits(['update:isOpen', 'set-card', 'save-card'])

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

const cancelEdit = () => {
    emit('update:isOpen', false);
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
    width: 80%;
}

.modal-wrapper {
    display: flex;
    align-items: center;
    flex-direction: column;
    width: 380px;
    height: 280px;
}

button {
    width: 180px;
    cursor: pointer;
}

.actions {
    display: flex;
    margin-top: 32px;
}

.save-button {
    background-color: #a2ffa2;
    margin-right: 8px;
}
</style>
