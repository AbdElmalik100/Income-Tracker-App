<template>
    <div class="container income-list">
        <income-item v-for="data in state.sortedIncome" :income="data" @remove-item="removeItem"></income-item>
    </div>
</template>

<script setup>
import { remove } from '@vue/shared';
import incomeItem from './incomeItem.vue';
const props = defineProps(["state"])
const emit = defineEmits(["remove-item"])

function removeItem(id) {
    emit('remove-item', id)
}
</script>

<style lang="scss" scoped>
    .income-list {
        margin-top: 30px;
        padding: 15px;
    }
</style>