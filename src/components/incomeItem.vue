<template>
    <div class="income-item">
        <div class="remove-item" @click="removeItem">X</div>
        <div class="desc">{{ income.desc }}</div>
        <div class="price">${{ income.value }}</div>
        <div class="date">{{ new Date(income.date).toLocaleDateString() }}</div>
    </div>
</template>
<script setup>
const props = defineProps(["income"])
const emit = defineEmits(["remove-item"])

function removeItem() {
    emit('remove-item', props.income)
}

</script>
<style lang="scss" scoped>
.income-item {
    position: relative;
    display: flex;
    padding: 15px 15px 15px 0;
    border-radius: 8px;
    background-color: #fff;
    margin: 0 auto 30px;

    .remove-item {
        color: #ef2d2d;
        font-weight: 600;
        font-size: 20px;
        text-align: center;
        margin: 0 15px;
        cursor: pointer;
    }

    div:not(.remove-item) {
        color: #666;
        font-size: 20px;
    }

    .desc {
        flex: 1 1 100%;
    }

    .price {
        min-width: 100px;
    }

    .date {
        text-align: right;
    }
}
</style>