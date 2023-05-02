<template >
    <header>
        <h1>Income Tracker</h1>
        <div class="total-income">${{totalIncome}}</div>
    </header>
</template>

<script setup>
const props = defineProps(["totalIncome"])
</script>

<style lang="scss" scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 15px 30px;
    background-color: #313131;
    border-bottom: 5px solid #ffce00;

    h1 {
        color: #eee;
        font-size: 28px;
    }

    .total-income {
        font-family: "Fira Code", "Fira Sans", sans-serif;
        background-color: #ffce00;
        color: #fff;
        padding: 5px 10px;
        font-weight: bold;
        font-size: 28px;
        min-width: 100px;
        text-align: center;
        border-radius: 8px;
        box-shadow: inset 0 0 6px rgba($color: #000000, $alpha: 0.25);
        text-shadow: 0 3px 3px rgba($color: #000000, $alpha: 0.25);
    }
}
</style>