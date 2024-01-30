<template>
    <div class="container">
        <FormCreate @set-card="addCard" />
        <CardFormModal :is-open="cardModalIsOpen" :card="cardForEdit" @update:is-open="toggleCardModal"
            @set-card="updateCard" @save-card="saveCard" />
        <WishList v-if="!cardsIsLoading" :cards="cards" @click-by-card="openCardForEdit" />
        <img v-else src="/loader.gif" alt="Идёт загрузка..." width="100">
    </div>
</template>
  
<script setup>
import { ref } from "vue";
import WishList from './components/WishList.vue';
import FormCreate from './components/FormCreate.vue';
import CardFormModal from './components/CardFormModal.vue'

const cards = ref([]);
const cardsIsLoading = ref(false);
const cardModalIsOpen = ref(false);
const cardForEdit = ref({});

const loadCards = () => {
    cardsIsLoading.value = true;
    setTimeout(() => {
        cards.value = [
            { id: 1, title: "Ноутбук", description: "Я хочу получить в подарок новый ноутбук", completed: false },
            { id: 2, title: "Наушники", description: "Я хочу получить в подарок наушники для ноутбука", completed: true },
            { id: 3, title: "Мышка", description: "Я хочу получить в подарок мышку для ноутбука", completed: false },
        ];
        cardsIsLoading.value = false;
    }, 2000);
};

loadCards();

const toggleCardModal = (value) => {
    cardModalIsOpen.value = value;
};

const addCard = (card) => {
    cards.value.push(card);
};

const updateCard = (card) => {
    cardForEdit.value = card;
};

const saveCard = () => {
    const newCard = Object.assign({}, cardForEdit.value);
    cards.value = cards.value.map(el => el.id === newCard.id ? newCard : el);
    toggleCardModal(false); // Закрываем модальное окно после сохранения
};

const openCardForEdit = (card) => {
    cardForEdit.value = { ...card };
    toggleCardModal(true); // Открываем модальное окно при редактировании
};
</script>
  
<style>
@import './assets/global.css';
</style>
  