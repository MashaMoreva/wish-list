<template>
    <transition name="fade" appear>
        <div v-if="props.modelValue" :class="['modal', { 'active': props.modelValue }]"
            @click.self="$emit('update:modelValue', false)">
            <div class="modal_wrapper">
                <div class="modal_close" @click="$emit('update:modelValue', false)">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M21.7636 3.36584C22.0761 3.05342 22.0761 2.54689 21.7636 2.23447C21.4512 1.92205 20.9447 1.92205 20.6323 2.23447L12 10.8667L3.3678 2.23447C3.05538 1.92205 2.54885 1.92205 2.23643 2.23447C1.92401 2.54689 1.92401 3.05342 2.23643 3.36584L10.8687 11.9981L2.23496 20.6318C1.92254 20.9442 1.92254 21.4508 2.23496 21.7632C2.54737 22.0756 3.05391 22.0756 3.36633 21.7632L12 13.1295L20.6337 21.7632C20.9462 22.0756 21.4527 22.0756 21.7651 21.7632C22.0775 21.4508 22.0775 20.9442 21.7651 20.6318L13.1314 11.9981L21.7636 3.36584Z"
                            fill="currentColor" />
                    </svg>
                </div>
                <slot></slot>
            </div>
        </div>
    </transition>
</template>

<script setup>
const props = defineProps({
    modelValue: {
        type: Boolean,
    }
})
</script>

<style>
.modal {
    display: flex;
    position: fixed;
    width: 100%;
    height: 100%;
    top: 0;
    right: 0;
    z-index: 20;
    background: rgba(19, 18, 18, 0.3);
    align-items: center;
    justify-content: center;
    overflow-x: hidden;
    overflow-y: auto;

}

.modal_wrapper {
    position: relative;
    padding: 30px;
    margin: 0 auto;
    background: #fff;
    border-radius: 20px;
}

.modal_close {
    float: right;
    background: transparent;
    cursor: pointer;
}

.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.25s ease;
}

.fade-enter,
.fade-leave-to {
    opacity: 0;
}
</style>
