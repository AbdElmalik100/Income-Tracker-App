<template>
    <form @submit.prevent="formatHandler">
        <input type="text" placeholder="Description..." v-model="formData.desc">
        <input type="number" placeholder="Value..." v-model="formData.value">
        <input type="date" placeholder="Date..." v-model="formData.date">
        <input type="Submit" value="SUBMIT">
    </form>
</template>

<script setup>
import { ref, reactive } from 'vue'
const emit = defineEmits(["add-income"])

const formData = reactive({
    desc: null,
    value: null,
    date: null,
})

function formatHandler() {
    emit("add-income", {
        desc: formData.desc,
        value: formData.value,
        date: formData.date,
    })
    formData.desc = null
    formData.value = null
    formData.date = null
}

</script>

<style lang="scss" scoped>
form {
    display: flex;
    justify-content: center;
    margin-top: 30px;

    input {
        font-size: 20px;
        outline: none;
        border: none;
        padding: 15px 25px;
        color: #888;

        &::placeholder {
            color: #aaa;
        }

        &:not([type="submit"]) {
            display: block;
            background-color: #fff;
        }

        &[type="submit"] {
            color: #fff;
            background-color: #ffce00;
            font-weight: 500;
            text-shadow: 0 1px 3px rgba($color: #000000, $alpha: 0.2);
            cursor: pointer;
        }

        &:first-of-type {
            border-radius: 8px 0 0 8px;
        }

        &:last-of-type {
            border-radius: 0 8px 8px 0;
        }
    }
    @media (max-width: 767px) {
        flex-direction: column;
        padding: 15px;
        gap: 20px;
        input {
            border-radius: 8px !important;
            padding: 15px 20px;
        }
    }
}
</style>