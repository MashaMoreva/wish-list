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

.modal-wrapper {
    display: flex;
    align-items: center;
    flex-direction: column;
    width: 380px;
}

button {
    width: 180px;
    background: #D9D9D9;
}

.actions {
    display: flex;
    margin-top: 30px;
}

.save-button {
    background-color: rgba(204, 102, 51, 1);
    margin-right: 8px;
}
</style>
