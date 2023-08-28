<script setup>

</script>

<template>
    <header>
        <h2 class="logo">devfinder</h2>
        <button class="toggler">
           <span class="text">light </span><span><img class="sun" src="../assets/002-sun.svg" alt=""></span>
        </button>
    </header>
</template>

<style scoped>
header{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
    .logo{
        color: #FFF;
        font-size: 26px;
        font-weight: 700;
    }
    .text{
        color: #FFF;
        font-size: 13px;
        font-weight: 700;
        letter-spacing: 2.5px;
    }
    button{
        background-color: transparent;
        border: none;
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 10px;
        padding: 0;
    }

</style>