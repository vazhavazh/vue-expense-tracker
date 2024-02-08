<template>
    <div class="inc-exp-container">
        <div>
            <h4>Доходи</h4>
            <p id="money-plus" class="money plus">+{{ income }} ГРН</p>
        </div>
        <div>
             <h4>Витрати</h4>
            <p id="money-minus" class="money minus">{{ expenses }} ГРН</p>
        </div>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    income: {
        type: Number,
        required: true,
    },
    expenses: {
        type: Number,
        required: true,}
})
</script>