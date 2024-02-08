<template>
    <h3>Add new transaction</h3>
    <form id="form" @submit.prevent="onSubmit">
        <div class="form-control">
            <label for="text">Назва транзакції</label>
            <input 
            v-model="text"
            type="text" 
            id="text"  
            placeholder="Введіть назву...">
        </div>
        <div class="form-control">
            <label for="amount">
                Значення <br />
                (від'ємне - витрати, позитивне - дохід)
            </label>
            <input  
                    v-model="amount"
                    type="text" 
                    id="amount" 
                    placeholder="Введіть цифрове значення...">
        </div>
        <button  class="btn">Додати транзакцію</button>
    </form>
</template>

<script setup>
import { ref } from 'vue'
import {useToast} from 'vue-toastification'

const text = ref('');
const amount = ref('');

const emit = defineEmits(['transactionSubmitted'])

const toast = useToast();

const onSubmit = () => {
    if (!text.value || !amount.value) {
        toast.error('Усі рядки мають биту заповнені');
        return
    }

    const transactionData = {
        text: text.value,
        amount: parseFloat(amount.value),
    };

    emit('transactionSubmitted', transactionData)

    text.value = '';
    amount.value = '';
};
</script>